---
title: "Being positive: hwo to make my hardware to work?"
date: 2006-02-02
forum: General Help
---

### Post by tico on 2006-02-02
Ok, I'll try once more. :)   I'm using Ubuntu Live CD and I cannot make my scanner (Lide50) and my printer (Lexmark z515) to work. So, could someone please help me to fix this?

1. Scanner - Live CD has xsane 0.97 and there's a 0.991 version, but Synaptic doesn't find it. I've downloaded it from xsane, but I don't know how to install it to make my scanner work. Could you pls give a good a detailed expanation? Thanks.

2. Printer - I have find no driver for my Lexmark z515. Is there any hope to make it work on Ubuntu (using the Live CD to try it)?

Thanks once more.

---

### Post by Joeb on 2006-02-02
I'm not sure about your scanner problem, but I looked at [www.linuxprinting.org](www.linuxprinting.org) (the place to go for printer issues with Linux) and they don't even list the z515.  I did find this link, which may help:  [http://www.aquarionics.com/article/name/Making_the_Lexmark_Z515_work_under_Debian_Linux](http://www.aquarionics.com/article/name/Making_the_Lexmark_Z515_work_under_Debian_Linux)

I usually try to shy away from Lexmark as they usually aren't Linux friendly and the cartridges usually cost as much as the printer!  Plus, it is always a good idea to check out [www.linuxprinting.org](www.linuxprinting.org) to see a prospective printer is compatable with Linux.

---

### Post by tico on 2006-02-02
Thanks for your answer. I've already found this article, but the link to the driver doesn't work...

---

### Post by tico on 2006-02-03
Does anybody has any other suggestion?

---

### Post by steve.horsley on 2006-02-03
You may have to accept that you have bought from manufacturers who choose not to support Linux. Drivers may simply not exist. 

Epson printers and scanners are well supported, and I hear that HP are too.

---

### Post by akiro.yamamoto on 2006-02-03
I checked the SANE website for info on the LIDE 50 scanner ( It's a CANON , right?).
[http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon&model=&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon&model=&bus=any&v=&p=)

According to yhat site they have GOOD Support for that scanner with the 
sane-genesys driver ( also called a back-end ;) )
[http://www.sane-project.org/man/sane-genesys.5.html](http://www.sane-project.org/man/sane-genesys.5.html)

This should be a good place to start. 
Just as in Win your hardware will need the correct drivers in order to function 
properly. 
As far as the Lexmark goes..... Hmmmm! 
Lexmark has a history of creating products that are problematic to set-up and configure even in Win.... So unless you can get your hands on the Lexmark Drivers
your going to have problems with that printer. Sorry!

---

### Post by akiro.yamamoto on 2006-02-03
I found an alternate site for the driver referenced in Joeb's post:
[http://www.opendrivers.com/freedownload/231925/lexmark-z612-z614-z615-z617-printer-driver-v1.0-1-red-hat-linux-download.html](http://www.opendrivers.com/freedownload/231925/lexmark-z612-z614-z615-z617-printer-driver-v1.0-1-red-hat-linux-download.html)

---

### Post by tico on 2006-02-03
Hi, akyro.yamamoto,

thanks for your answer. Could you pls tell me with details how to install this new version of xsane? I'm a newbie...

TIA

---

### Post by akiro.yamamoto on 2006-02-03
That printer driver is the z600.tar.gz driver I saw referenced for another Lexmark Printer. I think you can use it for the X1150 All In One (Printer set-up Only).
As far as I can remember it was not a very good set-up with that printer, of course
YMMV ;) .

---

### Post by akiro.yamamoto on 2006-02-03
Don't re-install xsane.
xsane is only the GUI for SANE...

---

### Post by akiro.yamamoto on 2006-02-03
When you run XSane what errors do you get.... Exactly!
What do you mean it doesn't work?
Is the scanner detected at all by xsane?

---

### Post by akiro.yamamoto on 2006-02-03
The version of SANE used for breezy is 1.15 the version you need is 1.17.....
I'll check if you can install it from dapper (if available) and get back to you. ;)

---

### Post by tico on 2006-02-03
[QUOTE=akiro.yamamoto]When you run XSane what errors do you get.... Exactly!
What do you mean it doesn't work?
Is the scanner detected at all by xsane?[/QUOTE]
 Ubuntu detects both my scanner and my printer, but it doesn't install the driver (because there's no right driver in the Live CD; that's important: I'm using an Live CD for testing pruposes). When I run xsane I get a message that says "no device found" or something like that (sorry, I'm in WinXP right now).
Any idea?

---

### Post by akiro.yamamoto on 2006-02-03
I'm downloading the dapper libsane package now (dial-up) ;) .
But in the interim you can use the z600 driver to set-up your printer.

EDIT:
The package won't install, dependancy problems.
So here is a hack......
Copy the following and paste it into a file called gensys.conf
[QUOTE=akiro.yamamoto]
##################################################
# genesys.conf: Configuration file for Genesys Logic GL646 and GL841 based scanners

#
# scanners that are not yet supported
# uncomment them only for developpment purpose
#

# UMAX Astra 4500 and Avision iVina 1600
#usb 0x0638 0x0a10

# Hewlett Packard ScanJet 2400c
#usb 0x03f0 0x0a01

# Hewlett Packard ScanJet 3670c
#usb 0x03f0 0x1405

# Plustek OpticPro ST24
#usb 0x07b3 0x0601


#
# supported scanners
#

# Medion MD5345/MD6228/MD6471
usb 0x0461 0x0377

# Hewlett Packard ScanJet 2300c
usb 0x03f0 0x0901

# Canon LiDE 35/40/50
usb 0x04a9 0x2213

# Canon LiDE 60
usb 0x04a9 0x221c
###########################################
[/QUOTE]
Ok now save that file and move it to /etc/sane.d

sudo cp genesys.conf /etc/sane.d

This may not work but if it works you should be able to use your scanner....
Otherwise you will have to compile and install the entire sane package.....
OK fire up xsane and let er rip :smile:

Keep your fingers crossed :smile:

---

### Post by akiro.yamamoto on 2006-02-03
This is the data package from libsane 1.0.17 it contains the files for the driver you need.

---

### Post by nocturn on 2006-02-03
Look here for your printer:
[http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

 Printers confirmed to work: Lexmark Z515 (using devfs and udev)

---

### Post by tico on 2006-02-03
Hey, thanks, I'll try this later (still in WinXP). Hope this will work with the Live CD...

Concerning the printer, could you ls give me more details on how to intall the driver. The newbie here (me :mrgreen:  ) doesn't has no clue...

---

### Post by nocturn on 2006-02-03
[QUOTE=tico]Hey, thanks, I'll try this later (still in WinXP). Hope this will work with the Live CD...

Concerning the printer, could you ls give me more details on how to intall the driver. The newbie here (me :mrgreen:  ) doesn't has no clue...[/QUOTE]

We can help you with that, but won't work on the LiveCD, you need an installation (have to replace files).

The lexmarks seem pretty nasty in Linux though, I have to say.

---

### Post by tico on 2006-02-03
How nasty? More details?

PS.: Where are you from in Belgium? I lived 6 years in LLN.

---

### Post by ZylGadis on 2006-02-03
tico, I suppose this is a follow-up to your other topic. Some good has come out of that, I see.
First of all, you have been trying to use linux for 8 years, and you are still a newbie? That by itself speaks volumes for your enthusiasm and willingness.
Second, you don't use the LiveCD for work. You use it for the purpose it exists - to see what Ubuntu Linux is. The Live CD is a demo version and you cannot expect to tweak it nearly as much as an installed version.
If you have the willingness to install Ubuntu and see for real that your hardware works/does not work (after 8 years of trying?), be my guest. If you lack it, stop trolling.
I apologize to the rest of the forum for the acrid mood, but I wasted an hour or so yesterday trying to help this... linux enthusiast, and I'd like to prevent other people from falling in the same pit.

---

### Post by tico on 2006-02-03
Hi, Alex,

Thanks for your answer. I'm using the Live CD for two things:

1. The other times, I've "wasted" time installing other distros that I could not use.
2. Since I need to resize my HD, I'm preparing the installation, making backups etc. (lot of stuff and every little thing configured in Windows. My last Win install was more than 2 years ago) So I need some more time before I install Ubuntu.

Just one thing (don't get me wrong!): it's not so kind to talk about "pits" and "trolls" here. I'm not wishing other people to fall in my "pits" and I wonder what exactly a "troll" means here in this forum. As I said before, my intention was not to be unkind, just to express my "frustration" (even if it's my fault, since I'm a newbie after 8 years ;)  )
And about myself being a "newbie" after 8 years trying: I didn't spend 8 years trying Linux. During this 8 years, I tried Linux every 1 and a half year or so. To see if it was "mature" for me. As I said before, many progress was done and I hoped this time would be THE time. Hope I'm not "trolling" again :-#

---

### Post by tico on 2006-02-03
Just one more thing: If I'm not welcome here, no problem, I'll stop "trolling" these "human beings" that use Ubuntu and will bother farway. I just cannot understand why people were so troubled with my post even after I apologize for being (maybe) unkind (what was not my intention, as I said). Once more, or maybe twice: my apologies for trying to act like a "human being" ;)

---

### Post by ZylGadis on 2006-02-03
You were inundated with suggestions what to do in the other thread. You decided to ignore all of them and keep saying "My scanner does not work with the live cd, I'm very disappointed with linux again, I'll not use it." If you won't use it just don't use it and stop there. I call wasting other people's time, given in good faith, trolling.
I realize you are doing it again - wasting my time, so I'll just stop here and ignore you, as some people more clever than me have already done.

---

### Post by tico on 2006-02-03
Before you ignore me, just do me a little favor: point me in the present thread something like "I'm very disappointed with linux again, I'll not use it". This was on another thread and that's why I started a new one with the title "Being positive".
If I was not interested in using Linux, I would not be here "trolling" people. But just do me this favor: point me in this thread the famous "I'm very disappointed with linux again, I'll not use it".

---

### Post by tico on 2006-02-03
Ok,
Before I install Ubuntu, I need to solve a little doubt. I've downloaded and teste (Live CD) the alpha version of next Ubuntu. My scanner was recognized \\:D/  .  If I install the 5.10 version, is it easy to upgrade or should I make a clean install when the next Ubuntu version sees the light?

TIA

---

### Post by tico on 2006-02-03
[QUOTE=akiro.yamamoto]This is the data package from libsane 1.0.17 it contains the files for the driver you need.[/QUOTE]

Hi, I tried your tip. I'm getting the following message:
root@ubuntu:~# cp genesys.conf /etc/sane.d
cp: cannot stat `genesys.conf': No such file or directory

Any idea on what's happening?

Thanks for trying to help me.

---

### Post by Joeb on 2006-02-03
[QUOTE=tico]Ok,
Before I install Ubuntu, I need to solve a little doubt. I've downloaded and teste (Live CD) the alpha version of next Ubuntu. My scanner was recognized \\:D/  .  If I install the 5.10 version, is it easy to upgrade or should I make a clean install when the next Ubuntu version sees the light?

TIA[/QUOTE]

Yes, it is easy to do an upgrade and no, you don't have to do a clean install.  You would just need to change the repositories for apt-get to point to the new ones and then either tell apt-get to do a dist-upgrade or do the same thing in Synaptic.

---

### Post by tico on 2006-02-03
[QUOTE=Joeb]Yes, it is easy to do an upgrade and no, you don't have to do a clean install.  You would just need to change the repositories for apt-get to point to the new ones and then either tell apt-get to do a dist-upgrade or do the same thing in Synaptic.[/QUOTE]
 Ok, Thanks. So I think I'll install Breeze in some days. I was very glad to see that the new version will recognize the scanner automaticaly.

Thanks again.

---

