---
title: "Crashed HD, Can Ubuntu help?"
date: 2010-01-21
forum: General Help
---

### Post by cephalopod1 on 2010-01-21
Hey all, great forum and I love Ubuntu! On another note I have a serious issue with my PC. My computer recently crashed (running windows xp) and keeps looping to a black screen that gives me the option to run last known working configuration, safe mode, etc. None of these choices if chosen actually work, they simply just send me back to the same screen without loading windows. 
 
The problem with this is I have a ton of photos on this computer I have yet to back up (I know, this is my fault for not backing them up). I downloaded the ubuntu disk, as I had read there was possibly a way to extract the files from my crashed HD using this program. 
 
When I load the disk, Ubuntu comes up flawlessly but will not mount my HD. here is the error message I receive when I try to open my HD:
 
Cannot Mount Volume
 
$Logfile indicates unclean shutdown (0,0) failed to mount '/dev/sdal/': operation not supported mount is denied because NTFS is marked to be in use. Choose one action. Choice 1: if you have Windows then disconnect the external devices by clicking on the safely remove hardware icon in the windows taskbar then shut down windows cleanly. Choice 2: If you dont have windows then you can use the force option for your own responsibility, For example type command line : mount -t ntfs-3g/dev/sdal/media/disk-o force or add the option to relevent row in the /etc/fstab file: /dev/sdal/media/disk ntfs-3g force 0 0.
 
Having limited computer experience, this means nothing to me. Do I need to unplug any USB devices, etc that may be connected to the PC and then try again. I simply want to access the photos on this comp and transfer them off of the HD to a safe place. I will try anything as long as it does not erase my pics. 
 
Thanks to anyone that can help me with this. All input is greatly appreciated. 
 
Kyle

---

### Post by NovaWasp on 2010-01-21
In the live cd.
 
Open a terminal
 
Applications : Accessories : Terminal.
 
1.  Enter the following:
 
sudo mkdir /mnt/windows
 
It means:
sudo - esculate your permissions to root (administrator) for the command
 
mkdir - make directory
 
2.  Enter the following:
 
sudo ntfs-3g -o ro /dev/sda1 /mnt/windows
 
It means:
ntfs-3g - mount with the ntfs-3g driver
-o - with the following options "ro" read only.
 
That should work.  You could also try
 
sudo ntfs-3g -o recover /dev/sda1 /mnt/windows
 
later,

---

### Post by efflandt on 2010-01-21
I had a similar issue with an old laptop that my boss' grandson apparently was not careful enough with.  WinXP refused to boot even in safe mode to protect any data left, and nothing else worked.  From Ubuntu CD gparted refused to do anything with the partition until Windows fixed it, and I could copy little of the user's home directory until it halted with looping read errors (didn't even get as far as My Documents).

When I first put it in USB enclosure it just made constant snicking sounds, like it was having read problems.  WinXP or Ubuntu on another computer recognized the USB enclosure, but could not mount anything.  I was beginning to wonder if the USB enclosure was faulty.

But yesterday (weeks later) I plugged it into my 64-bit Ubuntu 9.10 desktop, and to my surprise it mounted automatically.  So I copied off what I could (one dir was not readable) and burned that to DVD for the user.  Some of the data might be corrupt (some read errors in dmesg), but I got what I could from it.

PS: Didn't have as much luck with a different failing drive.  Fortunately I copied most of what I thought I needed to CD before removing the drive (but overlooked hidden folder with Outlook Express data).  While taking the drive to the store for a replacement, I accidentally dropped it a couple of feet flat onto a hard floor.  There was no longer any hope for that drive (would only make a couple of snicks, then give up quietly).

---

### Post by cephalopod1 on 2010-01-21
Thanks for the iput guys.  I will try your suggestion NovaWasp when I get home tonight.  I will post back to let you know how it goes.  Hopefully this will work.  I just went out and bought a HD enclosure, that may be the next step, but I am hoping ubuntu will get this done before I even have to mess with that.  Thanks again.
 
Kyle

---

### Post by cephalopod1 on 2010-01-21
NovaWasp, I typed in the command and then looked for the Hard drive... it was no longer on the list of drives.  Not sure what happened, but I can no longer see the drive on the list of places.  
 
I simply typed in the command and then typed the exit command to get out.  It did do something b/c I heard the computer make more of a whishing sound after the second command was typed, but this may have simply been the disc spinning in the drive.  Something else I need to do?

---

### Post by NovaWasp on 2010-01-22
The problem is I don't have a bad drive to monkey with right now.  We mounted the drive in /mnt/windows.  Point Nautilus ( the file browser) to /mnt/windows.  It will act like it's just another directory if it's working.   I forgot that bit.  If you've shut the computer down you'll need to recreate your mount directory and re-mount it with the ntfs-3g command.
 
later,

---

