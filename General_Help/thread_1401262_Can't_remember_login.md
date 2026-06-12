---
title: "Can't remember login"
date: 2010-02-07
forum: General Help
---

### Post by Mickgriddle on 2010-02-07
Can't remember Ubuntu login and pass and can't get into the terminal, is there anyway I can change it without having to reinstall everything?

---

### Post by x33a on 2010-02-07
This should help:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Mickgriddle on 2010-02-07
Ehh, neither shift nor enter worked. Single-boot on an ibook g3

EDIT: I never do see a GRUB LOADING SCREEN, I see the yaboot screen and a screen asking to boot GNU/linux or CD-rom

---

### Post by cjhabs on 2010-02-07
I haven't tried this but I think this should work:
Boot off a live cd
Mount the root partition
Edit the /etc/passwd and /etc/shadow files and remove the password field for your user
Reboot - hopefully will prompt you for a new password or let you log in with no password

---

### Post by x33a on 2010-02-07
You can try it with a livecd.

[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)

---

### Post by n0dix on 2010-02-07
Are you sure, you don't remember or you want to infringe the system?
i just kidding ;)

---

### Post by Mickgriddle on 2010-02-07
The boot cd I was using was the alternative install cd, which looks sadly, nothing like that. I'm just really confused. It's more like... a blue screen comes up and it just goes from there to ask me what country I am at and stuff like that. I can hit go back somewhere and set-up user and I do and I go back and it's no good.

---

### Post by cjhabs on 2010-02-08
You don;t want to set up the user from the live cd - you want to mount your root filesystem once the live cd is running fix the passwd and shadow files  there, then when you boot off your live installation you should be able to log in.

---

### Post by Mickgriddle on 2010-02-08
Ok, so how do I mount my filesystem without logging?

---

### Post by wojox on 2010-02-08
Did you hold down the Left Shift Key?

---

### Post by Mickgriddle on 2010-02-08
> **wojox said:**
> Did you hold down the Left Shift Key?

Mmhmm... No dice. =(

---

### Post by Leppie on 2010-02-08
> **Mickgriddle said:**
>  a screen asking to boot GNU/linux or CD-rom
press "e" at this screen, append an "s" at the end of the line starting with "linux /vmlinuz" and press CTRL+x to boot into recovery mode.

---

