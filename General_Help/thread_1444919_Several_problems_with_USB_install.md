---
title: "Several problems with USB install"
date: 2010-04-01
forum: General Help
---

### Post by Speedcuber on 2010-04-01
Hi,

I recently tried setting up Xubuntu, and later Ubuntu, on a flash drive using the instructions and procedures from [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

In both cases, I experienced the same two problems. I apologize if this is a stupid question, but I would really appreciate help on this as Linux looks great for me if I can get it working.


When I first booted up Xubuntu from my USB drive, it seemed to work fine. However, when I tried to set up the network so I could have access to the internet, I encountered problems. According to the documentation, clicking on the network symbol should provide options for "Wireless Networks"; when I clicked on the icon, none such option was available. I looked through all of the options that presented themselves from either left or right clicking the icon but was unable to find any way to connect to my network which works fine in Windows.

Secondly, after rebooting my computer and trying to boot Xubuntu for the second time, it did not work so fine. The screen seemed to freeze on "Starting init crypto disks" and eventually went blank. When I restarted the computer and tried again, I encountered the same problem.

I then returned to Windows and cleared the USB drive and started again. I met *identical* circumstances as the ones above. I then tried Ubuntu; I was unable to even boot this the first time--it just became frozen and never worked. I then tried for the third time with Xubuntu with, again, identical results.

I am using a Dell XPS laptop with Windows Vista Ultimate and a 4GB USB drive.

Does anyone have any ideas about what is going on?

Thank you for considering my problems.

---

### Post by Speedcuber on 2010-04-02
After thinking about it some more, I had another idea.

Would it be possible to install Ubuntu/Xubuntu to a CD, and boot from the CD, but then configure it so that all my settings/etc. would be saved onto a flash drive automatically? It would require using and transporting both objects, but I am willing to do that. Any ideas?

Thank you!

---

### Post by Mighty_Joe on 2010-04-02
Can you boot and use the Live CD?
Have you tried the [Live USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator") on the Live CD?  It's much easier than doing it by hand.
Have you googled for your particular hardware to see if there are outstanding issues?
It is possible to use the Live CD and save changes on another drive:  [see here]("https://help.ubuntu.com/community/LiveCD/Persistence").
I've had good results doing a full install on a USB drive.  It's faster than the Live USB/CD method, but it takes more space.  See my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680&highlight=partition+table") for the procedure I used.

---

### Post by C.S.Cameron on 2010-04-02
You should be able to boot Live CD and save to USB if you make a ext3 partition on the USB and name it casper-rw.
When booting the CD you need to press F6 then type (space)persistent.
This has worked for me with earlier versions, not sure about the current version.
It's probably easier getting the persistentsb to work using usb-creator.
Make sure you check the MD5SUM of the iso.

---

