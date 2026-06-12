---
title: "unzip - read failure while seeking for End-of-centdir-64 signature"
date: 2010-04-11
forum: General Help
---

### Post by Alfred_zxc on 2010-04-11
I encountered a problem when i tried to unzip a large .zip file ( about 7.8G). Below is the error message i got from shell. Could any guy help to look into this problem? How can i fix it (if other tools can work, please suggest:KS)

```
unzip VMImageV6.zip
Archive:  VMImageV6.zip
fatal error: read failure while seeking for End-of-centdir-64 signature.
  This zipfile is corrupt.
unzip:  cannot find zipfile directory in one of VMImageV6.zip or
        VMImageV6.zip.zip, and cannot find VMImageV6.zip.ZIP, period.
```Btw, I'm in lucid lynx, thanks in advance!

---

### Post by gmargo on 2010-04-11
Stating the obvious, it sounds like the .zip file is corrupt.  Easy test: use the unzip tool to test the archive with "unzip -t file.zip".  You can also test independent of unzip: install the p7zip-full package and use the 7z tool to test the archive: "7z t file.zip".

---

### Post by Alfred_zxc on 2010-04-11
Thank you, gmargo! i installed 7z and tested the archive, it told me that the archive can not be opened.

```
7z t VMImageV6.zip

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=zh_CN.utf8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: VMImageV6.zip

Error: Can not open file as archive
```To be sure, i re-downloaded the file from FTP, and now it works well. Thanks for the help:)

---

