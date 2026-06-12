---
title: "Help re-installing ubuntu!"
date: 2012-06-04
forum: General Help
---

### Post by codyjraines95 on 2012-06-04
Hey guys, I JUST recently got my pc in working boot order. I was dual booting windows 7 and ubuntu 11.04, I accidentally deleted the ubuntu partition and got my computer to working boot order. I want to re-install ubuntu back on my computer and dual boot it with windows 7 again....The only problem is when i try to install ubuntu 12 on here all i get is a flashing cursor in the top left corner..I've tried from a live cd, usb, and wubi please help this linux newbie!!!

---

### Post by wilee-nilee on 2012-06-04
Try the nomodeset option.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by codyjraines95 on 2012-06-04
haha worked on the first try!!! thanks man! \\:D/ 

Any way I can give you rep or something?? Anyways your help was very much appreciated!!

---

### Post by wilee-nilee on 2012-06-05
> **codyjraines95 said:**
> haha worked on the first try!!! thanks man! \\:D/ 

Any way I can give you rep or something?? Anyways your help was very much appreciated!!

Hehe, glad your going, just share the help with others. ;)

---

### Post by codyjraines95 on 2012-06-05
Well that was long lived....haha I logged on last night and updated all the drivers, my Nvida ones wouldn't for some reason :P but now when I'm in the boot loader and select ubuntu it begins to log in and stops at a purple screen... any ideas how to fix that?

---

### Post by codyjraines95 on 2012-06-05
new update, just un-installed ubuntu again haha...i really want to get it back but i can't get it to work right! :(

---

### Post by wilee-nilee on 2012-06-05
> **codyjraines95 said:**
> new update, just un-installed ubuntu again haha...i really want to get it back but i can't get it to work right! :(

Graphic drivers are not really my area, but it would help others if you posted some info.

Are you using the drivers from the Ubuntu repo?

What is the nvidia card, this command may tell you.
     ```
lspci | grep VGA  
```

---

### Post by codyjraines95 on 2012-06-05
It is a nvidia gtx 550ti

---

### Post by codyjraines95 on 2012-06-05
and i have no idea what drivers i'm using..i'm a complete linux n00b lol

---

### Post by wilee-nilee on 2012-06-05
> **codyjraines95 said:**
> It is a nvidia gtx 550ti

Are you using the repos driver, that is a key thing here, the ones on the nvidia site will break with a update, at least that&#8217;s what I see recommended.

Here is a ubuntu link, maybe within this are the keys to get that card running correctly.

[http://askubuntu.com/questions/127305/how-to-install-ubuntu-12-04-on-a-computer-with-a-nvidia-geforce-gtx-550-ti](http://askubuntu.com/questions/127305/how-to-install-ubuntu-12-04-on-a-computer-with-a-nvidia-geforce-gtx-550-ti)

All I know with this area is from lurking the forums and the IRC, so the IRC freenode channel #ubuntu may be another source as well for help if needed.

The additional drivers app I would think offer the correct drivers if you have not tried this after a install.

---

### Post by codyjraines95 on 2012-06-05
I'll try it, i tried to update them yesterday but they wouldn't

---

### Post by codyjraines95 on 2012-06-05
I have it installed I'm in recovery mode right now updating the packages and I also updated the grub loader to grub2 anything else I need to do?

---

### Post by codyjraines95 on 2012-06-05
I got logged in!!!! Haha I'll keep you posted if something doesn't work

---

### Post by codyjraines95 on 2012-06-05
And I can't activate the nvidia drivers....it says sorry, installation of this driver failed.
 Please have a look at the log file for details: /var/log/jokey.log

---

### Post by codyjraines95 on 2012-06-05
> **wilee-nilee said:**
> Are you using the repos driver, that is a key thing here, the ones on the nvidia site will break with a update, at least that’s what I see recommended.

Here is a ubuntu link, maybe within this are the keys to get that card running correctly.

[http://askubuntu.com/questions/127305/how-to-install-ubuntu-12-04-on-a-computer-with-a-nvidia-geforce-gtx-550-ti](http://askubuntu.com/questions/127305/how-to-install-ubuntu-12-04-on-a-computer-with-a-nvidia-geforce-gtx-550-ti)

All I know with this area is from lurking the forums and the IRC, so the IRC freenode channel #ubuntu may be another source as well for help if needed.

The additional drivers app I would think offer the correct drivers if you have not tried this after a install.

My graphics driver right now is VESA: GF106B board - 10500000

---

### Post by wilee-nilee on 2012-06-05
Hopefully someone else will see what&#8217;s up.  When you install drivers I have seen the advice is to remove to others first, but this is with consecutive nvidia drivers.

It may be a simple as removing the nvidias installed if any are there, doing a update, and checking the additional drivers app.

I think it is a workable situation from the web links I have seen, it just may be using the correct path or technique to get it done.

If you have more problems here I would start a thread on this and have the card in the header, this makes it more likely those that know will respond.

---

### Post by codyjraines95 on 2012-06-05
Solved it......thanks for the help bro sorry for being a noob haha

---

