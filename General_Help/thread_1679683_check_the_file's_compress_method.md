---
title: "check the file's compress method"
date: 2011-02-01
forum: General Help
---

### Post by rkoziol7 on 2011-02-01
Hi,

I have a compressed text file. The method of compress is unknown.

I can see the file contents by using Midnight Commander without a problem but I would like to view the file just with cat. So I am trying to uncompress the file with unzip or gunzip but it does not work.

How to check the method the file is compressed with? Is any way to find it with Midnight Commander?

Regards

---

### Post by Foxheadz on 2011-02-01
Normally you can just tell by the file extension, but if that doesn't work try right clicking on it and selecting properties there should be something like "type" or file extension.

And do you not see an option "extract here" when you right click on it?

---

### Post by rkoziol7 on 2011-02-01
I have an option 'Extract here' but it gives me an error:

> Archive:  /home/myaccount/file.zip
[/home/myaccount/file.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/myaccount/file.zip or
          /home/myaccount/file.zip.zip, and cannot find /home/myaccount/file.zip.ZIP, period.However the file is correct because I can view it with Midnight Commander. It is probably not a zip archive.

---

### Post by tredegar on 2011-02-01
Try  the **file** command:
```
file /path/to/compressed_file
```

---

### Post by rkoziol7 on 2011-02-01
That did the trick :)

> file.zip: gzip compressed data, from Unix

And gunzip did all the rest.

Thanks!

---

