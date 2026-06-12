---
title: "windows crashed need help to access through ubuntu"
date: 2010-01-25
forum: General Help
---

### Post by ydeardorff on 2010-01-25
Hello all,

I have ubuntu 9.01 64bit version. I used the wubi installer to install it within windows. I did this due to an update problem with vista 64bit that leads to losing your dvd rom. 
Normally I would setup ubuntu on a separate partition to avoid the following problem, but I could use your help on this.

My ubuntu works fine. windows recycles on reboot and will not load no matter what. even then the system has removed the functionality of my dvd rom in both linux and windows.

I need to find a way to edit the settings of msconfig, regedit and other problems within windows to get it back up to boot properly.

Are there any programs that will allow me to run these files? Wine wil not run them. And without a dvd-rom I cannot do the system start up repair for windows. Im thinking of making my external hard drive a boot-able drive, and use my wifes computer to copy al the files to the drive off the install DVD. Then doing the same for ubuntu on my flash drive. Then for the 3rd time in as many days format the new 500gb hard drive nd start over AGAIN! LOL

Id appreciate anything anyone can do! Id prefer not to loose everything I have installed and settings I have painstakingly got right withing linux.

Thanks

---

### Post by StuartN on 2010-01-25
> **ydeardorff said:**
> Id prefer not to loose everything

If you have ntfs tools installed, then you should have no problem reading the data off the old Windows partition. Running Ubuntu from a Live CD and copying the data onto a backup will ensure that nothing on the original partition is altered, if you need to keep the old Windows stuff.

---

### Post by pricetech on 2010-01-25
Live CD is not an option.  OP says it's not working.

That makes it sound like hardware issues, which may have in turn led to OS issues.

Best option for you is to remove the hard drive and put it in your wife's computer and copy your winders data that way, then run diagnostics on your computer to find out what else or what all is not functioning as it should.

Your hardware vendor should offer diagnostic software for the computer.  It may even be a boot option to run onboard diags.

---

