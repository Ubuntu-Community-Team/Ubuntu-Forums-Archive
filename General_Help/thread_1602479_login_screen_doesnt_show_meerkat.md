---
title: "login screen doesnt show: meerkat"
date: 2010-10-21
forum: General Help
---

### Post by goTux on 2010-10-21
Hi All,

    I upgraded kubuntu from lucid(10.04) to Meerkat(10.10). problem is login screen doesnt show up on boot. A black screen shows, Ctrl-Alt-F1 doesnt show the tty1. Ctrl-Alt-Backspace doesnt work either, neither does Ctrl-Alt-Del.

    I switch off the computer and reboot into recovery mode, I get the graphical recovery menu, on choosing boot normally, I get the tty1 login prompt.

    Upon logging, I check /var/log/Xorg.0.log.old. There is no error, nvidia 260.xx driver is loaded successfully and all other modules are loaded as well.

    I have done 'apt-get update' to see if there is any update in repository but there isnt. I have searched into the forum but I dont see any related post for this issue. Kindly help me out.

    This is my first post. Forum posts have really helped in me maintaining the kubuntu on my m/c. Thanks tons everybody !!

Cheers,
Amit

    I

---

### Post by whitefeather010 on 2010-10-21
similar problem here, after upgrading to meerkat a few hours ago,  all i get is a log in screen,  i log in and get reverted right back to the log in screen again. 

ctrl alt f1 lets me actually log in, but i can't get x to start from there either.  

anyone found a solution yet?

---

### Post by goTux on 2010-10-21
I actually had this problem while upgrading to lucid. But in Meerkat, the login screen itself doesnt show.
Anybody could help us debug the issue ?

Thanks!

---

