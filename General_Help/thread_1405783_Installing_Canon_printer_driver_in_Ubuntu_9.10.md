---
title: "Installing Canon printer driver in Ubuntu 9.10?"
date: 2010-02-13
forum: General Help
---

### Post by caitken on 2010-02-13
I'm trying to install the driver for my Canon PIXMA MP240 printer.  I have followed the instructions here:
[http://www.benvaughan.com/general/get-a-canon-mp240-multifunction-printer-to-work-in-ubuntu/](http://www.benvaughan.com/general/get-a-canon-mp240-multifunction-printer-to-work-in-ubuntu/)
and have downloaded the tar and debian packages.  However the installer complains that libcupsys2 is not installed (broken dependency).
How do I go about fixing this problem under Ubuntu 9.10 - is its safe to go ahead and install libcupsys2?
Any help would be greatly appreciated.

---

### Post by drpjkurian on 2010-02-13
Hi
Navigate to synaptic package manager through System-->ADMINISTRATION-->SYNAPTIC PACKAGE MANAGER
search for libcupsys2 in the search bar.
Right click it and check for installation.

---

### Post by cpjkennedy on 2010-02-15
I've tried to install libcupsys2 with synaptic but I can't find it via search.  Any suggestions?

---

### Post by oldfred on 2010-02-15
This will not help but:

I have a MP160 and installed the .deb for it 3 years ago (with some difficultly). I upgraded and with each upgrade never had issues. With 9.04 I wanted to add a second MP160 with different configuration for printing envelopes as a default but I got the same error as you did. I never found the problem, but my totally new install of Karmic found the MP160 and installed it without any issue.

As I remember libcupsys2 does not exist or is an error in the install script for the printer. but I do not remember if there was a work around.

---

### Post by xmx on 2010-03-04
Having the same issue.  says broken dependency.  The canon mp240 printer I have worked fine with 9.04 version.  Anyone have any ideas to try?

Pic of error
Any suggestions will help,

---

### Post by xmx on 2010-03-04
> **xmx said:**
> Having the same issue.  says broken dependency.  The canon mp240 printer I have worked fine with 9.04 version.  Anyone have any ideas to try?

Pic of error
Any suggestions will help,

Oh snap I looks on other forum  to fix this error go here down load libcupsys2_1.3.9-17ubuntu_all.deb

[http://packages.ubuntu.com/jaunty/all/libcupsys2/download]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download")

---

### Post by ubunw on 2010-03-08
Hi,

I have the same problem, could get the printer and scanner working but it's detected as a "broken package" so it is un-installed automatically every time I update the system.

As you said, the problem is that the driver packages, downloadable from the Canon website, depend on the package "libcupsys2". The reason you can't find this package in 9.10 Karmic is because it has been replaced by package "libcups2".

All this I found out in this forum (see post #42):
[http://ubuntuforums.org/showthread.php?t=953292&highlight=MP240&page=5](http://ubuntuforums.org/showthread.php?t=953292&highlight=MP240&page=5)

So, the problem is that the drivers CAN be installed, but the packages declare a dependency on package "libcupsys2", which is not available any more in 9.10 Karmic. Thus, the packages appear as "BROKEN PACKAGES" in Synaptic, and are uninstalled automatically, and the printer/scanner ceases working.

Does anybody know how to solve this dependency? Or, at least, a workaround to move the packages from "broken" to "installed"?

Thanks in advance!

---

### Post by OpenKimono on 2010-12-30
I had the same problem when I installed 10.04.  Since libcupsys2 has been replaced by libcups2, the Canon driver downloads run into dependency problems.  I overcame this problem by forcing dpkg to ignore the dependency.

sudo dpkg -i --ignore-depends=libcupsys2 cnijfilter-common_3.00-1_i386.deb

Everything tests fine, so hopefully this work around is valid.

---

### Post by amac777 on 2010-12-30
You can download and install a dummy libcupsys2 package that will allow the MP240 to keep printing with the original canon drivers. This web site has instructions and they worked for me for both 64 and 32-bit Ubuntu 10.01.

[http://r3dux.org/2010/05/how-to-get-a-canon-mp240-printer-working-in-ubuntu-10-04-3264-bit/](http://r3dux.org/2010/05/how-to-get-a-canon-mp240-printer-working-in-ubuntu-10-04-3264-bit/)

---

