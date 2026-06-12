---
title: "Disk space on a Ubuntu live usb installation"
date: 2010-02-07
forum: General Help
---

### Post by Hempriggs on 2010-02-07
Hi
 
I'm completely new to Ubuntu but trying out an experiment where the ultimate aim is the freedom from windows.
 
Anyway, my apologies if this is in the wrong section but as a new user I am not sure where I am going wrong but please boot me to the right section if I am posting in the wrong place.
 
Ok, My cunning plan was to create a live USB ubuntu 9.1 installation to run warcraft. I used pen drive linux and after 3 attempts it worked and there was much happiness. I set up with a 4GB casper rw file as this was the biggest I can select. Its on a 32GB stick though so I partitioned 26GB seperately and formatted that as ext3, the idea being I would mount that and use it for the install plus whatever else cool toys I found in the wonderful world for linux.
 
The issue I have is that while dowloading once I passed 3GB download ubuntu keeps telling me I am out of disk space despite the fact I have 23GB free in the ext3 partition. When I look at the root under the "file manager" it says I have zero bytes free but once I move to the folder where the ext3 partition is mounted I suddenly have my 23GB free. I also tried plugging in my external hard drive with 120GB free and while it mounted successfully in the /media directory it has not solved my root being full problem, which has not only stopped my download but now prevents me from downloading anything else. 
 
I can open openoffice files and can save them, it complains that its out of disk space then 10 seconds later it saves successfully, so to my windows experienced eye it looks like there is space there. I think the data saved in the partition is subtracting potential saving space in the casper file while not actually taking up any space, which is annoying.
 
Is the 4GB a limitation of the live usb install or am I missing something obvious and trivial? 
 
Also, if I was to select the "install ubuntu to my hard drive" could I save it properly to a memory stick without the casper file or does it have to be a hard drive on my machine? There are very good reasons why I can't install on the hard drive
 
Thanks
Hemp

---

### Post by undecim on 2010-02-07
The 4GB limit is a limitation of the filesystem that is used on a persistent install. The Casper rw file is a file on the thumb drive that is treated like another disk, but because the thumb drive is made to be compatible with other operating systems for storing files, it has to use a FAT32 filesystem, where 4GB is the maximum file size.

I would recommend using an ubuntu CD to install Ubuntu on to the thumb drive, using these instructions:[https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Method%201:%20Installing%20Ubuntu%20directly%20to%20USB%20drive%20from%20installer%20CD]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Method%201:%20Installing%20Ubuntu%20directly%20to%20USB%20drive%20from%20installer%20CD")

This will allow you to use the entire storage capacity of the drive while running your computer from it, but you will no longer be able to store files on this drive from other computers unless you repartition it.

You should note, as it is stated in that article, that you should use the "Advanced" button from the installation summary screen before installing and make sure that Grub is installed to your thumb drive rather than your hard drive. If you want to be extra careful, and you are comfortable taking a screw driver to your computer, you can try removing or disconnecting your hard drive before installing to the thumb drive.

---

### Post by Hempriggs on 2010-02-07
Cool thanks will have a go. :)

---

