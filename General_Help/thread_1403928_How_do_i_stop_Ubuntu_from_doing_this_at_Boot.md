---
title: "How do i stop Ubuntu from doing this at Boot?"
date: 2010-02-10
forum: General Help
---

### Post by JoeyF on 2010-02-10
[http://ubuntuforums.org/showthread.php?t=1400392](http://ubuntuforums.org/showthread.php?t=1400392)

Sorry for posting this again. Needed to change the title. :o


*Check the last post on that thread by me* *How to turn it off right if it freezes*

And do you think i would have the same trouble if i switched to Mint?

---

### Post by JoeyF on 2010-02-10
Ok. So i am going to reinstall. But when it freezes and you can't click on anything how do you turn it off right?(Not during install. When on the Desktop)

Thanks.

---

### Post by HappyFeet on 2010-02-10
> **JoeyF said:**
> how do you turn it off

Push and hold in the power button for a few seconds.

---

### Post by flippo on 2010-02-10
If you can drop to a terminal (ctrl+alt+f1) then log in and do 'sudo poweroff' to turn off your machine or 'sudo shutdown -r now' to restart your machine.  If you can't drop to a terminal (ctrl+alt+f1) then you may be frozen to hard to restart.  

Also, once in a terminal (ctrl+alt+f1) you can return to gnome with (ctrl+alt+f7).  You can also attempt to restart a frozen gnome with 'sudo /etc/init.d/gdm restart'.

---

### Post by JoeyF on 2010-02-11
Thanks. One last thing:What causes Ubuntu to mess up when you turn it off wrong and is there any way to fix it without reinstalling?

---

### Post by flippo on 2010-02-11
On 8.04 if I do a hard shutdown (improper) then it starts up fine, assuming my disks are not corrupted, so I'm not entirely sure what your asking. 

Please also note I entered the wrong instruction to shut down the computer, its 'sudo poweroff' the apt-get should not be there, I don't know why I put it there...

---

### Post by JoeyF on 2010-02-11
Maybe it's a driver issue. It's like a small rectangular color flash at boot.

---

### Post by JoeyF on 2010-02-11
Ok, So i went into the Terminal UI and went back to Gnome to test it out to see if that would trigger it and it did. But i got a video of it.

[http://tinypic.com/player.php?v=vf8q9z&s=6](http://tinypic.com/player.php?v=vf8q9z&s=6)


Computer:Gateway MD2614U

OS:Ubuntu 9.10 64 Bit.


Help? :confused:

Thanks.

---

### Post by JoeyF on 2010-02-12
Got that fixed.

Can you take a look at :[http://www.linuxquestions.org/questions/ubuntu-63/why-is-it-flashing-during-boot-788599/](http://www.linuxquestions.org/questions/ubuntu-63/why-is-it-flashing-during-boot-788599/)

Thanks.

---

