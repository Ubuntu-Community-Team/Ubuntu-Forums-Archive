---
title: "Unable to install server"
date: 2011-10-06
forum: General Help
---

### Post by stuffses on 2011-10-06
I have a netbook that I am trying to install Ubuntu-server 11.04 on, but when I boot from the drive, nothing happens, except for the flashing white line at the top left.

CPU: Intel Atom N270 (i686)
Ram: 2GB
Current OS: Backtrack-Linux 5 r1 (This installed fine)

I used the ubuntu-11.04-server-i386 download.
The iso is put on a USB flash drive, using Universal-USB-installer. (I also tried with uNetBootin)

---

### Post by stuffses on 2011-10-06
I just tried with Ubuntu-server 10, same result. Will now try with 9.

---

### Post by ubudog on 2011-10-06
So, you put the disk in, start the server, tell it to boot from CD, and all you see is a white line?  How long did you wait?

---

### Post by stuffses on 2011-10-06
Its a usb stick, and I waited 1/2 an hour. This method worked fine with Backtrack-Linux

---

### Post by ubudog on 2011-10-06
Yeah, USB, sorry!  ](*,)

What kind of flash drive are you using?

---

### Post by ubudog on 2011-10-06
Suggestion: 

Backup your data, then format the flash drive to FAT32, with a single partition.  Then, use unetbootin to copy the .iso to the drive.  

Try booting again.

---

### Post by stuffses on 2011-10-06
Transcend 8GB, and I also tried with a few others.
Also, Ubuntu 9 booted fine, but after choosing the keyboard layout, it wanted to know where the CD-ROM was, even when I was installing from USB.

---

### Post by stuffses on 2011-10-06
> **ubudog said:**
> Suggestion: 

Backup your data, then format the flash drive to FAT32, with a single partition.  Then, use unetbootin to copy the .iso to the drive.  

Try booting again.

I tried unetbootin with ubuntu-server 11, and 10, but ill try it with 9.

---

### Post by bodhi.zazen on 2011-10-06
I think there is some problem booting the server iso from usb, but I do not recall what =)

See this link :

[http://www.pendrivelinux.com/run-ubuntu-server-edition-installer-from-usb/](http://www.pendrivelinux.com/run-ubuntu-server-edition-installer-from-usb/)

They provide a script to make the usb, you can look at the script to see what to do or just run the script.

---

### Post by Vishal Agarwal on 2011-10-06
Hi,
While worked this much heard; do some more testing. If you have the desktop version; then try installing that from the USB drive. Further you can later remove the desktop version and install the server version.

---

### Post by stuffses on 2011-10-06
Ok, so, Ubuntu-desktop 9.10 works, and installs fine, but I would really like to have Ubuntu-server 11.04. Any other ideas?

---

### Post by Vishal Agarwal on 2011-10-07
I myself personally believe in LTS. Presently I am using the 10.04.03 LTS Server/Desktop for my office server and for my laptop at home/office.

---

### Post by bodhi.zazen on 2011-10-07
> **stuffses said:**
> Ok, so, Ubuntu-desktop 9.10 works, and installs fine, but I would really like to have Ubuntu-server 11.04. Any other ideas?

Did you read the link I gave you ?

---

### Post by stuffses on 2011-10-07
Yes, 10.04 didn't work either. (Using that script to install it to the USB)

Ubuntu-server 9 worked, but wanted a CD Drive. So now I'm going to try Ubuntu-Desktop-9.10, because apparently it doesn't check for CD Drives.

So now I'm stuck with Desktop 9, (Set to boot to terminal). How much of a difference would it make if I managed to switch to server 11?

---

