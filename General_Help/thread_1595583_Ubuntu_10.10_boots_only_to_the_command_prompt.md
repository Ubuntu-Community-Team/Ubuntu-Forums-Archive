---
title: "Ubuntu 10.10 boots only to the command prompt"
date: 2010-10-13
forum: General Help
---

### Post by gatorbrit on 2010-10-13
I just upgraded my desktop to 10.10.   All seemed to go fine.  The computer then prompted for a reboot, and on rebooting it boots to the shell prompt.

Any suggestions?

Thanks

---

### Post by Refalm on 2010-10-13
If you have a nvidia laptop card, and you installed the non-free driver, read here:
[http://ubuntuforums.org/showpost.php?p=9965364&postcount=9](http://ubuntuforums.org/showpost.php?p=9965364&postcount=9)

---

### Post by gatorbrit on 2010-10-13
> **Refalm said:**
> If you have a nvidia laptop card, and you installed the non-free driver, read here:
[http://ubuntuforums.org/showpost.php?p=9965364&postcount=9](http://ubuntuforums.org/showpost.php?p=9965364&postcount=9)


I have a fairly basic nvidia card, but the computer is a desktop not a laptop.  Is there any way to see if the video card is the problem?

thks

---

### Post by gatorbrit on 2010-10-13
Ha - a solution...  Disable the existing video driver..

Followed the instructions here and all is well..

[http://ubuntuforums.org/showpost.php?p=9949419&postcount=9](http://ubuntuforums.org/showpost.php?p=9949419&postcount=9)

---

### Post by noicestar on 2010-11-08
I have recently upgraded to 10.10. However I have followed the previous advice but it does not work.

Each time i reboot the machine the Ububtu 10.10 flashes up for a few seconds (the boot screen with the imgage of Ubuntu) but then abruptly flashes a few times and the command line prompt screen appears asking my to login. Which I do and enter my password.

However how do I get my gui to start working (what do I havev to type in the command screen). Im getting the feeling that upgrading was not a wise choice considering 10.04 was trouble free!
 

Please help if you can!

---

### Post by gatorbrit on 2010-11-08
> **noicestar said:**
> I have recently upgraded to 10.10. However I have followed the previous advice but it does not work.

Each time i reboot the machine the Ububtu 10.10 flashes up for a few seconds (the boot screen with the imgage of Ubuntu) but then abruptly flashes a few times and the command line prompt screen appears asking my to login. Which I do and enter my password.

However how do I get my gui to start working (what do I havev to type in the command screen). Im getting the feeling that upgrading was not a wise choice considering 10.04 was trouble free!
 

Please help if you can!


It sounds like a video driver issue.   Did you add the word "nomodoset"  (no quotes) after the boot line and try booting?  That will cause ubuntu to use a really basic driver that will look ugly but will get you into the desktop.

---

### Post by Lindelani on 2011-07-07
i have the same prolem,Just reinstalled the NVIDIA drivrs and after reboot it boots to command promt,Please hepl

---

