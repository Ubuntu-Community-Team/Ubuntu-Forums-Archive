---
title: "Help Needed"
date: 2011-07-31
forum: General Help
---

### Post by Hrishikesh Utpat on 2011-07-31
Hey,
Want to install Ubuntu on my machine. Already have installed Windows 7 on it. Want to run both side-by-side. My HD has a 140 GB partition in Windows, that doesn't contain the windows installer.
What partitions do I need? And how do I install Ubuntu? 

Thanks!

---

### Post by mikewhatever on 2011-07-31
Check out [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download).
See the 'Show me how' buttons?

---

### Post by Quarkrad on 2011-07-31
To give Ubuntu a try dual booting on your PC I would first of all use Windows to create an extra partition on your HD.  Give it a name/label such as **Ubuntu**, make it NTFS and say 50 GB.  After this put the Ubuntu CD into your cd rom and restart your pc.  This will install ubuntu in your RAM and give you the choice of testing/using ubuntu or installing on your HD.  I would do some research before you do this to get familiar with the install process but essentially when you get to the install ubuntu on your pc stage you will get a number of options.  The important one is when it  comes to where to install ubuntu, using the whole disk (no -this will wipe out your windows install), next to your current OS (no - this can cause problems) or do a **manual** install.  Choose the **manual** method and follow the screen prompts.  Basically you will see a number of partitions to choose where to install ubuntu, you will choose the ntfs partition you created using windows called **Ubuntu**. Reformat it using the ext4 system and choose / as your mount point.  This will then install ubuntu and give you a text based screen to dual boot either windows or ubuntu.  If you mess up don't worry - as long as you choose the **Ubuntu** partition to 'play' on.  I did it first time with no problems and I'm a newbie.   Once it is set up come back to the forum and you will find out what else to do including getting a nice graphical boot screen.  50GB is probably too large but if you like Ubuntu and decide to keep it then you need to really think about the partition sizes and for windows and ubuntu and resize your whole machine.

---

