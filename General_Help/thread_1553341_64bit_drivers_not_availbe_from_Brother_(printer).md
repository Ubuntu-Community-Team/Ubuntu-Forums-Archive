---
title: "64bit drivers not availbe from Brother (printer)?"
date: 2010-08-14
forum: General Help
---

### Post by lue42x on 2010-08-14
This site has drivers for my new Brother HL-3040CN laser printer ... but it says its the wrong architecture when I try to open the first one with GDebi Package Installer.

I'm kind of stuck now ...should I try just plugging the printer into the computer with the network cable and seeing if Ubuntu will automatically take care of drivers?

For reference I saw this topic when I googled the issue

[http://forums.linux-foundation.org/read.php?24,11074,11930](http://forums.linux-foundation.org/read.php?24,11074,11930)


Edit:  This site says 64 bit drivers are available for Ubuntu 9.10, only 32 bit drivers are available for Ubuntu 10.04.  I am running 10.04 (64bit) ... should I return the printer?

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/evaluation.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/evaluation.html)

---

### Post by Ginsu543 on 2010-08-15
> **lue42x said:**
> 
Should I try just plugging the printer into the computer with the network cable and seeing if Ubuntu will automatically take care of drivers?

Yes.

I have a Brother HL-2170W, an HL-5040, and an HL-1240, all connected to 64-bit Ubuntu PCs, and all of them have worked out of the box by simply connecting them with USB cables. The Ubuntu OS recognized each of them and installed the appropriate drivers on its own.

---

### Post by plucky on 2010-08-15
> Edit: This site says 64 bit drivers are available for Ubuntu 9.10, only 32 bit drivers are available for Ubuntu 10.04. I am running 10.04 (64bit) ... should I return the printer?


From the Brother website for Ubuntu 64 bit > # Pre-required Procedure (5)
    Related distributions
    Debian 64 bit version, Ubuntu 64 bit version
    Related products/drivers
    printer/PC-FAX drivers
    Requirement
    **ia32-libs or lib32stdc++ is required to be installed.**



This will allow the 32-bit drivers to work on a 64-bit system.

Good luck

---

### Post by Ginsu543 on 2010-08-15
ia32-libs will allow your 64-bit system to install and run 32-bit software.

---

### Post by morrie on 2010-09-05
I confirmed that both of the above-listed packages were already installed with the latest version (Ubuntu 10.04-64, brother 3040cn), along with steps here from Brother [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html), and still no joy.  I got the error "unsupported architecture 'i386'" trying to run the package, so I resorted to the instruction on the Brother website (above).  Still no printer (everything checked in the Brother steps, too).  I think am I supposed to be able to go to "add printer" now that the driver is installed and it will be there? (It seemed that I was manually installing it (following the link above).

---

### Post by Gideon123 on 2010-10-22
Is there a solution for this problem? Done everything I could find about installing the drivers.

---

### Post by klausner on 2010-10-22
> **Gideon123 said:**
> Is there a solution for this problem? Done everything I could find about installing the drivers.

Yes. See [this thread]("http://ubuntuforums.org/showthread.php?t=1602075&highlight=3040CN").

---

