---
title: "Unable to log in to Windows 7 after installing 11.10"
date: 2012-01-05
forum: General Help
---

### Post by meetdilip on 2012-01-05
Installed Ubuntu 64 bit from CD using " alongside Windows " option over  already installed Windows 7 Ultimate 64 bit. Ubuntu is in sda5 where as  Windows is in sda 3. During startup it shows an option called " Windows  loader sda3 " something. But when I choose that option, it says cannot  read from disc or similar and shows option to use ctrl + alt + del and I  use that to get into Ubuntu 11.10. 


Any help will be appreciated. Thanks :)

---

### Post by Mark Phelps on 2012-01-05
> **meetdilip said:**
> Installed Ubuntu 64 bit from CD using " alongside Windows " option over  already installed Windows 7 Ultimate 64 bit. ..

Bad idea; really Bad idea -- as doing it that way, as you have learned the hard way, risks corrupting the Win7 OS partition because you allowed the Ubuntu installer to resize that partition.

When you were able to use Win7, you could have made a FREE Win7 Repair CD using the Backup feature, but now, you will have to PAY for that priviledge.  You can go to the link below, download the proper Win7 Repair CD image, burn that to CD, and run Startup Repair three times (that's right, three times!):

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Or ... if you want to try a FREE approach (which often works), then read through the link below about using Boot-Repair:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by meetdilip on 2012-01-05
Thanks a lot Mark. I will try the first link (will try to learn from second), but can an MBR repair work in this case ? I have a Windows Repair Disc made of Wondershare Live Boot 2012 which can repair non bootable conditions. Will it damage the Ubuntu installation ? I have EasyBCD too, if Ubuntu damages, can I get it back using it ? 

I started an help thread and doubt thread on installation. I got a link on how to dual boot which I read and when I faced issue in installing, I had to start another thread which had some cold response (not blaming anyone). So I Googled and used the first guide on how to install Ubuntu 11.10 and followed the steps as mentioned in it. Will share the link here. 

Thanks again. :)

---

