---
title: "Problem with bootloader"
date: 2012-03-24
forum: General Help
---

### Post by tomislav91 on 2012-03-24
I have windows7 and ubuntu11.10.
I had the burg bootloader. All seems fine,until i choose to delete burg with the apt-get remove and install burg, after that, only the ubuntu show me(ubuntu,ubuntu rec.mode,mem test), but where is missing windows 7?
I notices that in the boot folder have the both(grub and burg) bootloader, and can't remove them. 
Where is the problem?

---

### Post by idoitprone on 2012-03-24
> **tomislav91 said:**
> I have windows7 and ubuntu11.10.
I had the burg bootloader. All seems fine,until i choose to delete burg with the apt-get remove and install burg, after that, only the ubuntu show me(ubuntu,ubuntu rec.mode,mem test), but where is missing windows 7?
I notices that in the boot folder have the both(grub and burg) bootloader, and can't remove them. 
Where is the problem?

if grub is in the mbr, then ignore the burg file in / it should be harmless

```
sudo update-grub
```

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

here is the boot script, it should give anyone here enough detail to diagnose your problem

---

### Post by tomislav91 on 2012-03-24
> **idoitprone said:**
> if grub is in the mbr, then ignore the burg file in / it should be harmless

```
sudo update-grub
```[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

here is the boot script, it should give anyone here enough detail to diagnose your problem


I remove all bootloaders,and install again and update grub and not help. :confused: :confused: :confused:

---

### Post by idoitprone on 2012-03-24
> **tomislav91 said:**
> I remove all bootloaders,and install again and update grub and not help. :confused: :confused: :confused:

can you run the boot script in the link

there are instructions on how to run it

obviously, we need to have details of your installation, hence we dont want to bork your installtion doing it blind

---

### Post by imachavel on 2012-03-24
don't want to pop in uninvited. Anything wrong with the idea of using the linux live cd, booting to it, and selecting fix grub? boot repair cd is another .iso you can download, burn to cd, then boot to and select fix grub, and it will also fix mbr. Just in case that doesn't work, if you could load the OS, and look for boot repair or install it via the terminal

ctrl+alt+delete

to open a terminal, then run sudo apt-get install boot repair or boot-repair, or download it then install it by finding software manager, then searching for boot repair and installing it, you can create a grub script and upload it into this thread as an attachment, considering that all your drivers load and you have a nic driver working and .net framework interface and access to the web over a healthy i.s.p. connection with a healthy public i.p. address. Now, you said you can get on ubuntu partition but not windows 7? Well I'd try boot-repair to fix the grub and mbr. Worked for me I had the exact same problem. I'd try to create the script with that link provided by idiotprone

or perhaps, you could try another method. You could download gparted .iso, untar it in downloads, right click on it and select to burn with brasero disk burner, reboot the computer and boot to gparted, and try setting the boot flag to windows instead of Ubuntu. I strongly don't think this will address the issue. Or you could try to put the windows 7 disk in, and follow this guide to fix mbr:

[http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html)

But now if the boot flag is set to /dev/sda1(assuming that's ubuntu and the swap partition is set to next partition, windows 7 set to partition after that, etc.) then grub might not like to be reset this way. I'd upload the script, and surely try using boot-repair, boot repair has worked the best for me. I hate mixing windows and ubuntu grub, one must be installed first because windows mbr and grub loader hates sharing and is picky about boot flag etc. And wubi is worst way to install. Best of luck, report back

---

