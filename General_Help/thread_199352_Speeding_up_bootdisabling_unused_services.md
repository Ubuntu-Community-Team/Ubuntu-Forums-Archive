---
title: "Speeding up boot/disabling unused services"
date: 2006-06-18
forum: General Help
---

### Post by fritz_monroe on 2006-06-18
I've been using Ubuntu on my laptop for about 8 months.  Due to school, I have not been able to do a lot of optimizing of my system.  Now I'm able to do some of this and I figured I'd start with something that has been bothering me.

As Ubuntu is booting up, a bunch of messages go scrolling past.  Several of these are questionable about if I need the service it's listing, but some I definately do not need.  For instance, Bluetooth is listed as starting.  Since I don't have any Bluetooth devices, I don't need bluetooth.   I want to stop this from loading.

My understanding is that when I go into the /etc/rc3.d directory, the S files in there are start files that are linked to the actual services they are calling.  If I remove the bluez-util file, it will keep bluetooth from loading up at startup.  Does this sound right?

---

### Post by Ramses de Norre on 2006-06-18
Your default runlevel is 2, not 3. And a safer way to do this is discribed [here]("http://ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf").

---

### Post by deb2006 on 2006-06-18
Before you start manually editing things, just do this:

apt-get install sysv-rc-conf

Once installed you call it from the copmmand line:

sudo sysv-rc-conf

And - voila - you'll get all the services. Some of the names of these services are obvious, some are not. If in doubt, try to google for an explanation.

---

### Post by fritz_monroe on 2006-06-18
Thanks for the input.  I never really thought about having a tool to do this.  Your post about sysv-rc-conf made me  look around a little.  Since I use my laptop mostly for schoolwork and Internet access, I work in a graphical environment most of the time.  I found [Boot Up Manager]("http://www.marzocca.net/linux/bum.html") that is a graphical tool for this.

I wasn't thinking straight, since I come up into X most of the time, I guess I use run level 5.

---

