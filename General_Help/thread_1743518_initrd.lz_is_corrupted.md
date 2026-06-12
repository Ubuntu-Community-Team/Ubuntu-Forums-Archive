---
title: "initrd.lz is corrupted"
date: 2011-04-29
forum: General Help
---

### Post by cmax24 on 2011-04-29
i'm trying to install ubuntu in my windows7 with wubi... i put in a folder wubi and ubuntu-11.04-desktop-amd64.iso... but when i try to install there is an error.. this is the lasts line of log

04-29 21:52 DEBUG  TaskList: ## Running extract_kernel...
04-29 21:52 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
04-29 21:52 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
04-29 21:52 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
04-29 21:52 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
04-29 21:52 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
04-29 21:52 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
04-29 21:52 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = 45a7bee6779b8cd75634a70fd7a566dd == 45a7bee6779b8cd75634a70fd7a566dd
04-29 21:52 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
04-29 21:52 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = d62bc5c85ac4d8e2d1172fbe9ab8a514 != 4aa66b9da42e1a3f667ab0c8009cc801
04-29 21:52 ERROR  TaskList: File D:\ubuntu\install\boot\initrd.lz is corrupted
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 526, in extract_kernel
Exception: File D:\ubuntu\install\boot\initrd.lz is corrupted
04-29 21:52 DEBUG  TaskList: # Cancelling tasklist
04-29 21:52 DEBUG  TaskList: # Finished tasklist
04-29 21:52 ERROR  root: File D:\ubuntu\install\boot\initrd.lz is corrupted
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 526, in extract_kernel
Exception: File D:\ubuntu\install\boot\initrd.lz is corrupted

---

### Post by cmax24 on 2011-04-30
ei.......

---

### Post by bcbc on 2011-04-30
Check the md5sum of the desktop CD image you downloaded. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by cmax24 on 2011-04-30
the .iso md5 is 7de611b50c283c1755b4007a4feb0379

---

### Post by Rubi1200 on 2011-04-30
Hash appears to be good. Are you trying to install Wubi to a non-default location (C drive is default)?

---

### Post by cmax24 on 2011-04-30
yes C is the driver where i have installed windows... D is a second partition

---

### Post by cmax24 on 2011-04-30
the same error appars in C

---

### Post by cmax24 on 2011-04-30
hoe can i resolve it??

---

### Post by bcbc on 2011-04-30
I'd create a bug report and attach your entire log file to it: [https://bugs.launchpad.net/wubi/+filebug](https://bugs.launchpad.net/wubi/+filebug)

You'll need to register at launchpad.net first.

---

### Post by cmax24 on 2011-04-30
yes I do it... but at moment there are nothing to resolve this problem?? I would try ubuntu...

---

### Post by bcbc on 2011-04-30
I haven't used the 64bit version. But I'd expect there would be more problems reported already if the image was bad. So I'm not sure what is causing this. You could try the 32 bit version...

Probably a good idea to run chkdsk on windows to make sure your ntfs file system is clean as well (but I doubt this is it - just to rule it out).

---

### Post by cmax24 on 2011-05-01
ok now i try

---

### Post by cmax24 on 2011-05-02
yes i386 version go good.... but after i choose ubuntu on boot compare a screen about :ntfs5: no wubildr

---

### Post by Rubi1200 on 2011-05-02
> **cmax24 said:**
> yes i386 version go good.... but after i choose ubuntu on boot compare a screen about :ntfs5: no wubildr
Does Ubuntu still boot after you see that message?

It is probably GRUB4DOS, which Wubi uses to boot from, searching each partition for the wubildr file until it finds it.

A bit annoying perhaps, but as long as Ubuntu boots nothing to worry about.

---

### Post by cmax24 on 2011-05-02
i have created a new partition so i have resolve all

---

### Post by Rubi1200 on 2011-05-02
> **cmax24 said:**
> i have created a new partition so i have resolve all
Problem fixed? Excellent :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

