---
title: "Unable to run WIN32 programs through WINE"
date: 2010-05-20
forum: General Help
---

### Post by ganeshmallyap on 2010-05-20
Hi all,

I am facing some unusual issue while trying to run any WIN32 applications through WINE in my Ubuntu Lucid AMD64 desktop.  As you may see from the attached image, my system reports that executable bit is blocked.  I am unable to run any Win32 applications after this.  Though I dont use any Windows applications from the day I switched to Ubuntu.  But I am keeping this ready just in case if I have to run any ever.  Please help.

Thanks.

---

### Post by dcstar on 2010-05-20
> **ganeshmallyap said:**
> Hi all,

I am facing some unusual issue while trying to run any WIN32 applications through WINE in my Ubuntu Lucid AMD64 desktop.  As you may see from the attached image, my system reports that executable bit is blocked.


It does **not** say that anything is blocked, it specifically says that something is not set.

If you want it to run, set the execute bit.

---

### Post by NightwishFan on 2010-05-20
Right click the file, go to permissions and check as executable. It is a security feature.

---

### Post by colin.p on 2010-05-20
Also, if you try and install off a CD, you have to copy it to the hard drive first, as the exe is "read only". Then you can make it an executable file.

Colin

---

### Post by ganeshmallyap on 2010-05-22
Thank you all for your time and the replies.  Actually the WIN32 application I was trying to run is located in my hard drive (separate partition).  I have marked it as executable. Over and above this I accessed this file through WindowsXP via VirtualBox and set the executable bit.  Even after this I am getting the same error. These applications are working fine when I run from WinXP via Virtualbox.  So I am made to believe that this issue is somehow related to configuration.  Not sure though :(

---

