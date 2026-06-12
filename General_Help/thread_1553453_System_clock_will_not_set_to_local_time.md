---
title: "System clock will not set to local time"
date: 2010-08-15
forum: General Help
---

### Post by lwalper on 2010-08-15
Try as I might I cannot seem to get the system clock to display local time. It looks like it's stuck on GMT. In the System>Administration>Time and Date I have my local time zone set correctly and also set to update automatically with an appropriate time server selected. It still displays my local time +5 hours (I'm central time, USA).

---

### Post by malspa on 2010-08-15
Try taking a look in /etc/default/rcS.

In mine, I have this line:

```
UTC=no
```

If yours is set to "yes," that might be the problem.  If you change it, you might have to reboot for the changes to take effect, I can't remember.

---

### Post by lwalper on 2010-08-15
That fixed it - no restart required.

Thanks a bunch!

For the other noobs on the forum, try this

sudo gedit /etc/default/rcS

After the prompt to enter your password that will open the gedit window where you can change the "yes" to "no".

Save the file and you should be good-to-go.

---

### Post by lwalper on 2010-08-18
Same problem, back to where we started - still displaying UTC. The file /etc/default/rcS is still set to "no". The rcS manual page suggests making changes to the /etc/localtime file. I checked that file - the file exists but it is zero size and contains no data. How can that be? I thought even a file name would require some "size" - a few bytes at least??

The man file also suggests that the /usr/share/zoneinfo file "must  be  readable  early in the boot process." How do I do that?

---

### Post by mcduck on 2010-08-18
Have you simply tried setting the clock applet itself to use that location as your home?

When you click the applet to open the calendar & different locations, do you see a small house icon next to your current location?

---

### Post by lwalper on 2010-08-20
Nope, sorry, don't see that option anywhere. No little house icon.

---

### Post by Vaphell on 2010-08-20
so add your location (button above the world map), as a bonus you'll get info about weather in your area :)

---

