---
title: "Wifi Card Driver"
date: 2006-04-07
forum: General Help
---

### Post by wcks48 on 2006-04-07
i installed unzip ndiswrapper and installed the .inf file which i took from my XP. when i typed 

ndiswrapper -l   ; it comes out with the message "installed ndis drivers: InfFileName, driver present, hardware present

but as shown in the readme file, i type "modprobe ndiswrapper" it says, 
FATAL error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted.

so, what had happen? i opened the network setting, but still unable to "enable my wlan0. 
any solution pls.. thanx.

---

### Post by binarysleeper on 2006-04-07
I suspect you need to stick sudo at the start of the command line to execute the command under the root account. It will ask you for the password, just use your normal one.

---

### Post by wcks48 on 2006-04-08
sith sudo, everything okay. i confirm the driver installed. but how to enable the wifi card and make it detect the network? i can't enable it in the network setting mode.

when i want to log in with root user in start up, it requires me the root password, which i don't think i ever set one for it. how could i tackle these problems? so i can log in as root to enable the wifi to detect the signal.

---

### Post by binarysleeper on 2006-04-08
I've not encountered this problem myself (I don't need to use ndiswrapper any more - new card), but googleing your error message came up with these 2 Ubuntu specific threads:
[http://www.ubuntuforums.org/archive/index.php/t-76763.html](http://www.ubuntuforums.org/archive/index.php/t-76763.html)
and
[http://www.ubuntuforums.org/archive/index.php/t-76310.html](http://www.ubuntuforums.org/archive/index.php/t-76310.html)

Have a read of those and try the suggestions there.

Good luck

---

### Post by mlm2012 on 2008-03-31
Binary Sleeper, will you please tell me which wifi card you found that works with Ubuntu?  Also is it 802.11g or what?  Also, if it's an exotic or obscure card, where I can get one?  Your help will be like a miracle and, no doubt, generate more good karma.  Thanks, Michael  [email]mlm2012@gmail.com[/email]

---

