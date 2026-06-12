---
title: "scan from command line"
date: 2010-02-17
forum: General Help
---

### Post by bill-lancaster on 2010-02-17
I have a Deskjet F2400 series and want to scan a document to a file from the command line without having the HP Device Manager being invoked.

Any ideas?

---

### Post by rnerwein on 2010-02-17
hi
have a look at the man page: man sane
try at the command line: scanimage -L to detect your scanner.
i have a: device `hpaio:/net/Photosmart_C309a_series?ip=192.168.2.117' is a Hewlett-Packard Photosmart_C309a_series all-in-one

and the commands works for me out of the box. my printer is connected via WLAN and i'm running ubuntu karmic koala 9.10.
good luck
ciao

---

