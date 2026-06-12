---
title: "Help Windows User"
date: 2011-02-15
forum: General Help
---

### Post by Beowolf64 on 2011-02-15
Hello everyone.

I have just installed Ubuntu 10.10 on top of Windows. I am totally new to Linux and really need some quick tips to get going.

1) How to connect to Internet? I have DSL modem, user name and password. Everything is working OK in Windows, but now it is time to get it working in Ubuntu.  My ISP gave me CD with Linux driver for my modem. I tried ./configure, but got "access denied" message. This lead to another question.

2) Root account. How to setup root account or maybe I don't need one.

3) How to quickly jump into root folder of C: and D: drivers inside command window.

4) I have big C: drive, but my root dist is only 17Gb. I am going to install lots of application. What if 17 Gb isn't enough?

5) From what I see, all Ubuntu stuff resides inside C:\ubuntu folder. Is there a way to install it separately. Can I split C: drive into to two parts and give 1 part to Ubuntu and the other to Windows. It is OK if Windows and Ubuntu can't see their part of C: drive. There is also D: drive, where I keep my documents. D: drive should be visible from both operating systems.

6) What is the easy way to run Windows apps from inside Ubuntu? I heard something about virtualization, but never done it myself. Any quick tips would be very helpful.

That is all. Thank you very much.

---

### Post by uRock on 2011-02-15
Hello and welcome to the forums.

I can't answer all of your questions but I'll give some of them a try.
> **Beowolf64 said:**
> Hello everyone.

I have just installed Ubuntu 10.10 on top of Windows. I am totally new to Linux and really need some quick tips to get going.

1) How to connect to Internet? I have DSL modem, user name and password. Everything is working OK in Windows, but now it is time to get it working in Ubuntu.  My ISP gave me CD with Linux driver for my modem. I tried ./configure, but got "access denied" message. This lead to another question.Does your system connect wirelessly?
> 2) Root account. How to setup root account or maybe I don't need one.You don't need the root account. Any time you need to run a command just put **sudo**(super user do) in front of the command. Your password will unlock root privileges.
> 3) How to quickly jump into root folder of C: and D: drivers inside command window. Not sure what you mean. All drives should be listed in the Places menu, but their name will not be shown, just Filesystem with the size beside it.
> 4) I have big C: drive, but my root dist is only 17Gb. I am going to install lots of application. What if 17 Gb isn't enough?I have had lots of extra softwares installed and never had more than 10GB in the root partition.
> 5) From what I see, all Ubuntu stuff resides inside C:\ubuntu folder. Is there a way to install it separately. Can I split C: drive into to two parts and give 1 part to Ubuntu and the other to Windows. It is OK if Windows and Ubuntu can't see their part of C: drive. There is also D: drive, where I keep my documents. D: drive should be visible from both operating systems. Yes, you can repartition your system and install Ubuntu to its own partition. Ubuntu will be able to read Windows partitions, but Windows can't read Ubuntu's partitions.
> 6) What is the easy way to run Windows apps from inside Ubuntu? I heard something about virtualization, but never done it myself. Any quick tips would be very helpful. Virtualization is a great way to run Windows applications, but it requires you to have a copy of Windows to install. There is a Program for Linux called Wine that can run some Windows Programs, but I recommend finding the Linux equivalent in the Ubuntu Software Center.

Hope this info finds you well and that it is helpful.

Cheers,
uRock

---

### Post by Beowolf64 on 2011-02-15
Hi uRock. Thanks for your input!

I use DSL with landline phone. No wireless. I try to install modem driver with sudo.

Is there a way to partition C: drive without reinstalling Windows? I prefer to keep Windows around until I get comfortable with Ubuntu. 

My ISP gives me limited traffic quota. I really don't want Ubuntu to download updates without explicit confirmation. How can I make sure that all automatic updates are disabled.

Thank you!

---

### Post by Beowolf64 on 2011-02-15
When I login into Ubuntu, GNOME doesn't start. I get only small terminal window on the upper left corner. Help!

---

### Post by adeee on 2011-02-15
> **Beowolf64 said:**
> When I login into Ubuntu, GNOME doesn't start. I get only small terminal window on the upper left corner. Help!

It just because you change your GUI session to 'Xtreame' .

So when your login screen apear. just hit your username. a bottom panel appear. 
Change sessions ( Xtreame to genome ).
and login.
simple. :P

---

### Post by adeee on 2011-02-15
> **Beowolf64 said:**
> 

Is there a way to partition C: drive without reinstalling Windows? I prefer to keep Windows around until I get comfortable with Ubuntu. 




yes you can migrate ubuntu Wubi to its seprate partition. see this thread. [**migrate wubi install to partition  **]("http://ubuntuforums.org/showthread.php?t=1519354").
it will help you. but i recomend you need to read all this first. and understand what is wrote on there. Google is your good guide. also ubuntu staff available here for your good help.

> 
My ISP gives me limited traffic quota. I really don't want Ubuntu to  download updates without explicit confirmation. How can I make sure that  all automatic updates are disabled.

Thank you!

Yes you can stop automatic updates. see this [https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html](https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html)

also manually here .

System > Administration > Software Preferences > Internet Preferences > unclick check for updates automatically

---

### Post by Beowolf64 on 2011-02-15
Thanks a lot. That was very helpful. But I am still having problems with my modem. It is sagem f@st 800-840. I tried **sudo ./configure**, but all I get are error messages. Is it possible to get this modem working under Ubuntu?

---

### Post by Beowolf64 on 2011-03-05
SOLVED. Trash USB model.

---

