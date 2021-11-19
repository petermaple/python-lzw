下载 http://192.168.1.1/downloadFile?file=/var/config/psi
去除60位：
dd if=psi of=psilzw bs=1 count=1000000 skip=60

INSTALLING

you should be able to install this package with

   python setup.py install

----

Ok, moving on.

The easiest way to use lzw is probably something like this

>> import lzw

>> filepath = "your_psi_file_deleted_previous_60"
>> infile = lzw.readbytes(filepath, 1024)
>> uncompressed = lzw.decompress(infile)
>> with open('your_save_file', 'wb') as f:
    for bt in uncompressed:
        f.write(bt)
注意tab
See the module documentation for more details.

---

The underlying compression algorithm for this module is as expressed
in section 13 of the TIFF 6.0 specification, pages 58 to 62, available
at the time of this writing on-line at

    http://partners.adobe.com/public/developer/en/tiff/TIFF6.pdf

Wherever possible, I've tried to adhere to the algorithm and
conventions that are described (in exhaustive and yet very readable
detail!) in that document, even when it gets a bit Tiff
specific. Where there are differences, they are likely bugs in this
code.

---

Current dev priorities:

- Hunt down some potential user applications, see why they're
  potential rather than actual, and then get on that bus.


For now

- Keep things as simple and intelligible as possible
- Adhere as closely to the TIFF spec as is reasonable
- Keep memory use low for good use of the iterators
- Stay in pure python
- Faster would be nicer, though...


