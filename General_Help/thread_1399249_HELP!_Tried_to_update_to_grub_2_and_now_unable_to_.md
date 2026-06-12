---
title: "HELP! Tried to update to grub 2 and now unable to boot"
date: 2010-02-05
forum: General Help
---

### Post by Enigmapond on 2010-02-05
Hi..

I thought I was doing good by updating the Grub and followed the instructions on how,,,but now I can't boot and just gives "error 15". I had to boot off of a live jaunty cd I had to get here. Is there anything I can do from here or do I need to re-install?? Please Help!!!

---

### Post by andrewdvalles3 on 2010-02-05
Hello, folks.  The latest Ubuntu update, though greatly appreciated, has the boot loader now unable to find the Kernel.  GNU GRUB2 simply produces a prompt which accomplishes very little.  In short, today's Ubuntu update was performed, I was asked to reboot the computer, and then... no OS.  Please advise.  Undoubtly others may have this issue as well.

---

### Post by Kir_B on 2010-02-05
Your not the only ones. Read my posts in this thread: 

[Karmic Update to 2.6.31-19 & Grub, Boot Help]("http://ubuntuforums.org/showthread.php?t=1399135")

good luck all. kir_b

---

### Post by Enigmapond on 2010-02-05
well I'm not that good at this and I only have a Jaunty live cd. I can see all my files and I have two kernels currently.... Is there a way just to modify things manually so that I can boot?

---

### Post by Enigmapond on 2010-02-05
Kir-b you are my hero for today. I read your thread and followed the advice given to you...set this...bashed the other thing...updated Grub and voila!  I'm now back to my Karmic installation. Thank you! Serves me right for being bored and seeing what I could do next...gotta love Ubuntu, certainly keeps you on your toes.

If I forgot to say Thank you...

[SIZE=7]**THANK YOU!!!:D**[/SIZE]

---

### Post by r_s on 2010-02-05
Jaunty cd .. well Jaunty does not have grub2 , it has the older version of grub.

---

### Post by Kir_B on 2010-02-05
Awesome!!! I'm extremely pleased to hear that I could be of help, but the real hero is "lmarmisa". Please stop by his page and let him know that his helping me has in turn helped you.

Again. AWESOME!!!  Peace and have a great day. Kir_b):P

---

### Post by Kir_B on 2010-02-05
> **r_s said:**
> Jaunty cd .. well Jaunty does not have grub2 , it has the older version of grub.

You won't have to worry about the live cd not having grub2, trust me. I was forced to use the jaunty cd to fix mine. Just follow, to the letter, the instructions given by "lmarmisa" in the [COLOR=#cc33cc][my grub2 nightmare won't end thread]("http://ubuntuforums.org/showthread.php?t=1325901").
                                             Good luck Kir_b
[/COLOR]

---

### Post by r_s on 2010-02-05
But you would have installed the older version of grub , not grub2.

---

### Post by Kir_B on 2010-02-05
> **r_s said:**
> But you would have installed the older version of grub , not grub2.

Sorry, I'd have gotten back to you sooner, but I thought that I was clear enough on what needs to be done. Sorry. If you are indeed running grub2 either through manually upgrading grub legacy after upgrading Jaunty, or you've installed a fresh Ubuntu Karmic Koala. If the either of the previous statements are the case, you are indeed running grub2. If this is the case, follow to the letter, the instructions that I recieved from "lmarmisa" in the "[COLOR=#cc33cc][my grub2 nightmare won't end]("http://ubuntuforums.org/showthread.php?t=1325901")[/COLOR]" thread.  When I fixed mine, I was also using a Jaunty CD. What lmarmisa had me do, was mount my O.S. {Ubuntu}, reinstall grub2 to it and then update the grubs config file. The reinstalled grub comes from the Ubuntu repositories and not the CD.

If you are running grub legacy, replace the "grub2" portion of his commands with "grub" and you might be okay. I'm no expert, so if you have any doubts at all, post a new thread that is very concise in detail about exactly what is going on.

I'll check back every ten minutes or so, just to see if I can help any further.
                           Good luck and peace. Kir_b

---

