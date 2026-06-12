---
title: "opening .exe files with Wine in Ubuntu"
date: 2011-08-14
forum: General Help
---

### Post by pb910 on 2011-08-14
so I downloaded it, and followed all the steps to get it working, I navigate my way to the folder with the .exe files in it that I want to open, and then them i typed in "wine [file name].exe"

then the output is:


wine: cannot find L"C:\\windows\\system32\\printf. exe"


can someone help me fix this problem ?

---

### Post by raja.genupula on 2011-08-14
copy what you got and paste here ,typed correct file name look for letter case also .

---

### Post by vavantoo on 2011-08-14
Hi,

You need to type it like this.

**wine/path/to/your/installer.exe**

Also make sure that you run 'winecfg' to set up your drives so that wine can see your CDRom.

If you need more help, just check this website.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Hope this could resolve the problem :)

---

### Post by Mark Phelps on 2011-08-14
Are you trying to set up a printer, or install printer drivers using Wine?  

Because if that is what you're trying to do -- you can't do that.

WINE is NOT a Windows Emulator, that is, it does not give you a full-blown Windows environment inside Ubuntu; instead, it provides the ability to run SOME Windows apps.

Among the things you can NOT do with Wine is install devices and and drivers.

---

### Post by vavantoo on 2011-08-15
If you are trying to install printer drivers. Below gives you some more information. Hope it helps.
_ANS:_
No. With the possible future exception of some printer drivers, Wine requires your hardware to already be working on your operating system. The technical reason for this is that Wine, like most applications, runs in user mode and not kernel mode.

---

