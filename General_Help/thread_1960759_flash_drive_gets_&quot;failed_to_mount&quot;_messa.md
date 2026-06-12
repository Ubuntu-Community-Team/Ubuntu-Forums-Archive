---
title: "flash drive gets &quot;failed to mount&quot; message"
date: 2012-04-18
forum: General Help
---

### Post by pretty_whistle on 2012-04-18
This is on Ubuntu 11.04.

Here's the error message:

[IMG]http://i44.tinypic.com/29nt7pz.png[/IMG]

This error started because I didn't "safely remove drive" before removing it.  I just yanked it out.

Is there a way to fix this?

Thanx.

---

### Post by ewz on 2012-04-18
Hello, 
Have you tryed to mount the flash drive on another computer ? 

It looks like you may have pulled it out before it finished writing data,
and the file system is a bit corupted 

you could do a check the filesystem using the Disk Utility application to see if the file system is bad 

I've added a screen of the application.



Hope this helps

---

### Post by pretty_whistle on 2012-04-18
> **ewz said:**
> Hello, 
Have you tryed to mount the flash drive on another computer ? 

It looks like you may have pulled it out before it finished writing data,
and the file system is a bit corupted 

you could do a check the filesystem using the Disk Utility application to see if the file system is bad 

I've added a screen of the application.



Hope this helps

I dont have another PC to try it on.

I checked the filesystem using disk utility as you mentioned but it says it's ok.

---

### Post by ewz on 2012-04-18
Hello, 
hmmm I had this or similar error quite sometime ago and it was the USB Drive was that was corupted. 

hmmm.. maybe you can mount the drive manually, eg: make a folder in your home directory call it mount then in the terminal type: **sudo mount /dev/sdb1 /home/your_name/mount**
My usb drive is sdb1 but yours maybe different,  disk utility will tell you what it is.

If this works I would copy the contents of your usb drive to a backup folder and then reformat the usb drive.

another way could be, use the Ubuntu CD, boot up into a live session and see if you can mount it in the live session.

hope this helps.

---

### Post by pretty_whistle on 2012-04-18
> **ewz said:**
> Hello, 
hmmm I had this or similar error quite sometime ago and it was the USB Drive was that was corupted. 

hmmm.. maybe you can mount the drive manually, eg: make a folder in your home directory call it mount then in the terminal type: **sudo mount /dev/sdb1 /home/your_name/mount**
My usb drive is sdb1 but yours maybe different,  disk utility will tell you what it is.

If this works I would copy the contents of your usb drive to a backup folder and then reformat the usb drive.

another way could be, use the Ubuntu CD, boot up into a live session and see if you can mount it in the live session.

hope this helps.

I tried the things you mentioned but they failed.  I still get the same error message.

---

### Post by pretty_whistle on 2012-04-18
Update:


I solved it.  Here's how-

I used a boot CD from a disk imaging program that's for Windows Vista.  It has a file browser and various utilities on it.  I opened the flash drive and copied the folders/files to another flash drive and then I formatted it.

Done.

---

### Post by ewz on 2012-04-19
Happydays :)
I'm glad you were able to fix it :)

---

