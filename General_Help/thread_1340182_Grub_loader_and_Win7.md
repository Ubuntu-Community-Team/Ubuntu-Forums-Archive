---
title: "Grub loader and Win7"
date: 2009-11-28
forum: General Help
---

### Post by warren181 on 2009-11-28
I had ubuntu dual booted with xp a while ago but then had to get rid of it to sell a hard drive. i am now about to install windows 7 on a new machine and i would like to be able to dual boot ubuntu on a second hard drive, in the same way that i discribe in this thread

[http://ubuntuforums.org/showthread.php?t=1032316](http://ubuntuforums.org/showthread.php?t=1032316)

My question is are all the line of code the same to get the computer to boot straight into windows unless i select the secound hard drive, or do i need something different,

Thanks for any help

Warren.

---

### Post by cariboo on 2009-11-28
Install Windows 7, then Ubuntu. Ubuntu will install grub, a boot loader, in the mbr. It creates a menu where you can select which operating system you want to use. By default it installs to the mbr of the first hard drive, so you really don't have to do any thing special.

---

### Post by john newbuntu on 2009-11-29
As suggested by Cariboo907, install win7 first and then Ubuntu.

Now, depending on the flavor or ubuntu, it may use grub or grub2.  Also, it may or may not install grub into the MBR of your first drive.  This is where you have to make sure that grub gets into the first drive so that you will be presented with the option to choose 
the OS.

If grub or grub2 is written to your second drive, then:
a.  you may have to relocate it to the MBR on the first drive (/dev/sda) for dual booting to work normally.
b.  Alternatively, you could also try chainloading windows into booting linux by handing off the MBR from your second drive (in the form of a file) to c:\ and adding an entry in win.ini.  I an not sure if this would work but worth a try.

---

### Post by warren181 on 2009-11-29
i understand about installing win7 first but the problem i want to overcome is if for any reason i need to take the secound hard drive out i wout be able to load into windows becausse the windows loader is not present. what i would like to be able to do is for the computer to load straight into windows unless i specify to boot from the secound hard disk which will have ubuntu installed and i intend to use 9.10

Warren

---

### Post by sensay on 2009-11-29
My system currently dual boots in a way i think your trying to achieve, basically my machine will natively boot into ubuntu (with no option for windows) but if i hit f8 at boot i can select to boot from my windows hard drive, complete with windows boot loader. Is this what your aiming for?

[http://ubuntuforums.org/showthread.php?t=1318424](http://ubuntuforums.org/showthread.php?t=1318424) here is the thread i made when trying to achieve that scenario :)

The gist of what i had to do was install ubuntu first to its own hd, then windows to its own HD (this took out grub) then reinstalled grub to the the ubuntu drive via the live CD.

HTH

EDIT: Just saw your doing this with 9.10 (grub2) i did mine with 9.04 (grub1) then upgraded to 9.10 so i dont know if it will be the same procedure

---

### Post by Mark Phelps on 2009-11-29
What I did for the same issue is to have both drives bootable is to NOT mess with the MBR on the MS Windows drive, but instead, install GRUB to the MBR of the Ubuntu drive and boot from that.

This way, both drivers are bootable on their own.

When the Ubuntu drive is the boot drive, it puts up the GRUB menu, from which I can select any OS.

When the Ubuntu drive is absent, boot defaults to the MS Windows drive, which being bootable on its own, is able to boot into the Windows boot loader menu.

---

### Post by sensay on 2009-11-29
> **Mark Phelps said:**
> What I did for the same issue is to have both drives bootable is to NOT mess with the MBR on the MS Windows drive, but instead, install GRUB to the MBR of the Ubuntu drive and boot from that.

This way, both drivers are bootable on their own.

When the Ubuntu drive is the boot drive, it puts up the GRUB menu, from which I can select any OS.

When the Ubuntu drive is absent, boot defaults to the MS Windows drive, which being bootable on its own, is able to boot into the Windows boot loader menu.

Yes, actually thinking about it choosing to put the grub in the mbr of the grub drive when you install is a much more sensible way than i did it :P

---

### Post by warren181 on 2009-11-30
i am try to do what sensay did but i want the computer to boot into windows by default. i did manage to do this the last time i dual booted ubuntu and when i had to detach the hard drive windows still worked. in the thead that i posted a link to above ui was given code to put in the terminal to get this to work with that code still work or will i have to change it for the computer.#

Warren

---

### Post by warren181 on 2009-11-30
sorry only read the Marks post i dident quite understand it till now,
How will i install grub just on the ubuntu drive, and not on the windows drive, so that i then have to chose the drive i want to boot into

Warren

---

### Post by warren181 on 2009-12-01
Please could someone answer my question as i have no idea how to go about only installing grub on  only the ubuntu hard drive

Warren

---

### Post by john newbuntu on 2009-12-01
To implement Mark's suggestion, take a look at this excellent article that illustrates installation from a liveCd:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Walking through the install on this site, I assume that all your Ubuntu stuff will go into partitions on /dev/sdb (the second drive).  So, when it comes to slide 27, if you do not want to play with partitioning at this time,  you are going to let the installer choose entire second drive (sdb) for installing ubuntu. 

Now, very carefully, somewhere three quarters way down, on slide number 35 is a "Ready to install" screen.  This is where you would click the advanced button.  In the drop-down for "devices for boot loader installation", you will choose /dev/sdb1 since you do not want the MBR on first disk to be disturbed. Complete the installation.

You will also have to change the BIOS setting to boot from second disk first and then the first disk.  This way, Grub2 comes into the picture.

---

### Post by warren181 on 2009-12-01
Ok thanks Ill try it when i build my new computer in a few weeks when i have brought my new processor

Warren

---

