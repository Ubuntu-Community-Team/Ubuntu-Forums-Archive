---
title: "unable to unmount usb drives when not root"
date: 2010-05-02
forum: General Help
---

### Post by gautambatra on 2010-05-02
Hi,
I'm fairly new to ubuntu. After upgrading from 9.10 to 10.04 I am unable to unmount usb drives when I'm not root. Every time I have to type "sudo umount /media/... " and give my password. When I right click the drive and click unmount, I get the following message:
Unable to unmount disk1
unmount: /media/disk1 not is not in the fstab (and you are not root)

How can this be solved?

---

### Post by Mr Gates on 2010-05-02
I am also having this exact same issue. I have found that none of my external drives or USB sticks given me the authority to add/delete or modify the files on them.

---

### Post by tomfin on 2010-05-05
> **gautambatra said:**
> Hi,
...After upgrading from 9.10 to 10.04 I am unable to unmount usb drives ... When I right click the drive and click unmount, I get the following message:
Unable to unmount disk1
unmount: /media/disk1 not is not in the fstab (and you are not root)

How can this be solved?


Not solved, but a GUI-based workaround if you just want to eject the disks without using the command line.

Go to "Places" menu and choose "Computer"; this'll show your connected drives, including any that are USB-connected (you'll notice the USB symbol on the drive icons).   Right-click the drive and choose "**Safely remove drive**".  This should power down the USB device and unmount any volumes associated with it.  

Note this is *not* the same as right-clicking a desktop drive icon and choosing "Unmount" - that would keep the USB device connected if, for example, you then planned on using GParted to repartition an external USB harddisk but had to unmount the partitions first.  "Safely remove drive" cuts all power to the USB device and it's not seen again until it's physically replugged.

Same dialog box and message here.  Reminds me of a delightful old story ([link](http://www.newhorizonssucks.net/LiveCD.html)).


EDIT: In case anyone's paying attention and trying to fix this, I've noticed the perpetually-mounted USB disk behaviour might be related to Nautilus (the Gnome filemanager) being misinformed that the USB disks are in fact fixed internal disks (which rightly *do* have entries in /etc/fstab and therefore are unmountable via right-click).  Oddly, killing the nautilus process in system monitor so it restarts itself while the USB disks are still connected changes their desktop icons from standard fixed-disk icons to USB-disk icons, and right-clicking them now rightly gives the "Safely Remove Drive" option instead of the bog-standard "unmount".

In any case, it seems that drives listed under "Computer" in the places menu are mountable/unmountable/removable correctly, and it's just the convenient desktop icons that are misbehaving.

---

### Post by Handssolow on 2010-05-11
> **tomfin said:**
> Not solved, but a GUI-based workaround if you just want to eject the disks without using the command line.

Go to "Places" menu and choose "Computer"; this'll show your connected drives, including any that are USB-connected (you'll notice the USB symbol on the drive icons).   Right-click the drive and choose "**Safely remove drive**".  This should power down the USB device and unmount any volumes associated with it.  

Note this is *not* the same as right-clicking a desktop drive icon and choosing "Unmount" - that would keep the USB device connected if, for example, you then planned on using GParted to repartition an external USB harddisk but had to unmount the partitions first.  "Safely remove drive" cuts all power to the USB device and it's not seen again until it's physically replugged.

Same dialog box and message here.  Reminds me of a delightful old story ([link](http://www.newhorizonssucks.net/LiveCD.html)).


EDIT: In case anyone's paying attention and trying to fix this, I've noticed the perpetually-mounted USB disk behaviour might be related to Nautilus (the Gnome filemanager) being misinformed that the USB disks are in fact fixed internal disks (which rightly *do* have entries in /etc/fstab and therefore are unmountable via right-click).  Oddly, killing the nautilus process in system monitor so it restarts itself while the USB disks are still connected changes their desktop icons from standard fixed-disk icons to USB-disk icons, and right-clicking them now rightly gives the "Safely Remove Drive" option instead of the bog-standard "unmount".

In any case, it seems that drives listed under "Computer" in the places menu are mountable/unmountable/removable correctly, and it's just the convenient desktop icons that are misbehaving.

thanks tomfin, your edit sheds some more light on this issue with USB sticks. Here's another thread discussing similar issues.
[http://ubuntuforums.org/showthread.php?t=1478368&page=3](http://ubuntuforums.org/showthread.php?t=1478368&page=3)

---

### Post by manupaz on 2010-05-13
hi,
 
I have the same problem but I think worst :-(
 
When my old Ubuntu 9.04 told me to upgrade to 10.04 I accepted without any doubt. Until this moment all my USB storege devices worked fine and with no fail. 
 
After the upgrade, my computer is unable to mount USB disks (500 Mb) or if the device is mounted (Pen drive 16 Gb), I'm not able to write in it. 
 
In addition, I had a folder network shared (Samba) and it's unreacheable too. 
 
I have some files that I need to copy to a USB before formatting the computer and restore the 9.04 Ubuntu version.
 
Any help?
 
Thanks a lot.

---

### Post by TheStroj on 2010-05-13
Happened to me also. The upgrade changed my permisions so i was unable to hear sound, mount... Go to Users and Groups and modify your permissions (you will need root passsword for that). When you open it just go to the advenced section and user permissions and select those that you want/need.

---

### Post by Handssolow on 2010-05-15
I selected all user permissions but still when I plug in a USB stick and it mounts, root has permission not me the user. Instead I'm using gksudo nautilus to unmount USB0 for example then close nautilus down. I then open Places, a left click where it shows my USB stick's file system, an icon appears on my Desktop and my USB stick's files can be modified.

But I missed something here, my user id is 1000 but it says "You can't change the user ID when the user is logged in", I'm thinking that 1000 is correct anyway.

When I've finished with the USB stick a right click shows me the option to remove it safely. (It also show eject too, not sure why).

---

### Post by hihihi100 on 2010-05-18
Similar problem here:

I can see the plugged external hard drive icon in the desktop, but not under its name (Volume 1), but USB0, I can access the files in the external hard drive and modify them, I can add files and extract files, and Gparted recognizes the external hard drive under its own name (Volume 1). Also, the OS (10.04) recognizes the mount point (in my case, /media/usb0), but cannot show the proper label (Volume 1)... see attached pictures. In the second one, you can see that both "Volume 1" and "/media/usb0" appear as independet USB sticked external hard drives, but I can only access the "/media/usb0" one...

tips please

---

### Post by pregiopomo on 2010-05-23
I've been having the same problem for a while, and I went for the   solution posted here (modyfing the etc/fstub) then I finally went to   test it with the laptop of a friend that recently installed Ubuntu   10.04, and on his computer everything worked fine.

So I checked out the Synaptic packages he had installed by default, and I   realized that I had some more that probably were creating some   conflicts/problems.

Now it works again!!

Here is what i did:

- start the "synaptic package manager"
- insert "usb" in the quick search
- compare your installed packages with the following list (these are the   one installed by default):
:arrow: 
 usbmuxd
    usbutils
      libusbmuxd1
      libusb-0.1-4
      libusb-1.0-0
      xserver-xorg-video-sisusb
      libmtp8
      usb-creator-gtk
      usb-creator-common
      libmobiledevice0
      libgphoto2-port0
      libgphoto2-2
      media-player-info
      libhpmud0
      hpijs
      hplip
:arrow:
- remove those packages that have been added by you or that may cause   conflicts, in my case I had all the previous ones and I removed the   following that I added months ago messing up with my laptop:

     :arrow: 
usbmount  (yep it sound weird, but now is working properly in my   laptop!)
       pyton usb
       usb creator
       gnome pilot
:arrow:

I hope this example might help some people as I did received help reading   this forum, this is not "THE WAY" you "HAVE TO" follow to solve this   problem, but this is just a way that worked for me, and I think is worth   to be shared :wink:

---

### Post by consularo on 2010-05-26
Pregiopomo... your recommendations worked perfectly here... thanks a lot...

---

### Post by timgood on 2010-05-26
A quicker way that worked for me was to uninstall pmount, and then re-install it.

Hope this helps.

---

### Post by Handssolow on 2010-06-14
> **timgood said:**
> A quicker way that worked for me was to uninstall pmount, and then re-install it.

Hope this helps.

Thanks timgood. I uninstalled pmount, switched off then re-installed pmount. Looking good so far.

Edit:As reported elsewhere, it was usbmount that I had to remove for normal use of my usb sticks to return. With it I didn't have permissions to alter files on a usb stick.

---

### Post by sr20ve on 2010-07-09
thanks pregiopomo that worked for me :D

---

### Post by khopek on 2010-07-10
> **pregiopomo said:**
> I've been having the same problem for a while, and I went for the   solution posted here (modyfing the etc/fstub) then I finally went to   test it with the laptop of a friend that recently installed Ubuntu   10.04, and on his computer everything worked fine.

So I checked out the Synaptic packages he had installed by default, and I   realized that I had some more that probably were creating some   conflicts/problems.

Now it works again!!

Here is what i did:

- start the "synaptic package manager"
- insert "usb" in the quick search
- compare your installed packages with the following list (these are the   one installed by default):
:arrow: 
 usbmuxd
    usbutils
      libusbmuxd1
      libusb-0.1-4
      libusb-1.0-0
      xserver-xorg-video-sisusb
      libmtp8
      usb-creator-gtk
      usb-creator-common
      libmobiledevice0
      libgphoto2-port0
      libgphoto2-2
      media-player-info
      libhpmud0
      hpijs
      hplip
:arrow:
- remove those packages that have been added by you or that may cause   conflicts, in my case I had all the previous ones and I removed the   following that I added months ago messing up with my laptop:

     :arrow: 
usbmount  (yep it sound weird, but now is working properly in my   laptop!)
       pyton usb
       usb creator
       gnome pilot
:arrow:

I hope this example might help some people as I did received help reading   this forum, this is not "THE WAY" you "HAVE TO" follow to solve this   problem, but this is just a way that worked for me, and I think is worth   to be shared :wink:


I was hoping this would work for me as I did have the exact same packages installed, and nothing else has worked. I removed the extra packages, but still no luck.

I can access and use the external devices just fine...I just can't unmount them, so every time I plug them in, it creates a new name. I now have a huge list of folders that used to be the mounted drives.

---

### Post by buzz57 on 2010-08-31
Awesome by removing the package usbmount from Ubuntu 10.04 am now able to copy to from the usb media which i could not before. Thanks a million. Hopefully this will be fixed in next release.

---

### Post by DKemp on 2010-09-09
Thanks Pregiopomo -- I've been trying to figure this out for days and nothing was working until this.

Thanks again!

---

### Post by gavinlamont on 2010-10-18
Thank you Pregiopomo!

I seem to have gotten the conflicting files when I downloaded a "Rescue Remix" program to try and fix another computer which had suffered from my ministrations.

Deleted those files per your recommend and my USBs are all back.

Thanks,
Gavin

---

### Post by JBAT66 on 2010-10-24
I removed "gnome pilot" and also mounted the drive in root, and changed my permissions on the USB drive to my user account. Not sure which one fixed it.

The NTFS permissions were already set for "everyone full control" from windows, but set it with UBUNTU as well.

Thanks for the help.


> **pregiopomo said:**
> I've been having the same problem for a while, and I went for the   solution posted here (modyfing the etc/fstub) then I finally went to   test it with the laptop of a friend that recently installed Ubuntu   10.04, and on his computer everything worked fine.

So I checked out the Synaptic packages he had installed by default, and I   realized that I had some more that probably were creating some   conflicts/problems.

Now it works again!!

Here is what i did:

- start the "synaptic package manager"
- insert "usb" in the quick search
- compare your installed packages with the following list (these are the   one installed by default):
:arrow: 
 usbmuxd
    usbutils
      libusbmuxd1
      libusb-0.1-4
      libusb-1.0-0
      xserver-xorg-video-sisusb
      libmtp8
      usb-creator-gtk
      usb-creator-common
      libmobiledevice0
      libgphoto2-port0
      libgphoto2-2
      media-player-info
      libhpmud0
      hpijs
      hplip
:arrow:
- remove those packages that have been added by you or that may cause   conflicts, in my case I had all the previous ones and I removed the   following that I added months ago messing up with my laptop:

     :arrow: 
usbmount  (yep it sound weird, but now is working properly in my   laptop!)
       pyton usb
       usb creator
       gnome pilot
:arrow:

I hope this example might help some people as I did received help reading   this forum, this is not "THE WAY" you "HAVE TO" follow to solve this   problem, but this is just a way that worked for me, and I think is worth   to be shared :wink:

---

### Post by GoldNugget on 2010-10-31
It worked for me too. This has been driving me crazy for months. I simply removed usbmount and it recognized my usb without unmounting as root and remounting as regular user. Thanks for sharing your simple solution.

---

### Post by Sauli on 2010-12-13
Thanks pregiopomo,

After removing usbmount I finally got the USB writing permission back. 
To FAT partitions at least ...

Unfortunately, I still cann't mount memory sticks formatted in EXT3. I have had the USB problems since upgrading to Ubuntu 10.04 and I may have messed things while trying to fix them. 

In fstab I now have 
/dev/sdb1 /media/usb auto rw,user,auto,exec,async  0 0
does that look suspicious?

Sauli

P.S. I believe my problems were originated from virtualbox USB configuration in fstab and difficulties in getting virtualbox upgraded for Ubuntu 10.04. After trying to fix things I probably made the situation worse. Now I have removed the virtualbox from the system.

---

### Post by allisonmargaret on 2011-03-26
Thanks for the workaround! One year later and the solution still works.

---

### Post by Tom Tiger on 2011-03-26
Worked for me aswell,  I removed pmount, gnomepilot and usbmount  and everything works as normal again :P

Thanks :D

---

### Post by atmjeet on 2011-10-14
The Problem is with "usbmount". While the package name suggests that it essential to mount usb devices automatically which is not true. the default installations has everything required to automount a usb device. this package automatically mounts USB mass storage devices (typically
USB pens) when they are plugged in, and unmounts them when they are
removed. The mountpoints (/media/usb[0-7] by default), filesystem types
to consider, and mount options are configurable. When multiple devices
are plugged in, the first available mountpoint is automatically
selected. If the device provides a model name, a symbolic link
/var/run/usbmount/MODELNAME pointing to the mountpoint is automatically
created.

But the problem lies in copying a file inside the device. it requires root privilege.

My suggestion is to remove this package "usbmount"and you will get back to happy doings with your usb device without any problem.
:)

---

### Post by jvin248 on 2012-03-25
My system had both usbmount and the python-usb but not the others installed. I only removed usbmount and now the flash drive works like it is supposed to.

---

### Post by harun3d on 2012-07-03
I have the same error for unmounting my android gsm which is connected with usb cable.  I have no problem with usb stick.  The link to my gsm in the bookmarks of file explorer stays on.  He also says: ```
unable to unmount 
/sbin/umount.udisks: no device for /media/H: No such device
```  I did all what is mentioned as solution in this thread.  It didn't help.
He shows an unknown character instead of the name of my microsd card in gsm. instead of harun, he says "h..." with a rectangle and  0 0 0 C in this rectangle.  The rectangle is as big as one normal letter. see picture.  
I think this happened after I had made a bootable usb stick.

---

### Post by papibe on 2012-07-03
Hi harun3d.

You will have more luck creating a new thread with your concern. Please do so.

Feel free to link this thread in your new one for reference.

Thread is closed now.

Regards.

---

