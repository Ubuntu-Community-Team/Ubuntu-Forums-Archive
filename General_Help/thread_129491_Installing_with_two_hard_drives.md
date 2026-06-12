---
title: "Installing with two hard drives"
date: 2006-02-13
forum: General Help
---

### Post by reidms on 2006-02-13
I am installing Kubuntu on my computer.  I have to hard drives.  
Is there anyway to install linux on one and leave my windows on the other?

Does the installer give me a choice of which hard drive I want to install on? :-k 

Thanks for your time! :)

---

### Post by analyticalman on 2006-02-14
Yes - thats the setup I have.  assuming Windows is on the Master hard drive (HDa) then get the installer to install to the second drive (HDb).  It should be straightforward.  THe Boot manager (GRUB) should go on the MBR of HDa and should give you a choice of which operating system to boot into when you switch on

---

### Post by Robgould on 2006-02-14
exactly right.  Just run the install cd for ubutnu and follow the prompts.  When you are done you will be amazed at how simple it is.

---

### Post by reidms on 2006-02-14
So the installer will give me a choice of which hard drive I want to install on?

---

### Post by darknightuk on 2006-02-14
are both drives ide?
personally i would disconnect the xp drive and make the other hd0 first drive on your system and install with only 1 drive attached shud be ez to then to reconnect the drive then add xp info to grub just make sure you don't install grub on your xp drive's mbr!

---

### Post by engla on 2006-02-14
Yes it will give you the choice but it's not neccessarily simple; it could be a problem to figure out which drive is which. The easiest way is probably to check exactly how large the drives are (hopefully they are not identical) and use that to identify them.

---

### Post by Robgould on 2006-02-14
The installer presents you with lots of options to install.  Here are some helpful links.
 
[http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")
 
[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

