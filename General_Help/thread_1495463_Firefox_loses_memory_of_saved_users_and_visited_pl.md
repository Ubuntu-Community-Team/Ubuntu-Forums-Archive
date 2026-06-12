---
title: "Firefox loses memory of saved users and visited places!"
date: 2010-05-28
forum: General Help
---

### Post by Pontus Ohman on 2010-05-28
Hey folks!

Since Ubuntu become 10.04, Firefox got some big issues with losing it's memory of saved users/passwords and places I've visited earlier. To fix it, I need to close and re-open Firefox and all is fine for a time. But after some time, all stuffs is gone missing again and I need to close and re-open it...

Why isn't Windows users affected with this? Only Ubuntu folks?

Anybody else notice this sickness with Firefox?

---

### Post by dino99 on 2010-05-28
never had this issue or seen over the forums, you need to look at your logs (system admin log viewer) and .xsession-errors into your /home (unhide it with menu)

into synaptic, right click on firefox package to remove/purge it then reinstall it

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo dpkg-reconfigure firefox

are you using firefox from synaptic repo or from a ppa ?
check the plugins installed too

---

### Post by Pontus Ohman on 2010-05-28
> **dino99 said:**
> never had this issue or seen over the forums, you need to look at your logs (system admin log viewer) and .xsession-errors into your /home (unhide it with menu)

into synaptic, right click on firefox package to remove/purge it then reinstall it

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo dpkg-reconfigure firefox

are you using firefox from synaptic repo or from a ppa ?
check the plugins installed too

Using the firefox that was in Ubuntu 10.04 when I first installed it... And I'm not alone here in Sweden having this problem with Firefox and Ubuntu =/ I have posted it on the Swedish Ubuntu forum where peolpe get the same issues like I'm having with Firefox.

---

