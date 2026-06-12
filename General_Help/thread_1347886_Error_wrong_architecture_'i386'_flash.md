---
title: "Error: wrong architecture 'i386' flash"
date: 2009-12-06
forum: General Help
---

### Post by gmerindol on 2009-12-06
Okay so I'm running a 32bit version and I've been trying to install Adobe Flash Player for a long time. No luck i've been researching and no luck.
The error is:
Error: wrong architecture 'i386' flash 
Package: adobe-flashplugin

And it's thru the package installer.

Thanks a lot.

Edit: I've been trying to install it from the .deb file
So.... install_flash_player_10_linux.deb
Output of uname-m: x86_64

---

### Post by mikewhatever on 2009-12-06
Can you post the output of **uname -m** from Terminal. Can you also elaborate on the way you've been trying to install flash.

---

### Post by gmerindol on 2009-12-06
I just edited my recent post, is that good?
P.S: I didn't think I had a 64bit version if that's what the output means...
I don't even think my computer is 64bit...
It's a Dell latitude D620 running on an Intel Core Duo Processor (Windows XP)

---

### Post by lexfati on 2009-12-06
Yes, that output means you have the x64 bit version.

---

### Post by gmerindol on 2009-12-06
Okay so What do i do?

Edit: What I really mean, is, What are my possibilities?

---

### Post by Psumi on 2009-12-06
You'll want to install the adobe plugin from the repos:

sudo apt-get install flashplugin-nonfree

or install the 64-bit beta/alpha release:

[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

I suggest the flashplugin-nonfree method because 64-bit is pretty unstable.

---

### Post by LuisGMarine on 2009-12-06
Even better follow this link, this script works like a charm.  Good luck! :popcorn:

[http://ubuntuforums.org/showthread.php?t=1259102]("http://ubuntuforums.org/showthread.php?t=1259102")

---

### Post by gmerindol on 2009-12-06
Okay, I just installed it, it worked, but when I try to click on something in the Flash part of a website, it won't open. 
For instance: A Xat Chat: I try to click on my name to change it, nothing appears, I try to click on someone's name to Private Chat with them, and nothing appears....
What do I do?

Thanks

---

### Post by Psumi on 2009-12-06
> **gmerindol said:**
> Okay, I just installed it, it worked, but when I try to click on something in the Flash part of a website, it won't open. 
For instance: A Xat Chat: I try to click on my name to change it, nothing appears, I try to click on someone's name to Private Chat with them, and nothing appears....
What do I do?

Thanks

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

---

