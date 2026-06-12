---
title: "Ubunty is very slow"
date: 2006-02-13
forum: General Help
---

### Post by bafi on 2006-02-13
We have 5 lab with 20 computers each. I was asked to find Linux System we can use in on of the lab. I found out that Ubuntu is very nice easy desktop system, but but but it is almost not possible to run on lab computers. We will need go back to the Microsoft. We had before Windows NT worsktation 4.0 on those computers and it was working well. Ubuntu is to slaw and it need more hardware than Windows. Is it possibility to make Ubuntu faster.
All computers are:
Penntium II 300Mhz and 128MB RAM.
I thought that Linuz can be good alternative for Windows but it seems it is oposit.
Any suggestion??? Any other distrubution which can be used on good but older computers? What advantage we can have from Linux if it need better computers than Windows. Free System but you have to pay more for hardware?

Marcus

---

### Post by kaamos on 2006-02-13
Gnome is too heavy for that setup. Perhaps xubuntu (ubuntu server install + xubuntu-desktop) because it has a lighter window manager (xfce).

Damn small linux could be a good choice as well.

---

### Post by drfalkor on 2006-02-13
To small cpu, and not so much ram you guys have there. Go for DSL ( Damn small linux), it will run very well on that hardware :D

---

### Post by Didjit on 2006-02-13
As mentioned above XFCE (it was designed for speed and to be light) or don't run a windows manager at all. This depends on what you are doing. If you are just running server processes, apache, sendmail, ftp server etc, there really is not a need to always have the WM running.

Didjit

---

### Post by pato101 on 2006-02-13
[QUOTE=bafi]
All computers are:
Penntium II 300Mhz and 128MB RAM.
I thought that Linuz can be good alternative for Windows but it seems it is oposit.
[/QUOTE]

Please compare apples to apples... try install WinXP there and then compare to ubuntu.

Nevertheless, the xfce option stated by previous repliers should work pretty well on that hardware (until firefox is started, at least). 

Using a very old distro (e.g. RedHat 7.3) might certainly speed up things but you would loose too much features as well.

---

### Post by bafi on 2006-02-13
We tested Windows XP on the same configuration and Windows was slightly faster


Marcus

[QUOTE=pato101]Please compare apples to apples... try install WinXP there and then compare to ubuntu.

Nevertheless, the xfce option stated by previous repliers should work pretty well on that hardware (until firefox is started, at least). 

Using a very old distro (e.g. RedHat 7.3) might certainly speed up things but you would loose too much features as well.[/QUOTE]

---

### Post by frodon on 2006-02-13
you could also just replace metacity (the default gnome window manager) by xfwm4 (the xfce window manager) : [http://www.ubuntuforums.org/showthread.php?t=102875](http://www.ubuntuforums.org/showthread.php?t=102875)

---

### Post by bafi on 2006-02-13
We need linux as a desktop replacement. Thus we need all office software , browser etc.. If ubundu is faster we will use it but is to slow for old hardware.

As a server we use Slackware and as a firewall we use SentryFirewall.

Marcus
[QUOTE=bafi]We tested Windows XP on the same configuration and Windows was slightly faster


Marcus[/QUOTE]

---

### Post by dcstar on 2006-02-13
[QUOTE=bafi]We have 5 lab with 20 computers each. I was asked to find Linux System we can use in on of the lab. I found out that Ubuntu is very nice easy desktop system, but but but it is almost not possible to run on lab computers. We will need go back to the Microsoft. We had before Windows NT worsktation 4.0 on those computers and it was working well. Ubuntu is to slaw and it need more hardware than Windows. Is it possibility to make Ubuntu faster.
.......[/QUOTE]
There are many HOWTOs on making Ubuntu faster in this forum:

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

As an example, someone just posted one on faster Network file transfers:

[http://ubuntuforums.org/showthread.php?t=128873](http://ubuntuforums.org/showthread.php?t=128873)

You can do a forum search to see if any might apply to your old hardware.

---

### Post by Lord Illidan on 2006-02-13
[quote=bafi]We need linux as a desktop replacement. Thus we need all office software , browser etc.. If ubundu is faster we will use it but is to slow for old hardware.

As a server we use Slackware and as a firewall we use SentryFirewall.

Marcus[/quote]

You need XFCE then..

Also, consider Zenwalk Linux  [www.zenwalk.org](www.zenwalk.org) .. I used it and was impressed with its speed. Had issues with Nvidia drivers, but it doesn't seem that you will need them!

Now, allow me to pick apart your first post :

> We have 5 lab with 20 computers each. I was asked to find Linux System we can use in on of the lab. I found out that Ubuntu is very nice easy desktop system, but but but it is almost not possible to run on lab computers. We will need go back to the Microsoft. We had before Windows NT worsktation 4.0 on those computers and it was working well. Ubuntu is to slaw and it need more hardware than Windows. Is it possibility to make Ubuntu faster.
All computers are:
Penntium II 300Mhz and 128MB RAM.
I thought that Linuz can be good alternative for Windows but it seems it is oposit.
Any suggestion??? Any other distrubution which can be used on good but older computers? What advantage we can have from Linux if it need better computers than Windows. Free System but you have to pay more for hardware?

Ubuntu is just ONE distribution out of hundreds. Just because one distro doesn't work for you doesn't mean that all Linux doesn't work! Just because you may not like a particular brand of Ford doesn't mean that Ford sucks, doesn't it.

Linux is an OS which can run on all hardware, from wristwatches (try xp on that) to supercomputers!
And as regards speed : Have you enabled dma?

---

### Post by carlosqueso on 2006-02-13
If you do want to use it....use Carlosqueso's crap computer special.

Do a server install, and then install gdm, icewm, icepref, menu, abiword, epiphany-browser, and gnumeric.  It worked pretty well with my 500Mhz pIII with 64MB RAM, but I then upgraded the RAM and switched to xfce.  If you have any questions about the setup...let me know and I'll try to help

---

### Post by rsmereka on 2006-02-14
Strange is'nt it,

I started reading through the posts in the server forum looking for a good ftp server for stock breezy and I stumbled upon this post and I could not let it go without giving my two cents.

I have been around the Linux world for quite some time and one of my objectives is getting Linux to run on minimal hardware. Small amount of RAM, small hard drive and processor.

One of my experiments which was a disaster was to load stock breezy on a PII-350 64MB RAM machine with 4GB HDD. Part of the reason I did this was that Ubuntu's own doc's (FAQ etc) talk about 32MB RAM and up. Actually I have seen different values from 32MB to 128MB. Another experiment which is still in progress is stock breezy on a PIII-1GHZ 128MB RAM 30GB HDD. This seems more realistic but you know what. It's still slow. It's like there is something weighing it down. So I disabled GDM so I could mess around with the command line and the conclusion I came to is that Gnome is huge and is the main reason why stock Ubuntu is so slow on older hardware.

My main work machine is a PIII-1GHZ dual 512MB RAM SCSI running Gentoo and xfce and it is very fast. I am looking around for a desktop replacement for Gentoo. There are some things that I do not like about it. As it stands now, the fact that Gnome on breezy is so huge is going to be a factor.

BTW, the fastest free OS on older hardware is FreeBSD (imho). Especially networking. I have it running on that PII-350 (64MB RAM) I previously spoke of and its amazing. Keep in mind that its a server (no GUI).

The most amazing Linux story I have to share on older hardware is a production machine that I set up and is still in use supplying http and ftp Internet services on a PI-166 80MB RAM 4GB HDD running Libranet 2.8.1 (no GUI). Now Libranet, like Ubuntu is based on Debian so I know that Debian can run quickly with minimual hardware.

Cheers,
rick

---

### Post by noalternative on 2006-02-17
I personally prefer for old computers, [feather]("http://featherlinux.berlios.de/") over dsl.  It  is more full featured in many respects.  If ubuntu would start running the xubutu desktop on [kdrive's Tiny X]("http://www.google.com/search?q=kdrive+tiny+x&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official"), it would probably work as well on my computer as feather or dsl does.

I don't think either would be appropriate for a computer lab, because you can't add users easily.  They're both knoppix remasters.  So yeah I would tell this poster to go with xubuntu-desktop.  I hope the improve the speed in dapper.

---

