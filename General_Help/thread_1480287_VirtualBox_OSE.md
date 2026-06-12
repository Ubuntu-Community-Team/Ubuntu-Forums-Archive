---
title: "VirtualBox OSE"
date: 2010-05-11
forum: General Help
---

### Post by Dustdj20 on 2010-05-11
Can anyone tell me how to set up Windows XP on VirtualBox OSE?  

Thanks

---

### Post by thirdgen88 on 2010-05-11
You'll need a Windows XP Installation Disc (or Image), then it is as simple as launching VirtualBox, click New to create a new virtual machine, and follow the prompts.  It will take your through naming the virtual machine (and picking the target guest OS), creating the disk image that will house the virtual machine, and then, after starting the image, helping you to link up to your Windows XP Installation disc/image.

From there, it will install as it would on any other computer.  Once finished, go to the Devices menu of VirtualBox and select "Install Guest Additions" to enable better control and integration.

---

### Post by snowpine on 2010-05-11
It is just like installing Windows on a "real" computer. Make sure your virtual machine is set up to "see" your CD-ROM drive, then insert your Windows XP Install CD, follow the directions on screen, type your activation code when prompted, etc.

I'd suggest reading the VirtualBox manual and FAQ:
[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

---

### Post by QIII on 2010-05-11
First, I would use the PEUL version instead of the OSE so that you get USB support.

Check here for how to install it.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Rather than trying to give you instructions via the forum and a lot of back and forth, give the following a read first.  Read the section on configuring virtual machines.  Then, if you have further questions, come back and we will help you out.  I know that manuals are sometimes as hard as the application to figure out!  You will certainly have questions, and we are definitely willing to help.  We won't let you flounder.

[http://dlc.sun.com.edgesuite.net/virtualbox/3.1.8/UserManual.pdf](http://dlc.sun.com.edgesuite.net/virtualbox/3.1.8/UserManual.pdf)

It is not so difficult to set up, but a little bit of understanding of the tools will help you ask more direct questions so we can give you more helpful answers.

---

