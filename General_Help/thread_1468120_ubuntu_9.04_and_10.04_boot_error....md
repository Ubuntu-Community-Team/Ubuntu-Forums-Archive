---
title: "ubuntu 9.04 and 10.04 boot error..."
date: 2010-05-01
forum: General Help
---

### Post by sgs112 on 2010-05-01
[CENTER]Hello. :)
[/CENTER]
 I downloaded Ubuntu 9.10-desktop-i386, burned the ISO file to a CD, when I restart the computer and try to boot the CD it works fine, but when choosing a language, and I try to choose any one as "the availability of Ubuntu without any change to the computer or "install ubuntu" and so on ... I allways got an error reading boot cd (I / O error) ...  

[http://img179.imageshack.us/i/100430a005.jpg/](http://img179.imageshack.us/i/100430a005.jpg/) 

what's the problem? please help :confused: [IMG]http://yfrog.com/4z100430a005j[/IMG][IMG]http://img179.imageshack.us/i/100430a005.jpg/[/IMG]

and I have error with ubuntu-10.04-desktop-i386. I see some kind of blue screen, in a midle of the screen i see small keyboard icon and head or something... after few secounds, BOOM... error... :(

---

### Post by Naitsirhc Hsem on 2010-05-01
burning to fast or bad cd drive.  you can use unetbootin to burn the iso to a flash drive.

---

### Post by sgs112 on 2010-05-01
here's how it looks 

[http://img28.imageshack.us/i/100501a001.jpg/](http://img28.imageshack.us/i/100501a001.jpg/)

the same error with the 10.04... :(

---

### Post by sgs112 on 2010-05-01
> **Naitsirhc Hsem said:**
> burning to fast or bad cd drive.  you can use unetbootin to burn the iso to a flash drive.

I tryed to burn with max speed, then next cd with x4 and another with auto speed... but I got the same sh**.

---

### Post by dino99 on 2010-05-01
you a usb stick to boot with, no need to burn again and again tons of cd

---

### Post by sgs112 on 2010-05-01
> **dino99 said:**
> you a usb stick to boot with, no need to burn again and again tons of cd

how can I burn it to the usb stick ? and what the program is unetbootin ?

---

### Post by Naitsirhc Hsem on 2010-05-01
unetbootin.sourceforge.net/

unetbootin lets you can select the iso you downloaded and it extracts the live cd files to the usb drive and then installs a temp boot loader on the drive.  this will work as long as you can boot your computer from usb.  when you are done, you can format the drive and it will be a normal flash drive again.

---

### Post by sgs112 on 2010-05-01
ok. I'll try it.

---

### Post by dino99 on 2010-05-01
Google is your friend :P  search: unetbootin+ubuntu 

but as your are desperate i'll give you a link

[http://www.makeuseof.com/tag/install-linux-with-ease-using-unetbootin/](http://www.makeuseof.com/tag/install-linux-with-ease-using-unetbootin/)

---

### Post by pazuzuthewise on 2010-05-01
To boot then from the usb key, you need to select it (with the usb drive plugged in) as boot device, either by pressing the key to access the boot menu (usually F12) during the initial stage of the boot process, or by setting it as the first boot device in your computer's bios. (see your computer or motherboard manual for the shortcut keys to access the boot menu or the bios settings, and do not alter other settings in your bios, besides the boot order)

---

### Post by sgs112 on 2010-05-01
whitch one I need to choose ?  [http://img709.imageshack.us/i/100501a002.jpg/](http://img709.imageshack.us/i/100501a002.jpg/)

---

### Post by Naitsirhc Hsem on 2010-05-01
usb-hdd or usb-zip or some other usb on the menu

---

### Post by sgs112 on 2010-05-01
it doesnt work... I can't boot it from any "USB-..." 
but when I choose USB-HDD, something happens.
usualy in the black screen I see (boot from CD-ROOM) or something like that, but after USB-HDD choosed it didn't showed up... but still turns on win 7 and win xp dual boot, to choose... and nothing happens..
I have a dual boot, win 7 and win xp sp3. maybe this is a problem ? may it not boot because of windows dualboot? :confused:

---

### Post by Naitsirhc Hsem on 2010-05-01
have you looked in the bios (usually F2 on boot) for the usb drive?  in some systems you can set it to automatically try all usb devices first

---

### Post by sgs112 on 2010-05-01
> **Naitsirhc Hsem said:**
> have you looked in the bios (usually F2 on boot) for the usb drive?  in some systems you can set it to automatically try all usb devices first

can you tell me more detayled ?

---

### Post by Naitsirhc Hsem on 2010-05-01
The bios are very computer specific, if you could tell me the type of computer you have, I can look ate the online manuals and see if it can boot from usb.

---

### Post by sgs112 on 2010-05-01
I did something. 

but it just counting secounds, 10s after 10s and nothing happening: [http://img402.imageshack.us/i/100501a005.jpg/](http://img402.imageshack.us/i/100501a005.jpg/)

when I press tab: [http://img690.imageshack.us/i/100501a006.jpg/](http://img690.imageshack.us/i/100501a006.jpg/)

when i press Esc: [http://img697.imageshack.us/i/100501a007.jpg/](http://img697.imageshack.us/i/100501a007.jpg/)

my computer: **Intel(R) Core(TM) Quad PCU Q9400 @ 2.66GHz**

---

### Post by sgs112 on 2010-05-01
i choosed "HARD DISC" from boot menu and then this USB -->  [http://img442.imageshack.us/i/100501a008.jpg/](http://img442.imageshack.us/i/100501a008.jpg/)

---

### Post by Naitsirhc Hsem on 2010-05-01
You are getting the unetbootin screen, that is good.  check out this for usb install options, unetbootin does not always work. [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by sgs112 on 2010-05-02
still nothing...  with LinuxLive USB Creator 2.5, I created bootable usb. when it boots, I cant choose any options.. and now counting 5 sec. after that- 5 sec again, and again and go on.. 
maybe it is corrupted iso file or something ? but i downloaded fron ubuntu.com...

btw, what is *ubuntu-10.04-desktop-**amd64*** version ? it is for only for amd processors ?

---

### Post by sgs112 on 2010-05-02
yes I think I have a bad iso file. because it is only 504mb... I'm downloading 10.04-desktop-i386  (699mb) from torrents now.
 I hope it will work.

---

### Post by Naitsirhc Hsem on 2010-05-02
bad iso sounds right

---

### Post by sgs112 on 2010-05-02
YES ! finally I did it. :) booting fine, working well

---

### Post by Naitsirhc Hsem on 2010-05-02
congradulations:)

---

### Post by sgs112 on 2010-05-02
thank you :) and thanx for help ;)

---

