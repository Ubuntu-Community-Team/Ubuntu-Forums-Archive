---
title: "Dual Boot With Windows 7"
date: 2010-03-22
forum: General Help
---

### Post by Jnelso56 on 2010-03-22
I tried to install a windows 7/Ubuntu dual boot and I've tried it a couple times but every time I boot into Windows it breaks Grub and won't boot. It says loading Grub and just freezes on the screen. Is there anyway to keep Windows from doing this?

---

### Post by Mark Phelps on 2010-03-22
> **Jnelso56 said:**
> I tried to install a windows 7/Ubuntu dual boot and I've tried it a couple times but every time I boot into Windows it breaks Grub and won't boot. It says loading Grub and just freezes on the screen. Is there anyway to keep Windows from doing this?

If you have only one hard drive -- no.  Every MS Windows install will automatically overwrite the MBR.  That's how it works.

You will need to boot from an Ubuntu LiveCD and reinstall GRUB (or GRUB2 if you installed 9.10 clean) to rewrite GRUB into the MBR.

---

### Post by oldfred on 2010-03-22
Is your problem after an install which is normal and required a reinstall of grub as Mark Phelps commented or after rebooting and using windows.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

### Post by Jnelso56 on 2010-03-22
It happens whenever I reboot from windows. It's a gateway so I might try closing some of the gateway programs on there and see if that solves it.

---

### Post by Peter Alien on 2010-03-22
I had WinXP Pro and Ubuntu Linux installed in just one HD.
For that you have to install always first the Microsoft OS and after that Linux... and that's it... GRUB is fine and it was a piece of cake :)

For Win7 i think it's the same thing!
INSTALL ALWAYS FIRST THE MICROSOT OPERATING SYSTEM AND AFTER THAT LINUX.

---

### Post by wilee-nilee on 2010-03-22
> **Jnelso56 said:**
> It happens whenever I reboot from windows. It's a gateway so I might try closing some of the gateway programs on there and see if that solves it.

Your description is confusing if you want help, tell us what is installed and in what order they were installed and what actually boots!

---

### Post by Jnelso56 on 2010-03-22
I originally had Ubuntu 9.10 installed on it. I formatted the hard drive and used the Windows 7 recovery discs to copy windows back onto the hard drive. I then went back through and installed Ubuntu. Everything works fine I can boot into Ubuntu or Windows 7. However, the next time the computer tries to boot after a Windows 7 session the screen says Grub is loading but it never does so Windows/something Gateway installs by default is over-writing the MBR every time so Grub won't load.

---

### Post by Mark Phelps on 2010-03-22
> **Jnelso56 said:**
> I originally had Ubuntu 9.10 installed on it. I formatted the hard drive and used the Windows 7 recovery discs to copy windows back onto the hard drive. I then went back through and installed Ubuntu. Everything works fine I can boot into Ubuntu or Windows 7. However, the next time the computer tries to boot after a Windows 7 session the screen says Grub is loading but it never does so Windows/something Gateway installs by default is over-writing the MBR every time so Grub won't load.

Some of the OEMs have their own utilities that write code into the MBR, and force it to be rewritten upon detecting changes to the MBR. 

Additionally, there are some AV utilities that do the same thing.

You would have to go through a long and painful process in Win7 of finding out which app/program is rewriting the MBR -- and then see if it can be disabled.

Sorry, don't know a way in Ubuntu to prevent that from happening every time.  

However, there is an alternative -- EasyBCD.  This free utility can be downloaded from the NeoSmart Technology forums and can be used to add Ubuntu to the Win7 boot loader.  That way, you will still be able to boot into either OS, and you won't have to deal with this problem on every boot.

---

### Post by Jnelso56 on 2010-03-23
I un-installed norton and a gateway recovery management application and that seems to have fixed it.

---

