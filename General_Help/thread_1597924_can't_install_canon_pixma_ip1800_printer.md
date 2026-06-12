---
title: "can't install canon pixma ip1800 printer"
date: 2010-10-15
forum: General Help
---

### Post by binobooks on 2010-10-15
There is not a driver for the Canon Pixma ip1800 Printer in Ubuntu.  How do I go about getting this printer to work with Ubuntu 10.10.

Thanks, Michael

---

### Post by bobaloochi on 2010-11-02
Bump as I have the same problem.

---

### Post by ezsit on 2010-11-02
Canon printers are known to be troublesome in Linux because of lack of drivers from Canon. Canon is not a very Linux friendly manufacturer. HP and Brother are far better supported. You can try a commercial product called TurboPrint [http://www.turboprint.info/](http://www.turboprint.info/)

---

### Post by bigred1 on 2010-11-11
Same for me; and I managed to get the printer working on an earlier version of Ubuntu, following some instructions I found through the Ubuntu forums.

---

### Post by jontheid on 2010-12-01
Here's the solution:

[http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900](http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900)

If you do as the page says, it works with Maverick 10.10, with all updates up to now.

Good luck

Jon

---

### Post by Simeo on 2011-01-29
It doesn't work....I'm trying to get it to work with my friends Ubuntu 10.10 x86 and it's just...not...working. No response, no message...nothing. Help? I've spent the past several hours trying to get this stupid printer to work. It's the only printer I've had issue with Ubuntu.

---

### Post by ScaroDj on 2011-03-09
I just wanted to say thanks to ezsit for his tip about TurboPrint, that solves my problems for a while.

Although, ideally, Cannon should provide proper drivers for their printers, as I was stupid enough to buy one without knowing they didn't support Linux, this is a good example of my theory: "not everything has to be free in Linux".

---

### Post by empitt on 2011-03-11
Script to install the drivers Canon iP1800: [http://www.linuxone.pl/download/canon_ip1800_deb.tar.gz](http://www.linuxone.pl/download/canon_ip1800_deb.tar.gz)

---

### Post by calchal on 2011-04-12
Hi all, ):P

thanks for all the links, at last I can use my printer :D

---

### Post by HaRabAS on 2011-04-12
i wish this links would help me out on my Canon Pixma IX4000 and Brother DCP-130C too!!

---

### Post by poodoopealeoaph on 2011-04-12
Sadly, I wish there was a way for my pixma ip2700 to work in ubuntu also but I'm not sure there is very much hope there... I think if I ever want to get a printer again, though I probably wont, I would get an HP like someone mentioned earlier. My dad's 7 year old hp printer worked the second I plugged it in and I instantly knew that cannon was a crap company.... WHY DO COMPANIES HAVE TO HATE ON OPEN SOURCE?!?!?!

---

### Post by dOvi on 2011-04-12
> **poodoopealeoaph said:**
> Sadly, I wish there was a way for my pixma ip2700 to work in ubuntu also but I'm not sure there is very much hope there... I think if I ever want to get a printer again, though I probably wont, I would get an HP like someone mentioned earlier. My dad's 7 year old hp printer worked the second I plugged it in and I instantly knew that cannon was a crap company.... WHY DO COMPANIES HAVE TO HATE ON OPEN SOURCE?!?!?!
Well, maybe they don't care about the users, as they might allegate, but care just for the money???

---

### Post by walt.smith1960 on 2011-04-13
> **poodoopealeoaph said:**
> Sadly, I wish there was a way for my pixma ip2700 to work in ubuntu also but I'm not sure there is very much hope there... I think if I ever want to get a printer again, though I probably wont, I would get an HP like someone mentioned earlier. My dad's 7 year old hp printer worked the second I plugged it in and I instantly knew that cannon was a crap company.... WHY DO COMPANIES HAVE TO HATE ON OPEN SOURCE?!?!?!

I don't know that it's hate....more like "it'll cost me more to support Linux users than I'll make back in sales".  I have been known to write to the CEO of companies that don't support Linux and say something like " I really liked the look of your product but your product wouldn't work with my computer.  Your competitor's product will work on my computer so I gave my money to your competitor instead."  THAT they understand.  

Re getting your Pixma installed, have you checked Canon's Australian or Asian sites? Some times they have Linux software that is nowhere to be found on North American sites.

Edit:  Like here:  [http://support-sg.canon-asia.com/contents/SG/EN/0100272002.html](http://support-sg.canon-asia.com/contents/SG/EN/0100272002.html)

---

### Post by lupas on 2011-04-30
Any help for the New Ubuntu 11.04 for IP1800 ????

---

### Post by empitt on 2011-05-05
> **lupas said:**
> Any help for the New Ubuntu 11.04 for IP1800 ????

[http://ubuntuforums.org/showpost.php?p=10548102&postcount=8](http://ubuntuforums.org/showpost.php?p=10548102&postcount=8)

---

### Post by empitt on 2011-05-07
Simplified to installing the drivers Canon iP1800 for all Ubuntu:
```
cd /tmp && wget http://www.linuxone.pl/download/canon_ip1800_deb.tar.gz && tar xzf canon_ip1800_deb.tar.gz && sudo canon_ip1800_deb/install.sh
```

---

### Post by sidfadnis on 2011-06-02
This link provides the required driver and steps to make Canon iP1800 work like a charm with Ubuntu 11.04

[http://www.znupii.ro/how-to-canon-pixma-ip1800-si-ip1900.html:guitar:](http://www.znupii.ro/how-to-canon-pixma-ip1800-si-ip1900.html:guitar:)

---

### Post by krumpy on 2011-06-02
One more link.  This is the one I used to get mine working.

[http://ubuconf.buron.eu/2011/04/canon-mp640-on-ubuntu.html](http://ubuconf.buron.eu/2011/04/canon-mp640-on-ubuntu.html)

---

### Post by docklc on 2011-06-10
> **lupas said:**
> Any help for the New Ubuntu 11.04 for IP1800 ????


I have probably put in 40 hours trying to get my ip1800 to work under Ub HH trough NN11.04 following multiple URLs by others--Spain, Australia, Europe, etc (Interesting that NO Americans seem to have the incentive to come up with a solution).  

I have an AMD 5600x2 system.  My Canon scanner, an N670U worked immediately.  If the Linux folks want us all to buy Windows 7, this is the way to do it--don't provide any basic drivers for older Canon printers.  I have three great Canon printers: an i550, an ip1700 and an ip1800.  NONE will work on my AMD64/Ubuntu system.  ALL will work on my older, slower WinXP system.  

Canon has released drivers for Linux in rpm.  But, apparently no one in the Open Source community has the time or interest in making/updating these Canon drivers to NN11.04.  I'm 71 years old, just want my computer to be a tool, not a toy.  I don't want to have to buy a 4th printer...Good luck.

---

### Post by linuxinstalledfromhdd on 2011-06-10
> **docklc said:**
> I have probably put in 40 hours trying to get my ip1800 to work under Ub HH trough NN11.04 following multiple URLs by others--Spain, Australia, Europe, etc (Interesting that NO Americans seem to have the incentive to come up with a solution).  

I have an AMD 5600x2 system.  My Canon scanner, an N670U worked immediately.  If the Linux folks want us all to buy Windows 7, this is the way to do it--don't provide any basic drivers for older Canon printers.  I have three great Canon printers: an i550, an ip1700 and an ip1800.  NONE will work on my AMD64/Ubuntu system.  ALL will work on my older, slower WinXP system.  

Canon has released drivers for Linux in rpm.  But, apparently no one in the Open Source community has the time or interest in making/updating these Canon drivers to NN11.04.  I'm 71 years old, just want my computer to be a tool, not a toy.  I don't want to have to buy a 4th printer...Good luck.

You probably need to be using a 32-bit installed version of Ubuntu...  Don't use 64-bit..    Use 32-bit and try installing the drivers.. and then updating your kernel to PAE.  Done deal.

---

### Post by zephyr707 on 2011-06-21
I ran this:

cd /tmp && wget [http://www.linuxone.pl/download/canon_ip1800_deb.tar.gz](http://www.linuxone.pl/download/canon_ip1800_deb.tar.gz) && tar xzf canon_ip1800_deb.tar.gz && sudo ./install.sh
and stuff seemed to happen, I replugged my printer into the usb port and it recognized and said it was ready to be used.  Showed up in the print menus and everything, great!  But when I go to print it pops up the queue and then disappears, no printing.  When I check the print queue again, it says all the jobs were completed.

I have five jobs sitting in /var/spool/cups and no pages printed.  The ip1800 is just looking at me with a green light and i want to smash it... any help would be appreciated (in getting the printer to print, not smashing, I am pretty good at that already ;P  )

thanks
z

---

### Post by zephyr707 on 2011-06-21
ok!  got it working following a link from sidfadnis:

[http://www.znupii.ro/how-to-canon-pixma-ip1800-si-ip1900.html]("http://www.znupii.ro/how-to-canon-pixma-ip1800-si-ip1900.html:guitar:")

at first I clicked on the link and it went to a 404 page, but I realized that there was a :guitar: tagged onto the end, maybe some sort of smiley.  Anyways, without that it works, and the instructions are easy and they work for me: xubuntu 11.04 32bit, canon pixma ip1800.

thanks!
z

---

### Post by zephyr707 on 2011-06-21
ha, guess it definitely was a smiley.  I can't seem to find a grayscale option for this driver, or a way to print color.  All the colored parts of the page are printed blank.  But b&w is a pretty good start I guess.

---

### Post by kevinjones30 on 2011-11-16
Zephyr,

the link you posted is no longer available...I've got the same problem as you in that my printer appears to be installed properly, but when I print a job appears in the print list, but then immediately say completed...with no printing!

Any advice how to resolve this?

Thanks,

Kevin

---

### Post by kevinjones30 on 2011-11-16
Hi all, 

I've searched for, and tried various solutions to issues with this printer but haven't had any luck as of yet..hoping someone has some words of wisdom!

I'm running Ubuntu 11.10, I have an ip1800 printer, have installed drivers as advised by various posters. Ubuntu recognises my printer, but, when I print something, the job shows up in the printer list for a couple of seconds then immediately says it has completed, but no printing occurs. 

Any ideas how to resolve this?

Thanks,

Kevin

---

### Post by jimmac49 on 2011-11-16
Google and download:-
Canon-Pixma-ip1900-ip1800-KarmicKoala.tar.gz

I run 11.10 from a Kingston USB drive and the above works for me.


Luck

Jimmac49

---

### Post by mörgæs on 2011-11-16
Kevinjones30, please don't double-post. 
Threads merged.

---

### Post by lupas on 2011-11-18
> **jimmac49 said:**
> Google and download:-
Canon-Pixma-ip1900-ip1800-KarmicKoala.tar.gz

I run 11.10 from a Kingston USB drive and the above works for me.


Luck

Jimmac49


That is the ans my friend.

---

### Post by empitt on 2011-11-19
Kevinjones30, should work: [http://ubuntuforums.org/showpost.php?p=10548102&postcount=7](http://ubuntuforums.org/showpost.php?p=10548102&postcount=7) & [http://ubuntuforums.org/showpost.php?p=10781817&postcount=15](http://ubuntuforums.org/showpost.php?p=10781817&postcount=15)

---

