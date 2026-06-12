---
title: "How to remove Ubuntu Netbook 10.04 and back to original"
date: 2010-09-07
forum: General Help
---

### Post by ssobox on 2010-09-07
I am very new ubuntu or linux user.  Last week, I had download ubuntu netbook 10.04 version and use it from booting by USB key.  I found it quite useful from USB and eventually installed it on my Gateway netbook, that's where my nightmare started.  At installation option gave me to ubuntu side by side with my Windows Vista on the netbook.  It used part of hard drive space to create a separate partition for ubuntu.  Intallation is OK but display is very bad particular moving the mouse around Firefox.  Screen turned white back ground right with messy character font.  It tried move around and have to restart ubuntu to get out.

I thought it might be something display drive not setup but found no option to make change from within Ubuntu.  I had frustrated to search for fixing option and decide to "remove" ubuntu from the netbook.  The worst, there is no option whatsoever on how to remove it.  I search this forum and script to delete the partition from terminal.  When it restart, the MBR or Grun loaded with errors incorrect file system.  That mean the MBR not load and it is a netbook.  It does not come with Vista CD for me to fix MBR nor resize the partition.  I had to re-install ubuntu again back to square one to use it size by size with Windows.

Any one have a clean and details steps on how to remove ubuntu, resize partition and able to bring the netbook back to Windows only?

---

### Post by MooPi on 2010-09-07
When you purchased the Gateway netbook did it come with instructions on restoring the computer to manufactured defaults ? What is the model# of your netbook ? Do you have an external CD/DVD drive ? You may have to contact Gateway to get the appropriate software.

---

### Post by ssobox on 2010-09-07
It come with image on a hidden partition.  I had used it to restore back to factory default but it only touch the windows partition, not the one Ubuntu is using.

The netbook had no CD media nor a external/internal CD/DVD drive.

---

### Post by MooPi on 2010-09-07
Removing Ubuntu is as simple as inserting your usb thumb drive and starting an application called gparted to remove the Ubuntu partition. The MBR is another issue altogether. Please tell me your model number as Gateway may have a function key set to start your restore without booting the OS.

I have just visited the Gateway Support page to get info on restoring your netbook back to original. During boot depress Alt + F10 repeatedly to start restore feature. I'm hoping this will repair the MBR. I'm not certain it will but it is worth a shot.

---

### Post by ssobox on 2010-09-07
It's a Gateway LT20.

This is exactly the same way I did on my last try.  I delete the Ubuntu partition by using Gparted and restart got file system error.

When I user the default image to restore Windows, it only able to see the NTFS partition not the empty space which left behind by Ubuntu.

---

### Post by MooPi on 2010-09-07
I should have instructed you to increase the size of your ntfs partition to absorb the empty space with gparted. You will probably be without a good MBR and unable to boot but your partition size will be what you need.  You may need to borrow an install CD and external drive to correct your MBR. I was hoping the restore process would correct your MBR.

---

### Post by garvinrick4 on 2010-09-07
Insert usb thumb drive and boot off of it: open a terminal:
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```

May show error messages about the rest of lilo missing, ignore, we just want MBR

Reboot into Windows.

---

### Post by MooPi on 2010-09-07
> **garvinrick4 said:**
> Insert usb thumb drive and boot off of it: open a terminal:
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR

Reboot into Windows.
Can grub be used in a similar fashion to fix MBR ?

Just found a solution for grub2,    [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by ssobox on 2010-09-07
Sorry, what is the meaning of these two line command script will do?

---

### Post by garvinrick4 on 2010-09-07
> **ssobox said:**
> Sorry, what is the meaning of these two line command script will do?
Read under description:
rick@rick-laptop:~$ aptitude show lilo
Package: lilo
State: not installed
Version: 1:22.8-8ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,229k
Depends: mbr, debconf (>= 1.2.9) | debconf-2.0, libc6 (>= 2.7),
         libdevmapper1.02.1 (>= 2:1.02.20)
Suggests: lilo-doc
Conflicts: manpages (< 1.29-3)
Description: LInux LOader - The Classic OS loader can load Linux and others
 This package contains lilo (the installer) and boot-record-images to install
 Linux, OS/2, DOS and generic Boot Sectors of other OSes. 
 
 You can use LILO to manage your Master Boot Record (with a simple text screen,
 text menu or colorful splash graphics) or call LILO from other Boot-Loaders to
 jump-start the Linux kernel.

---

### Post by ssobox on 2010-09-10
garvinrick4: I got you private message the other day.  I m try to borrow an external CD rom to try whatever option other guy have mentioned.

---

