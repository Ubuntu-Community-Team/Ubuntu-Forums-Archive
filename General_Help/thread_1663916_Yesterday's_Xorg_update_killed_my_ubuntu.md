---
title: "Yesterday's Xorg update killed my ubuntu"
date: 2011-01-10
forum: General Help
---

### Post by marin123 on 2011-01-10
I did an update yesterday and shut down my laptop and this morning my laptop wont boot. I pass grub normally and plymouth too, but then i just get blank screen and nothing happens. Updates included xorg so i guess it screwed everything up. Is there any soulution except reinstallation? I can get to tty, because if i could i would run apt-get upgrade again...
Thanks!

---

### Post by marin123 on 2011-01-10
bump!

---

### Post by kenzaoe on 2011-01-10
same here.

i'm assuming xorg goes at 100%, cuz the fans are getting super loud, i can't login via ssh

---

### Post by kenzaoe on 2011-01-10
it's working now.

1. at the grub screen i booted with the "single" option
2. i updated to the newest kernel 2.6.35-24 (i was at 2.6.35-23)
3. i've reinstalled xserver
```

sudo aptitude reinstall xserver-xorg xserver-common

```
4. reboot 
5. boot with "single" option
6. installed newest ATI drivers
7. reboot

hope it helps someone. (btw i'm running 10.10)

---

### Post by marin123 on 2011-01-10
what do you mean, "boot with single option"?
recovery?

---

### Post by ShadowWraith on 2011-01-10
I haven't had this issue, but if it really is a problem with xorg,
then you can probably get into the console with ctrl-alt-f1.

---

### Post by marin123 on 2011-01-10
no, i tried that. after plymouth goes away its just blank screen and i have to force shutdown my laptop (i have to hold the power button for a few seconds).

---

### Post by kenzaoe on 2011-01-11
by single option i meant, boot into single user mode:
[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

if you have grub 2 the key commands are different (i think ctrl-x to boot instead of "b") but the instructions are the same, just add the word "single" at the end of the line starting with "kernel"

ctrl-alt-f1 didn't work for me either...

---

### Post by marin123 on 2011-01-11
thank you kenzaoe!! :)

if someone needs this, you have to select kernel at grub2 menu, press e to edit and at the end of line that starts with "linux" remove quiet and splash parts and add "single" : linux... on uuid... ...ro single, and then press ctrl + x and you can choose terminal with networking or failsafeX, whichever you want and then i reinstalled graphics drivers, disabled docky and compiz and set metacity as default compositor (i dont know if this all helped, but its working now) and rebooted.

marking it as solved...

---

### Post by AVeryLongNickname on 2011-01-13
Thank you! this worked perfectly!

---

