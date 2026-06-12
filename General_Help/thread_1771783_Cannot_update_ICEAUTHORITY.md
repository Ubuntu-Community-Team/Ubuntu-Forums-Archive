---
title: "Cannot update ICEAUTHORITY"
date: 2011-05-30
forum: General Help
---

### Post by 9000cse on 2011-05-30
Hi all, Just started my system up after an hour of being shut down. All shut down the way it should by the way.
On booting up, I got a msg saying Cannot update iceauthority   /home/..../.iceauthority
Check in the help files and nothig their. So, any body got any ideas on what this is???

Cheers

Andy

---

### Post by linuxinstalledfromhdd on 2011-05-30
Did you select to have the home folder encrypted during the installation process?

---

### Post by hawthornso23 on 2011-05-30
From your home directory run 

```
ls -l .ICEauthority
```

See who owns it. It should be ... yourname yourname ... if you see ... root root ... then that is your problem right there. This is not uncommon and is caused by running GUI programs as root using sudo instead of gksudo.

The fix is to run

```
sudo chown yourname:yourname .ICEauthority
```

obviously with "yourname" replaced by your real user name. Then reboot.

---

### Post by 9000cse on 2011-05-31
Hi, and thanks for getting back to me. 
No, NO encrypted used. The system has been up and running for some time now with no problems. This just seemed to happen.
I'll try the above and and get back to you with a result.
Cheers
Andy

---

### Post by garvinrick4 on 2011-05-31
most likely after you try to give password at log-in if used:
hit ctrl/alt/f1 and log in:
cd /home
```
sudo chown -R rick:rick /home
```
Use your own user name.
```
sudo reboot
```

---

### Post by 9000cse on 2011-05-31
Hi Guys, problem seems to be resolved. using

sudo chown yourname:yourname .ICEauthority
job done. Solved.

OK, How do I make this as Solved ?

---

