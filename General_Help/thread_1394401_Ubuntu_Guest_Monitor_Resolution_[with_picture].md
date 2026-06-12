---
title: "Ubuntu Guest Monitor Resolution [with picture]"
date: 2010-01-30
forum: General Help
---

### Post by alexp91k on 2010-01-30
[IMG]http://i45.tinypic.com/2dba1jt.png[/IMG]

I simply ran the Guest Additions CD (on VirtualBox), double clicked the x86 (I'm running 32-bit) executable, and got that error.

Any help would be greatly appreciated.

---

### Post by Psycho.mario on 2010-01-30
There should be another file, without .exe in the filename. The file you tried to run is a Windows Executable

---

### Post by alexp91k on 2010-01-30
> **Psycho.mario said:**
> There should be another file, without .exe in the filename. The file you tried to run is a Windows Executable

The files in that folder end with the extensions:

.exe
.pkg
.INF
.run
.sh

Do you know which one I should double click? Or perhaps my Guest Additions isn't the right CD?

---

### Post by alexp91k on 2010-01-30
> **alexp91k said:**
> The files in that folder end with the extensions:

.exe
.pkg
.INF
.run
.sh

Do you know which one I should double click? Or perhaps my Guest Additions isn't the right CD?

Actually, I think I'm supposed to do the .run because it's on the Guest machine, which is Ubuntu (and I'm assuming .run is the Ubuntu executable).

I did that but it says I don't have enough permissions to run it so it aborted.

Can I run this using superior permissions (sudo, I assume?)

---

### Post by howefield on 2010-01-30
Download the PDF manual from virtualbox.org 

Page 65.

Or follow the tutorial here...

[http://www.mydigitallife.info/2009/11/25/how-to-install-virtualbox-guest-additions-in-linux-ubuntu-debian-fedora-opensuse-red-hat-and-more/](http://www.mydigitallife.info/2009/11/25/how-to-install-virtualbox-guest-additions-in-linux-ubuntu-debian-fedora-opensuse-red-hat-and-more/)

---

### Post by alexp91k on 2010-01-30
> **howefield said:**
> Download the PDF manual from virtualbox.org 

Page 65.

Or follow the tutorial here...

[http://www.mydigitallife.info/2009/11/25/how-to-install-virtualbox-guest-additions-in-linux-ubuntu-debian-fedora-opensuse-red-hat-and-more/](http://www.mydigitallife.info/2009/11/25/how-to-install-virtualbox-guest-additions-in-linux-ubuntu-debian-fedora-opensuse-red-hat-and-more/)

Thanks, it installed successfully.

However, when I restarted, and then resized the window, it did not change its resolution at all. I also don't notice any mouse-pointer integration or copy/paste benefits.

Did I do something wrong? Would appreciate any help to finish this process off.

---

### Post by howefield on 2010-01-30
> **alexp91k said:**
> Did I do something wrong?

If you are using a fairly current version of Virtualbox, it sounds like it hasn't installed successfully. Try again.

Post any error messages, ect.

---

