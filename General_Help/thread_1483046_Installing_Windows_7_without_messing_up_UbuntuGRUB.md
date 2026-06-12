---
title: "Installing Windows 7 without messing up Ubuntu/GRUB"
date: 2010-05-14
forum: General Help
---

### Post by joosto on 2010-05-14
Hello all,
I'm thinking about upgrading my Windows Vista to Windows 7. I rarely ever use it but I figured that when I do have to use it I would rather use Windows 7.

Will it mess up Ubuntu or GRUB when I do this? Like GRUB not recognizing Ubuntu any more? I don't really know but I just wanted to ask this here just in case.

Thanks :)

---

### Post by SeQueNceR on 2010-05-14
as far as i know, you will lose the GRUB. but it's not an issue. you can restore it using many ways.

check this link for restoring your GRUB using live cd

[http://ubuntuforums.org/archive/index.php/t-1199520.html](http://ubuntuforums.org/archive/index.php/t-1199520.html)

or if you ain't a power linux user. you can fix it under windows using **auto super GRUB**

download it from here [http://www.supergrubdisk.org/index.php?pid=12](http://www.supergrubdisk.org/index.php?pid=12)

here is a simple how to use

[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

I wish this helps!

---

### Post by ff1-ff1 on 2010-05-14
if you have grub installed on MBR you may expect unexpected :) 
This type of grub installation is forced by whole community and in my opinion this is mistake because of this problem during windows installation.
In my case grub is always installed on main partition of linux (with system).If i want to reinstall windows i have to use cfdisk to change bootable partition from linux to partition with windows.After reboot  hdd behaves like without linux -starts directly windows.So now i have clear street to reinstall windows.After that  i have to start live cd with linux,mount partition where is located linux,using cfdisk change boot partition to linux .And now i have windows,linux and working grub.This solution is demanding only when i want to install windows.During linux installation i dont need to mount something and change like in this description.
Because community is forcing more dangerous (but on first look better) solution,many people have problems during re-installation of windows.
Decision is yours-as usually....

---

### Post by cap10Ibraim on 2010-05-14
I think yes it will mess up Grub 
you  can use the ubuntu live cd  Refer to [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) sections 6 and 7  
or get the [Super Grub Disk]("http://www.supergrubdisk.org/") when you finish installing windows boot this CD super grub will see Ubuntu boot to Ubuntu and Reinstall Grub

---

### Post by Mark Phelps on 2010-05-14
MS Windows OSs always overwrite the MBR whenever you do an install, so in this case, your MBR will get replaced.  There's simply no way to avoid that.

As already mentioned, however, it's then a simple matter to reboot using an Ubuntu LiveCD and reinstall GRUB.  

After that, boot back into Ubuntu, open a terminal window, and enter "sudo update-grub".  That will regenerate your GRUB menu and SHOULD add an entry for Win7.

---

### Post by joosto on 2010-05-14
Thanks guys!

It indeed deleted my GRUB as expected. I will AutoSuperGrubDisk since I don't have a LiveCD lying around. 

Again, thanks for the help/tips :D.

---

### Post by cap10Ibraim on 2010-05-14
So did you like windows 7 ? I think it's a great OS

---

