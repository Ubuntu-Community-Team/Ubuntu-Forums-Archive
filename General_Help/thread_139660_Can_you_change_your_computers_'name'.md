---
title: "Can you change your computers 'name'?"
date: 2006-03-04
forum: General Help
---

### Post by mztriz on 2006-03-04
Okay, when I open terminal it says mztriz@ubuntu2:

I know this is a bit useless but, I want to change it from 'ubuntu2' to something else is this possible?

---

### Post by jfcous on 2006-03-04
I tried but don't do the same thing I did.  My trying follows.

I wanted to change my computer system's name.  It was linksys (I don't know how that happened) and I wanted to change it to zendo (I do Zen meditation).

I did a search for linksys and found a file called "hostname" which only contained the work "linksys".  I used vi to edit it and changed it to "zendo".  

Upon booting the next day, after logging in I saw the following message. 

"Could not look up the internet address for zendo.  this will prevent GNOME from operating correctly.  It may be possible to correct the problem by adding zendo to the file etc/hosts." 

When I go to a terminal session and did "sodo su", I see the following message.  

"sudo: unable to lookup Zendo via gethostbyname()"

I cannot get back into the "hostname" file because I am not root.  

I can reinstall but must be an easier way to correct this.  Two questions.

- How can I get hostname to accept an edit so I can correct my error.
- How can I change my computer name. 

John

---

### Post by arctic on 2006-03-04
[http://www.cpqlinux.com/hostname.html](http://www.cpqlinux.com/hostname.html)

---

### Post by mztriz on 2006-03-04
[QUOTE=arctic][http://www.cpqlinux.com/hostname.html](http://www.cpqlinux.com/hostname.html)[/QUOTE]
Cool, thanks arctic.

---

### Post by wylfing on 2006-03-04
Also, it is unnecessary to edit the config files directly for this. In Gnome, choose System > Administration > Networking and then click on the General tab.

---

### Post by simon_is_learning on 2006-03-04
I read the link - but still i managed to screw it up.

And now Im in the same situation as jfcous

help would be appriciated, becouse as it is now - I can't do anything as root.

---

### Post by simon_is_learning on 2006-03-04
jfcous:
I solved it by rebooting into recovery mode - change it back to what it was before. then rebooting into normal mode.

---

### Post by jfcous on 2006-03-04
mttriz,
Thanks.  Now I know what recovery is good for.  We'll get it right one of these days.

jfcous

---

