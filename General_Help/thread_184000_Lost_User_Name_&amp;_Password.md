---
title: "Lost User Name &amp; Password"
date: 2006-05-29
forum: General Help
---

### Post by mano on 2006-05-29
Dear All,

can some one please Help?
recently a freind installed UBUNTU on one of my machines... but then i have lost the user name and password that's needed to log on to this system

can some help in re-setting both?

thanks and look forward to your replies.

mano

---

### Post by xyz on 2006-05-29
You're not alone...good luck!
[http://ubuntuforums.org/showthread.php?t=183782&highlight=user+lost](http://ubuntuforums.org/showthread.php?t=183782&highlight=user+lost)

---

### Post by oli888 on 2006-05-29
Does your friend know the passwords?

And do you have any valuble data stored on your PC. If not, go for a fresh installation.

Sorry I couldn't be much help,

Oli

---

### Post by kanha on 2006-05-29
quite easy..........
on grub bootloader
choose option safe mode
then when a prompt apear type
[COLOR="Red"]passwd USERNAME[/COLOR]
where USERNAME is ur username
type new password8)

---

### Post by tkjacobsen on 2006-05-29
[QUOTE=kanha]quite easy..........
on grub bootloader
choose option safe mode
then when a prompt apear type
[COLOR="Red"]passwd USERNAME[/COLOR]
where USERNAME is ur username
type new password8)[/QUOTE]

(still boot in recovery mode)
First you have to find your username.. look in the /home folder. All users have a folder equal to their name..```
ls /home
```
then set the password as kanha described

---

### Post by mano on 2006-06-01
To All whome helped thank you very much you saved my *** from re-intalling the software.

again thanks a million...
BTW follow the steps given by "tkjacobsen" he's the man with the full solution. thanks mate.

regards
mano

---

