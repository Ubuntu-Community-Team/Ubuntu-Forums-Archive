---
title: "Unable to mount digital camera"
date: 2009-11-06
forum: General Help
---

### Post by protoguy on 2009-11-06
After I installed 9.10, I cannot get anything to work except Firefox. I will start with my digital camera. It worked fine in Jaunty. now F-stop gives me this message when I plug in the camera:
Unable to mount Kodak EasyShare Z612 Zoom Digital Camera

Error initializing camera: -60: Could not lock the device

So now what?

---

### Post by Nick Brohman on 2009-11-06
I've had the same message with a Canon Powershot A470.

I closed the message & used the Import button. It seems to do this action randomly & as Import works, I'm ignoring the message.

---

### Post by bertmanphx on 2009-11-06
Hello,
I had this issue as wlel, with a camera, USB thumbdrive, and a Sansa Clip.  Use the Disk Manager from the programs list, you can mount it from there.

bertmanphx

---

### Post by protoguy on 2009-11-06
Nope.  It found the pictures, but when I told it to transfer. It said error transferring file.

---

### Post by khelben1979 on 2009-11-06
> **protoguy said:**
> Nope.  It found the pictures, but when I told it to transfer. It said error transferring file.

I've had this experience with an old Nikon digital camera myself and I managed to solve it by having the digital camera to be switched in another mode where it normally would show the pictures in the camera other than having the camera activated as photo capture. You can try this.

---

### Post by bford16 on 2009-11-15
> **protoguy said:**
> After I installed 9.10, I cannot get anything to work except Firefox. I will start with my digital camera. It worked fine in Jaunty. now F-stop gives me this message when I plug in the camera:
Unable to mount Kodak EasyShare Z612 Zoom Digital Camera

Error initializing camera: -60: Could not lock the device

So now what?
Same problem here. But it isn't f-spot.  The error occurs without f-spot installed at all! This error is caused by the process which mounts the camera's filesystem(s).

---

### Post by Nick Brohman on 2009-11-24
What I have found is that I get the 'unable to mount' message with F-Spot running.

i don't get the message when I connect the camera with no F-Spot running.

I now shut down F-Spot before importing photos. or use the import button after closing that message.

---

### Post by moe46 on 2010-01-07
Hi
I had this same issue.
Normally one turns a camera on then plugs it in, this gave me the -60 error.
I found if I just left the camera plugged in, turned it off and then back on
it would then mount normally and I was able to remove the photos.

My camera was Nikon Coolpix s220.

---

### Post by Cotopaxi on 2010-01-08
prootoguy,

your camera is listed as supported by gphoto2, see the following link:

[http://www.gphoto.org/proj/libgphoto2/support.php]("http://www.gphoto.org/proj/libgphoto2/support.php")

You can download gphoto2 from the repositories.

Gphoto2 is only a command-line tool, if you download "digikam" (kubuntu) or "gtkam" (ubuntu), you have an application with a graphical user interface.

Both applications are based on "gphoto2"

Good luck!

---

### Post by Cotopaxi on 2010-01-08
Guys, this one is amazing!

My &#8220;Kodak M340&#8221; is not listed in the &#8220;gphoto2&#8221; list of supported cameras, but I switched the camera ON and in PHOTO SHOOTING MODE, connected it afterwards to the computer and it was recognized immediately by &#8220;digikam&#8221;.

The &#8220;gphoto2&#8221; web-page says that &#8220;Kodak Easy Share&#8221; models are all supported by &#8220;gphoto2&#8221;

My system is Kubuntu 9.10

Good luck

---

### Post by gazdevil on 2010-06-21
Hi everyone,

I'm having problem on monting my Kodak M1063 EasyShare since the new 10.04.

I have parsed a lot of threads and no one talk about my problem.

When i connect my camera via USB, nothing happen anymore. Before it was automatically mounted, twice like several of you guys but it worked. Now I can see it with lsusb : 
```

$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f9:01d6 Brother Industries, Ltd MFC-260C
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 040a:059b Kodak Co. Digital Camera
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

But i don't see it anymore with blkid :
```

$ sudo blkid
/dev/sda1: LABEL="winshare" UUID="5BB3-01F7" TYPE="vfat" 
/dev/sdb1: UUID="e4a23785-8f05-d68d-0045-6118325c9972" TYPE="linux_raid_member" 
/dev/sdb3: UUID="0a85c909-cc11-95f1-befc-dd5695edef99" TYPE="linux_raid_member" 
/dev/sdb4: UUID="5fc9e2b6-67cb-84cf-b13b-12af30ee0dd1" TYPE="linux_raid_member" 
/dev/sdc1: UUID="e4a23785-8f05-d68d-0045-6118325c9972" TYPE="linux_raid_member" 
/dev/sdc3: UUID="0a85c909-cc11-95f1-befc-dd5695edef99" TYPE="linux_raid_member" 
/dev/sdc4: UUID="5fc9e2b6-67cb-84cf-b13b-12af30ee0dd1" TYPE="linux_raid_member" 
/dev/sdd1: UUID="2494A30B94A2DE94" TYPE="ntfs" 
/dev/sdd5: UUID="6c678457-ee3c-4aa4-b8a8-69bd43547e1e" TYPE="ext4" 
/dev/md1: UUID="MfOEDB-xuGF-ehkA-Xkl3-TCAn-ssct-t3EePl" TYPE="LVM2_member" 
/dev/md1p1: UUID="659a2a4b-7fff-47a8-a684-ae381d1a43e9" TYPE="ext4" 
/dev/md2: UUID="ZeZjrK-5VnE-rXaA-D2Wj-WWAV-yRav-NgPOu0" TYPE="LVM2_member" 
/dev/md2p1: UUID="4b504b96-0bd9-46ea-a092-2bb6af7f3b26" TYPE="ext4" 
/dev/md0: UUID="02TyjX-xldP-TW1L-cebo-FE4L-6SM0-21qS2s" TYPE="LVM2_member" 
/dev/md0p1: UUID="23d4d451-24e7-4b80-b07b-9c71438c83b6" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="0ed06849-462c-4712-b1ae-d3e2d55df33e" TYPE="swap" 
/dev/mapper/cryptswap2: UUID="6221fdf8-e38f-4d9b-b7df-c27de069e6e2" TYPE="swap" 

```

Usually it appears at the last line

I used blkid to find the /dev dir and then use 
```

$ sudo mount /dev/'dir' /media/mount_point

```

So Digikam, gphoto2 and all other software dont mount my camera but they all see it (like me with lsusb)

What can i type to find out what's going on on this machine ??

Long time ago, i used /etc/udev/rules and add a rule for a USB device (with the ID:Vendor found with lsusb) but since the ubuntu 10.04, it doesn't work same way. Can anyone help me ?

Thanks guys!

---

### Post by Cotopaxi on 2010-06-22
Gazdevil,

Eventually I am repeating something that I mentioned earlier:

Switch the camera on BEFORE connecting it to the USB port.

If you connect the switched OFF camera to the USB port, the camera will go into BATTERY CHARGING MODE.

Just put your camera into photo shooting mode and afterwards connect it to the USB port.

Good Luck.

---

