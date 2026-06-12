---
title: "USB not mounting. EEEPC"
date: 2010-12-11
forum: General Help
---

### Post by sarsar on 2010-12-11
Hey,

Heres the background: Im running 10.10 desktop on an Asus EeePC. Ive managed to rectify most common problems, but it will not mount a USB. It does not come up in the places menu - I have to manually mount it in the terminal. 

However, i can only READ the documents, i cannot edit or save documents to the USB disk - it opens ion read only mode. (Im using open office 3.2 by the way). 

I have tried doing this with a new document. It will not save, it is saying the location does not exist and cannot mount the USB. I know this is a mounting USB problem exclusively as it will save documents and allow me to edit them from the home folder, the desktop and the documents folder. 

I think this is probably very easy to solve. 

Thanks in advance

SarSar

---

### Post by pytheas22 on 2010-12-11
My first guess would be that you're mounting the USB stick with permissions such that only root can save to it.  Which command are you using when you mount it?

Also, have you tried figuring out why the USB stick won't auto-mount like it should?  The first place I'd look would be at the output of "dmesg" right after plugging in the USB stick.  Solving that problem would likely solve the larger issue as well, because when your stick is auto-mounted, the permissions will be set to allow ordinary users to save to it.

---

### Post by tajiknomi on 2010-12-11
!

---

### Post by sarsar on 2010-12-11
in looking on internets - now using 

#sudo mount -t vfat <device name> /media/usbdrive -o uid=1000,gid=100,utf8,dmask=027,fmask=137

and now I can read and write and what not. jolly good

Now the only problem is the usb device is not auto mounted. other usb devices do and are visible in places menu. i am looking into the problem with usb 2.0 devices not being compatibel or something like that. Another forums told me to  unmod ehci_hcd

however, when i unmod i get the error "Module ehci_hcd does not exist in /proc/modules"

so... the plot thickens.

Thanks

---

### Post by tredegar on 2010-12-11
I had the same problem.....

I went nearly crazy trying to install 10.04 on my 4GB eee701 a month ago.
I was installing from a USB stick.
I wanted most of **/** on the 4GB SSD
But I wanted **/usr** and **/home** on a 16GB SDcard plugged into the slot.
I allocated a partition on the SDcard (at install time, this was seen as **/dev/sdc**) to **swap**.

Install finished, and I removed the install-stick and rebooted. Everything worked _except_ automounting of USB drives.

It turned out that **/etc/fstab** was at fault, because once the install USB stick was unplugged the disk ordering was bad - **swap** was at **/dev/sdc1** which did not exist at boot, and when I plugged in a USB stick, the kernel allocated it to **/dev/sdc1** but this was already (incorrectly) referenced in **fstab** as being **swap**. (I know ubuntu now usually defaults to UUIDs in **fstab**, but it does *not* do this for **swap**. Don't ask me why.)

I corrected the reference to **/dev/sdc1** in **fstab**, rebooted and all was back to normal.

USB sticks and my iPod touch work again.

Only took me three days to solve that problem. It was a sneaky one.

So, my advice is: Check your **fstab** *very* carefully.

---

### Post by sarsar on 2010-12-11
> **tredegar said:**
> I had the same problem.....

So, my advice is: Check your **fstab** *very* carefully.

you, good sir, are the man!

I checked fstab and saw this:

/dev/sdb1  /      ext4  users,user           0  1 

damn thing trying to mount to root! drive is also vfat...so...changed to this:

/dev/sdb1  /media/usbdrive      vfat  users,user           0  0


and works fine! you are awesome. I would have your back in a knife fight.

---

