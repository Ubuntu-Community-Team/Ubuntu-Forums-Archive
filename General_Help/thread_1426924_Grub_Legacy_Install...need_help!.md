---
title: "Grub Legacy Install...need help!"
date: 2010-03-10
forum: General Help
---

### Post by WaveRunner on 2010-03-10
I was afraid to type the title after reviewing many of the posts including those in the archives. And I have also Googled questions related to Grub Legacy but have run into some confusion--specifically I am not sure what I am suppose to use to write the lines of code (ie: XP Console; ms-dos; or..?) Now some background and objectives.
 
I have an old Pent III and two HD's but no CD R/W rom just a CDrom in addition to the standard 3.5"floppy. I have two USB connections on back which are low speed. And the BIOS only indicates "boot to floppy and removable media" and does not specify USB in the list...and I suspect the BIOS cannot be upgraded? So I suspect that creating a bootable USB Flash is a "non-option". 
 

Now for my objectives. I am new to both Ubuntu and Linux and I want to get some exposure and experience using these systems. _I want to create a dual-boot on one HD for now:_ One OS would be Win XP HE and the other Ubuntu 9.04. As of this writing I understand that Ubuntu 9.10 is having problems dual booting with Win XP using Grub2. So I decide to drop back to an earlier version of both Ubuntu and a bootloader until I am better able to work on a more recent version of Ubuntu. I have done a clean install of Win XP and partitioned the hardrive into 3 partitons and one extended partion. I have some unallocated space at end of HD. The 1st partition has Win XP (boot and system); the 2nd partition is Win XP recovery; the 3rd partition is small and for paging and swap files; the fourth partition is an extended one with 3 logical drives. The 4th extended partiton is where I want to put Grub and Ubuntu.[LIST=1]
[*]I want to start the computer and go directly to Grub then load the OS of my choice (Win XP or Ubuntu 9.04)
[*]I would also like to create a Grub bootable floppy. I have directions on "how to" but am confused on what text editior to use to write the code with to the floppy...on the XP Console or what.
[*]I have access to DSL to download the ISO image either as "alternate" or "LiveCD"...BUT I can't burn a CD.  I can only save to USB Flash.  _Can I still unzip these files and install on HD and use them?_
[/LIST]I realize that many of you are way way aheadof me on Ubuntu and Grub but I would appreciate anyone's time in getting me started. I should also note that I am having trouble with my .pdf file reader so any reference to a web site that has .pdf files is "iffy" for me. Many thanks and thanks to the Admistrators for keeping this site going.
-WaveRunner

---

### Post by zvacet on 2010-03-11
[Here]("https://help.ubuntu.com/community/Installation/FromWindows") you can find how to install from Windows.If you want to be able to choose OS from grub install grub on MBR not on Ubuntu partition.**Don't unzip iso!!!** You have to burn iy (or save to usb) as image not data.If you want legacy grub install with grub2 and after that read [this.]("https://help.ubuntu.com/community/Grub2#Reverting to GRUB Legacy") When you are finish and your Ubuntu is running make grub floppy following [this]("http://members.iinet.net.au/~herman546/p15.html#grub_floppy_howto_make") guide.

---

### Post by WaveRunner on 2010-03-12
Thank you for your time...I will try!  Am I suppsoe to close this thread at this time or wait until the problem is solved then close?  With gratitudfe and much humility.  -WR

---

### Post by zvacet on 2010-03-12
Close the thread when you solve problem.If you have questions about this just ask.

---

