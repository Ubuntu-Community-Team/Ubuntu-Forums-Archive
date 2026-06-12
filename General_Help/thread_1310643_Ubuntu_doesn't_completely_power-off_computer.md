---
title: "Ubuntu doesn't completely power-off computer?"
date: 2009-11-02
forum: General Help
---

### Post by tryingtoboot on 2009-11-02
Just installed 9.10 as a dual-boot with XP on my HP a1010n ([specs]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00303941&lc=en&cc=us&lang=en&product=459879&dlc=en")). I'm having a problem where when I shut down Ubuntu, it turns off but doesn't actually power the machine down (I need to tap the power button first). How do I fix that?

---

### Post by Dark_Stang on 2009-11-02
It could be hanging up during shut down. Does it finish turning off if you hit "Ctrl + Alt"?

---

### Post by tryingtoboot on 2009-11-02
> **Dark_Stang said:**
> It could be hanging up during shut down. Does it finish turning off if you hit "Ctrl + Alt"?

You mean, at that last screen (which by the way looks like a black screen with some white terminal words and stuff at really low resolution), I should try pressing Ctrl + Alt? I'll need to get to the computer and try...

UPDATE: This time, I didn't see any terminal-like stuff but the screen was black, and it still hung instead of fully powering down. Ctrl + Alt didn't help, I needed to push the power button.

---

### Post by TheForumTroll on 2009-11-02
Maybe CTRL+ALT+DELETE then? 

You could try to edit /etc/default/bootlogd and change BOOTLOGD_ENABLE=No to BOOTLOGD_ENABLE=Yes. Reboot and have a look in /var/log/boot :)

---

### Post by tryingtoboot on 2009-11-02
> **TheForumTroll said:**
> Maybe CTRL+ALT+DELETE then? 

You could try to edit /etc/default/bootlogd and change BOOTLOGD_ENABLE=No to BOOTLOGD_ENABLE=Yes. Reboot and have a look in /var/log/boot :)

Ctrl alt delete? Really? I could try, but not tonight.

Oh boy... I really need more detailed instructions than telling me to edit something or look in something because I know a lot of these things won't let you edit them... I need you to tell me what to put in terminal... would it be like sudo gedit /etc/default/bootlogd ?

---

### Post by TheForumTroll on 2009-11-02
Okay :)

Press ALT+F2 and write:
```
gksudo gedit /etc/default/bootlogd
```

Then change it from No to Yes. Reboot. Then ALT+F2 and:
```
gksudo gedit /var/boot/log
```

and look for errors (or post it here ;) )


Always use **gksudo** when starting a graphical app like gedit and **sudo** when it is a console app. Using the wrong one could screw things up (or so say the experts. I have no idea how or why) :)

---

### Post by tryingtoboot on 2009-11-02
> **TheForumTroll said:**
> Okay :)

Press ALT+F2 and write:
```
gksudo gedit /etc/default/bootlogd
```Then change it from No to Yes. Reboot. Then ALT+F2 and:
```
gksudo gedit /var/boot/log
```and look for errors (or post it here ;) )


Always use **gksudo** when starting a graphical app like gedit and **sudo** when it is a console app. Using the wrong one could screw things up (or so say the experts. I have no idea how or why) :)
The boot log thing is empty. :\

---

### Post by TheForumTroll on 2009-11-03
Hmm yes I see. It seems this is an old bug in Ubuntu. Everyone and his mother says to use the dmesg log but it (at least on myc PC's) doesn't log shutdown.

---

### Post by batterybaby on 2009-11-03
it seems that your original setting about the laptop needs to be corrected.times of "enforced turn off"is harmful to the computer.therefore donnot try that again.

---

### Post by tryingtoboot on 2009-11-03
I scrapped Ubuntu and tried Linux Mint 8.10 which doesn't have this problem.

---

### Post by kja999 on 2009-11-03
I am now getting this error in 9.10 though .. never had it before.
There is a really old bug open for it : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/44008](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/44008)

---

