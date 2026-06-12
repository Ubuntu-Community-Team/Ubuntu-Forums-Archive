---
title: "Ubuntu doesn't complete boot up....makes me use startx"
date: 2011-07-03
forum: General Help
---

### Post by rcayea on 2011-07-03
Hey everyone,


I must have deleted a file or done something wrong because now when I start ubuntu11.04, my startup stalls at the blackscreen where it lists the output of current operations. Mine seems to stall at checking pulseaduio or stall at checking cron. I am not totally certain of the phrases but anyway, my only way to log in is to ctrl+alt F1 and sign in that way followed by startx. 

I copied some exact info down and here is where my computer usually stalls:

Screen says, Starting CUPS printing spooler/server [ok]
Checking battery state...  [ok]
Stopping System V runlevel compatibility [ok]

This is the usual stopping stop for my computer. 




Is there way to fix this?

Thanks,
Randy

---

### Post by rcayea on 2011-07-03
Bump. Any help please?

---

### Post by Dustin2128 on 2011-07-03
make gdm or startx run on startup. [http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)
Just put gdm (login screen) or startx into the script, name it something like bootscript.sh, and make it run at boot. Should do the trick.

---

### Post by rcayea on 2011-07-03
thanks ill give it a try.

---

