---
title: "mounting android - unable to see deeper than one level."
date: 2011-11-13
forum: General Help
---

### Post by zeefreak on 2011-11-13
having a somewhat bizarre problem that i hope the knowledgeable folks here might be able to help with.

i tried to load some new music on my phone this morning, but i'm unable to see anything under the top level of the phone. e.g. i have all the directories under my phone, but all of them are reporting as empty through ubuntu. checking the filesystem on the phone, i see the content i expect.

on phone i have:
/sdcard/media/ringtones
/sdcard/media/music
/sdcard/media/alarms

on ubuntu i have:
SAMSUNG_Android/media/<empty directory>

i can create a new directory under media, say 'temp' and i see it on my phone. unmount, remount, temp is invisible to ubuntu.

checking dmesg i am seeing the following error:

[  313.767405] usb 2-1.3: new high speed USB device number 7 using ehci_hcd
[  314.099858] iwlagn 0000:02:00.0: Aggregation not enabled for tid 6 because load = 6
[  315.324946] usb 2-1.3: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -71

i'm not sure if it shoudl be mounted as a gphoto2 fs or not. it used to work, and when it did i wasn't paying attention to how it was mounted.

i think, but i'm not certain that this problem has arisen as of the latest kernel update 3.0.0-12. i'm running ubuntu 11.10. the problem is consistent across both 64bit and 32bit. i am sad to say that mounting on a windows box i'm able to see all the directories as that seems to put the problem firmly with ubuntu.

---

### Post by zeefreak on 2011-11-14
wow 71 views and 0 replies. that doesn't happen often on here. anyone?

---

### Post by hoover67 on 2012-07-31
Just got a brand new Galaxy S3 and can only add a "me too" so far. I can see the dirs one level deep, but am unable to access any folders and get an error "-60" when plugging in the device on ubuntu 12.04 (unity 2d).

---

### Post by Atilliar on 2012-09-13
Me too... I also get error -60 and the same results as everyone else.

---

### Post by vukm on 2012-12-19
I also had problems copying stuff to my phone and noticed it was mounted as gphoto2 filesystem. I installed the gphoto2 (sudo apt-get install gphoto2) package and now it works :)

---

### Post by cwsnyder on 2012-12-19
Hey, guys, the new kernel was changed to reflect the changes coming in the Android operating system.  The 'new' way of mounting Android devices is to mount as MTPfs, no longer mounting your device as a block memory device.

---

### Post by rosswmcgee on 2012-12-25
Hi! As a new Galaxy S3 owner I get the same error as mentioned in this thread. My old 

Blackberry 9800 did not have this problem. Thinking that android and ubuntu were some

how more compatable was an error on my part. So I am asked to mount using Rhythmbox.

So how would I use your method of mounting? re/MTPfs

---

### Post by rosswmcgee on 2012-12-25
I have the same problem as above the 60 error plus I am asked to use Rhythmn box.

So how do you mount as MTPfs as you suggest?

---

### Post by IanW on 2012-12-25
This works for me:- [How To Properly Mount Android 4.0+ Devices In Ubuntu Using Go-mtpfs]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html")

---

