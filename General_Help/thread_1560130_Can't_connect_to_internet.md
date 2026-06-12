---
title: "Can't connect to internet"
date: 2010-08-24
forum: General Help
---

### Post by fastop on 2010-08-24
I had Ubuntu 10.04 on my laptop, it started messing around a bit so i decided to do a clean install. 

I downloaded the new Ubuntu file which is "10.04.1" and installed. Installed perfectly, except my internet. It goes in a continual "Authentication required by wireless network" loop, when I know for a fact I put in the right wep key as my 2 other computer's connect fine. It looks like it's about to connect but then prompts me for the key.

My wireless card is Intel Wireless 3945ABG.

Has anyone else had this problem? Or anyone know how to solve it? Thank you :)

---

### Post by pricetech on 2010-08-24
Can you give us some more information.  What kind of laptop is it ?? What hardware, specifically the NIC ??

---

### Post by nacho32 on 2010-08-24
I have had that same problem 10.04 was a network nightmare asked for the key I put the right key in and gave some lame wrong password when I knew it was correct since I run a dual boot Win7, tried my friends router same thing. Degraded back to 9.10 and I'm staying with it.

---

### Post by emmerc on 2010-08-25
Hi Friends,

I have a Toshiba Satellite P305-S8832 with the Ethernet card  Marvell Yukon 88E8040T and the Intel Wireless 3945ABG.

I have installed Ubuntu Linux 10.04.1 LTS and so far I have managed both the wired and wireless network to work flawlessly with the two flavors 32bits and 64bits.

When I tried the Ubuntu 10.04.1 live CD everything worked so I did the installation but once I did all the updating, the wired connection went undetected. When I tried the fixes I found in the network, I ended without wired and wireless connection.

I did a new fresh installation and I did all the updates with the exception of the kernel. I am using still the kernel 2.6.32.24.39 because when I updated it to the kernel 2.6.32.24.41 the mess happens.

So I suggest to install 10.04.1 (either 32 or 64 bits) but retain the kernel 2.6.32.24.39 until some other than 2.6.32.24.41 appears on the horizon.

I'm writing this post on my Toshiba P305-S8832 connected through the wireless of my machine and the Marvell Yukon 88E8040T is there ready for any wire to come and the Intel Wireless 3945ABG is working just fine!.

Hope this might help you Friends!

---

### Post by Bucky Ball on 2010-08-25
Have you plugged in an ethernet cable and gotten all updates? Get online with a cable first, you could be missing some firmware for your wireless card. Plugging a cable in will possibly help. Might take a few minutes to detect the card or you can go for an update.

---

### Post by emmerc on 2010-08-25
Hi Bucky Ball,

When I downloaded and apply all the available updates my Ethernet resulted undetected and not working at all. Then I began a try and error strategy and began with the Kernel. When I rolled the kernel back from 2.6.32.24.41 to 2.6.32.24.39 the whole thing came back to life.  That's why I decided to stay with the kernel 2.6.32.24.39 and all the connections work very well. That is not the case with 2.6.32.24.41 even with all the workarounds I tried. Some of the workarounds even rendered my wireless undetected. 

Thanks Friend!

---

### Post by Bucky Ball on 2010-08-25
I still use 8.04 LTS because I need my machines stable and reliable. Updates can be a little unpredictable on newer releases but no doubt the next update or the one after that will fix your problems. I would stick with what works. It is no big deal not having the latest. It is NOT always the greatest. That is windows thinking and look what happened to Vista! ;)

---

### Post by emmerc on 2010-08-26
I agree on that!!! Yes stability and reliability are more important in a production machine! Sure, good for you friend and thanks for the dialogue!

---

### Post by dineshs on 2010-08-26
Do not know whether this is related
[http://ubuntuforums.org/showpost.php?p=9680300&postcount=14](http://ubuntuforums.org/showpost.php?p=9680300&postcount=14)
or
[http://ubuntuforums.org/showpost.php?p=9767936&postcount=11](http://ubuntuforums.org/showpost.php?p=9767936&postcount=11)

---

