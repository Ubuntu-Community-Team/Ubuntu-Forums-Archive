---
title: "[Serious] I fails to access my Windows 7 OS"
date: 2011-09-10
forum: General Help
---

### Post by fungw on 2011-09-10
Please really help me on this. 
Everything is in Ubuntu 10.10.

I have a gateway laptop with window 7 installed, then i installed Ubuntu (duel-boot). Every is fine, I loved it too. I got window and ubuntu together. But few days ago I open my computer and get "grub rescue" screen when I starting up my computer (I probably did something wrong the day before..don't know). So what i figure out is there is something wrong with my grub obviously. So I go plug my ubuntu USB drive (the ubuntu installation) into my laptop and try installing in. When I install it i decide to only use 10 GB of space for Ubuntu and 5 GB for swap area, because there is only two option appear on the screen, "Use entire disk" or Manually divide the drive up. (I know it must of done something wrong up to this point). After I install it, I can't see anything from my previous ubuntu and also my Window 7 OS in grub. My window 7 side is complete disappear. I am so scare, i beg u guys to help me out here.

I really need to access my Windows 7 OS and retrieve some data by today. Please help!!!I am new to ubuntu and linux. Please help me please!!!

---

### Post by gandaran on 2011-09-10
> I really need to access my Windows 7 OS and retrieve some data by today. Please help!!!I am new to ubuntu and linux. Please help me please!!!
cant you see the windows drives in the file browser while running ubuntu from the live cd or usb flash drive?
run gparted using the live cd or usb drive then post a screenshot here so we can take a look at the hard-drive partitions.

---

### Post by fungw on 2011-09-10
What is gparted?? And plus I can't see my windows drivers in file browser at all...

---

### Post by TurtleKing on 2011-09-10
What option did you choose? You didn't exactly tell us that in 1st post ("after I installed it"). I am afraid if you chose entire disk, your options look very bad (Ubuntu data was written over Windows data). As for gparted, that is an application that lets you see your drivers installed with Operating System. In Ubuntu 11.04 we have Disk Utility as default under System > Administration, so I don't remember what comes shipped as default for Ubuntu 10.10. If you do have  Disk Utility then open it, and just LOOK around. Hopefully it will list Windows in there. 

For the future, if you have important stuff on a Windows or Mac hard drive/solid state drive just buy a cheap hard drive that has enough space for Ubuntu and is compatibly with your system specs.
What has happened to you could also happen if your hard drive malfunctioned (without Ubuntu being involved). I have 2 hard drives because one of them already passed it's warranty year, so if it fails I am safe with the other. If you don't have a lot of important documents, then just save them on a flash drive and partition your 1 hard drive accordingly (my friend's approach). You always want to have a backup in case bad things happens.

I think they should add this to the Ubuntu download page as a "Warning!!! click for more information" option. Seems a lot of windows folks are unaware that **** happens when putting stress on 1 hard drive.

---

### Post by foureyesboy on 2011-09-10
Sorry, a little confused.

When you booted to Ubuntu on USB after the GRUB rescue screen, how many partitions did you see?  Did you see the Windows partition?

Have you chosen "Use entire disk" option while you re-installed Ubuntu?

---

### Post by fungw on 2011-09-10
I am very sure that i didn't press the button "Use Entire Disk" when i was installing it

Also I don't see any word that says "Windows" in ubuntu's disk management, same goes to the grub menu. Please help me here, i am getting even more scared. 

Also i am using a school internet which after you connect to the network, you must log-in inside your browser. But using the Ubuntu's Firefox, it always fails to prompt the log-in screen to me, whereas in windows, the Firefox works fine.

---

### Post by fungw on 2011-09-10
Inside the disk utility:

10GB ext4
Usage: Filesystem

5GM swap space

Extened 310 GB (This should be where my window 7 is located)
Usage: Container for logical partitions

302GB ext4 (??)

3.1GB swap space


Inside grub menu: 
Ubuntu, with linux 2.6.35-22-generic
Ubuntu, with linux 2.6.35-22-generic (Recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

---

### Post by TurtleKing on 2011-09-10
> **fungw said:**
> I am very sure that i didn't press the button "Use Entire Disk" when i was installing it

Also I don't see any word that says "Windows" in ubuntu's disk management, same goes to the grub menu.

Weird. If you didn't select "Use Entire Disk", do you remember how you setup your partitioning? I think you can still delete windows by accident using this feature. If Grub or disk management don't recognize it, then I am stumped. Maybe try re-installing Grub, but wait for a more expert member to reply before doing so.

---

### Post by fungw on 2011-09-10
I pretty much give 10 each, 10gb for ubuntu and 10gb for swap area. The rest untouched.

---

### Post by techvish81 on 2011-09-10
if you select to install ubuntu "alongside windows 7" then only u can br sure that you are not deleting win7.. otherwise there is always a possibility to delete it. i think you have selected the third option "something else" while installation and accidentally deleted win 7. 

if you have not deleted or formatted win7 partition ,you can view the contents or filesystem of win 7 in file manager. only one thing is possible out of these two.

---

