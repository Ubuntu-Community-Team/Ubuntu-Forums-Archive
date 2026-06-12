---
title: "Revelation password manager error"
date: 2006-05-17
forum: General Help
---

### Post by freakzilla on 2006-05-17
I tried opening my stored passwords in Revelation and got this error message.  Does this mean anything to anyone?  Is there any other way to access my passwords through another password program?  :-k 

Traceback (most recent call last):
  File "/usr/bin/revelation", line 1360, in ?
    app.run()
  File "/usr/bin/revelation", line 1339, in run
    self.file_open(io.file_normpath(file))
  File "/usr/bin/revelation", line 1256, in file_open
    entrystore = self.__file_load(file, password)
  File "/usr/bin/revelation", line 786, in __file_load
    return datafile.load(file, password, lambda: dialog.PasswordOpen(self, os.path.basename(file)).run())
  File "/usr/lib/python2.4/site-packages/revelation/io.py", line 113, in load
    entrystore = self.__handler.import_data(data, password)
  File "/usr/lib/python2.4/site-packages/revelation/datahandler/rvl.py", line 379, in import_data
    input = zlib.decompress(input[0:-padlen])
error: Error -3 while decompressing data: incorrect header check

---

