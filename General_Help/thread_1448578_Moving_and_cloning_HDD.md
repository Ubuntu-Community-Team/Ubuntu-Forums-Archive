---
title: "Moving and cloning HDD"
date: 2010-04-06
forum: General Help
---

### Post by ShadeS_07 on 2010-04-06
Are the following possible?

1. Moving an HDD where my Linux distro / OS resides, into another machine, 
   probably a similar one.

   So far, I've tried and have done such with Windows XP Professional SP2.
   After moving the HDD to another machine, I did a "repair install" 
   which retained my data and configurations, without reformatting the
   HDD...

2. Cloning an HDD...

   For example, with Ghost, or maybe other utilities that works well
   with a Linux distro / OS... Can I clone my HDD to make a complete
   backup of my system? And, aside from files and configurations, will
   it also retain the updated and upgraded packages? Say I have 
   OpenOffice v3.1.1, and I have upgraded it to v3.2.0; After cloning
   my HDD, will I have the older version or the upgraded version?

Thanks in advance...

~ShadeS_07,, -_+ :popcorn:

---

### Post by ubunterooster on 2010-04-06
answer to 1: usually, can be iffy
answer to 2: [http://www.clonezilla.org](http://www.clonezilla.org) I've used this; it makes an *exact* copy of your drive and is good for backups as well.

---

### Post by colorlessprism on 2010-04-06
[remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") takes your current install and turns it into a live cd. you can even choose "backup" and grab all your personal files as well. choosing the backup option may require you to exclude some large folders like Music for example. once you have the iso either burn it off or use usb startup disc creator and use a flash drive.

---

### Post by ubunterooster on 2010-04-06
Does it include a program for installing itself or is it stuck as a liveCD? 

Edit: It does. I should have looked before asking, sorry.

---

### Post by colorlessprism on 2010-04-06
edit, i should have read you edited portion...

it should have an install icon on your "desktop" and under "System-->Administration" (this is after you have booted into your backup either on disc or on USB) if not, i have had it happed a few times, you can type "install" when you get to the boot menu and will be guided through the installation process. however at the boot menu you should hit enter and test out your backup first.

---

### Post by waynefoutz on 2010-04-06
I've read good things about Mondo Rescue. I'm told that will will even clone multiple partitions. 

[ttp://www.mondorescue.org/]("ttp://www.mondorescue.org/")

Not sure if it's in the 9.10 or later repositories, but it's definitely there in 9.04 and earlier.

---

### Post by ShadeS_07 on 2010-04-07
Thank you for the response.. ^^

Uhmmm, btw, I've already know about Remastersys.. I've been using it to make backup copies of my system, but I also wanted to know if I can make an HDD cloning, aside from using Remastersys..

Thanks again... God bless all... ^^

~ShadeS_07,, -_+ :popcorn:

---

### Post by ubunterooster on 2010-04-07
> **ShadeS_07 said:**
> Thank you for the response.. ^^

Uhmmm, btw, I've already know about Remastersys.. I've been using it to make backup copies of my system, but I also wanted to know if I can make an HDD cloning, aside from using Remastersys..

Thanks again... God bless all... ^^

~ShadeS_07,, -_+ :popcorn:

> **ubunterooster said:**
> answer to 1: usually, can be iffy
answer to 2: [http://www.clonezilla.org](http://www.clonezilla.org) I've used this; it makes an *exact* copy of your drive and is good for backups as well.
This?

---

### Post by ShadeS_07 on 2010-04-07
Yes, and I'll also try what waynefoutz has suggested, Mondorescue... Hehehe... :popcorn:

---

