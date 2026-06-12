---
title: "running gparted off cd"
date: 2010-08-02
forum: General Help
---

### Post by dsub42 on 2010-08-02
HI im really new to linux and struggeling...

I want to run gparted off the cd so that I can extend the ubuntu partition of my computer...

I hdownloaded the gparted iso file and burnt it onto a CD...

but how do i run the software?? .... there appears to be 3 folders on the cd (isolinux, live and syslinux) and two other files 'copying' and 'g-parted live version' - these two are both text files...

Any help would be appricated

---

### Post by oldfred on 2010-08-02
It is a bootable CD running linux. You need to have all partitions unmounted so you boot from the CD. But often liveCDs will use a swap partition so you may have to click (right click?) on the swap partition and swap off.

---

### Post by dacman48 on 2010-08-02
if u want a cd what u have to do is download this->[http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.6.1-2/gparted-live-0.6.1-2.iso/download](http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.6.1-2/gparted-live-0.6.1-2.iso/download), and burn the iso to a cd
if a live usb is more your speed, download this->[http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-v1.7.6.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-v1.7.6.exe) and choose gparted from the dropdown menu. click the box tthat says download iso, choose your flash drive, then click next and enjoy the ride

---

### Post by snowpine on 2010-08-02
How did you install Ubuntu? Gparted is on the Ubuntu Live CD, if you have one.

---

### Post by dsub42 on 2010-08-02
I downloaded the iso from the first link you posted ... when it unpacked the files on the cd they appear as I said in my first post...

but now how do i run the software...?

when i start up ubuntu and put the cd ... nothing autoruns?..... what do i need to do?

---

### Post by dacman48 on 2010-08-02
oh... u dont know how to burn an iso. this complicates things >.<. alright, ddownload this->[http://sourceforge.net/projects/portableapps/files/InfraRecorder%20Portable/InfraRecorder%20Portable%200.50%20Rev%204/InfraRecorderPortable_0.50_Rev_4.paf.exe/download](http://sourceforge.net/projects/portableapps/files/InfraRecorder%20Portable/InfraRecorder%20Portable%200.50%20Rev%204/InfraRecorderPortable_0.50_Rev_4.paf.exe/download), and install it. its a portable app, so it doesnt matter where. after that open the app and choose the burn image option and find your iso. burn the cd, and get back to us

---

### Post by Quackers on 2010-08-02
It's an .iso file. You won't see the .iso file, just the others. Burn the .iso to cd with an iso burner (like imgburn for example). Then shut down the system and boot from the disk.

---

### Post by dsub42 on 2010-08-02
i have downloaded that portable app thing .. but when i double click to open/install it .. i get this error!...
======


rchive:  /home/matt/Downloads/InfraRecorderPortable_0.50_Rev_4.paf.exe
[/home/matt/Downloads/InfraRecorderPortable_0.50_Rev_4.paf.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/matt/Downloads/InfraRecorderPortable_0.50_Rev_4.paf.exe or
          /home/matt/Downloads/InfraRecorderPortable_0.50_Rev_4.paf.exe.zip, and cannot find /home/matt/Downloads/InfraRecorderPortable_0.50_Rev_4.paf.exe.ZIP, period.

---

### Post by dacman48 on 2010-08-02
oopsie, ur running ubuntu... my bad. okay, go to applications->sound and video->brassero and choose the burn image file option. select ur image and burner and hit okay

---

### Post by dsub42 on 2010-08-02
cheers... but now when i select the iso file using brassero .. i am not able to select a disc to write to ... its like my CD drive isn't recognised?... it says no disc available 

im slowly loosing the plot with ubuntu! 

any ideas?

---

### Post by dsub42 on 2010-08-02
anyone?

---

### Post by dsub42 on 2010-08-02
i finally got it to work .. but when i boot from the cd i get as far as a message saying gparted use at your own risk.... but thats it then my pc reboots....?

---

### Post by dacman48 on 2010-08-02
redownload, reburn, reboot, rejoice!

---

