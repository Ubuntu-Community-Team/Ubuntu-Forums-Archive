---
title: "ubuntu 10.04 freezes on startup screen"
date: 2010-07-20
forum: General Help
---

### Post by vengiss on 2010-07-20
Hi, I've been using 10.04 for a while now with no problems but for some reason it started freezing on the splash screen, 2 of my keyboards lights start blinking and thats it, I've tried with recovery mode and no luck either. The thing is I don't remember doing anything wrong..

Can anyone help me?? Thanks in advance!

---

### Post by dcstar on 2010-07-21
> **vengiss said:**
> Hi, I've been using 10.04 for a while now with no problems but for some reason it started freezing on the splash screen, 2 of my keyboards lights start blinking and thats it, I've tried with recovery mode and no luck either. The thing is I don't remember doing anything wrong..

Can anyone help me?? Thanks in advance!

Boot off a previous kernel and see it that loads.

---

### Post by gognos on 2010-07-21
i have had this problem no matter what kernel used

here is a list of different bugs that have occurred since using 10.04 

Start up goes to terminal type log in instead of gui 

Or the keyboard wont work when trying to enter user name password on start up.

Or mouse pointer on start up start bouncing all over the place and cant be controlled 
This may take several reboots but eventually things work out.

Sometimes after reboot problems continued so i left off for a few minutes then retried which seems to fix the problem. Turning my computer on using 10.04 is like a lucky dip. You never know what you are about to be served.

When using a wireless 3g modem it will sometimes disconnect me and allow no more reconnection's until reboot. 10.04 just keeps on reminding me of windows restarts. With every update i hope the problems cease.Still no fix. 10.04 = stability gone wrong im ditching 10.04 and going back to 9.04 as 9.10 made my wireless useless.

---

### Post by GenePayne on 2010-07-21
Try looking in the syslog file
```

less /var/log/syslog
```

for errors. If you can get to a shell, that is.

---

