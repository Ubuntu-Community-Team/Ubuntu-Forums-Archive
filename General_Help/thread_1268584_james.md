---
title: "james"
date: 2009-09-17
forum: General Help
---

### Post by jamescw7 on 2009-09-17
Hi guys.
Pretty new to this but can anyone please answer a question that has no doubt been asked numerous times. We are new to Obuntu and have lost the username. We have successfully changed the password but can not seem to do the same with the username. How do we do this? Alternatively can Obuntu be uninstalled (download version) and if so how so we can start again.
Thanks James.

---

### Post by Waappu on 2009-09-17
Hi,

This is one way, maybe not best:

Start your pc in recovery mode.
Then type ```
nano /etc/passwd
``` you can see all users from that file.

Edit,
Do not edit that file, just try find what is lost username. Then you can reset password for it.

Also one way is create totally new user

---

### Post by bryncoles on 2009-09-17
If I remember correctly, you can reboot, and start in the recovery mode as suggested above. then type ```
ls - la /home
``` That should tell you all the users names on the system. 

then you can type ```
passwd <username>
``` to set a new password (obviously, where it says <username> you would type in 'james' - or whatever the user is who's password you're changing).

---

### Post by wojox on 2009-09-17
You could also try booting into recovery mode. After you get to a shell, enter:

```
ls /home
```

Your username should appear in the results.

---

