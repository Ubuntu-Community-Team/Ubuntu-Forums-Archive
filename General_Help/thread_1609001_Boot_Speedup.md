---
title: "Boot Speedup"
date: 2010-10-29
forum: General Help
---

### Post by RastaManPower on 2010-10-29
hello guys i found out this guide to speed up boot time. is it safe?
[http://aroundtheweb.info/2010/09/how-to-speed-up-ubuntu-10-10-maverick-meerkat-boot-time-with-profiling/](http://aroundtheweb.info/2010/09/how-to-speed-up-ubuntu-10-10-maverick-meerkat-boot-time-with-profiling/)

---

### Post by Omnomnom on 2010-10-29
If you want, but I wouldn't risk it seeing as the site opened 3 popups and an unwanted flash ad.

---

### Post by RastaManPower on 2010-10-29
sisnt open anything here...haha.. guess i wont play around with boot options haha. i am spending so much time adding apps and tweaking ubuntu. this OS is the best. love how you can do millions of things that windows cant

---

### Post by joshruehlig on 2010-10-29
sudo apt-get install bum
sudo bum
then uncheck services you dont need like bluetooth

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
Some of the same service with some others (wanna be a little more careful here, I always uncheck a bunch of these when I install ubuntu)

My list unchecked (that were checkd by defaut)
apparmor - lose a little security if others use your computer, or rogue app
brltty - a diability thing
dns-clean - I think these next two are for dialup...
pppd-dns -
rsync - can do a bunch of command when combined with cron to run at different times
speech-di - a disability thing

---

### Post by Easy Limits on 2010-10-29
Reported attack site with Firefox.

---

