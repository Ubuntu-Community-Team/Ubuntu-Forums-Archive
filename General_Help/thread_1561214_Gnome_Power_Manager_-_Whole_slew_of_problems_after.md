---
title: "Gnome Power Manager - Whole slew of problems after update."
date: 2010-08-25
forum: General Help
---

### Post by Weidbrewer on 2010-08-25
I am running 10.04, and just ran an update.  I was watching TV while they were running in the background (Via Myth) when things went haywire.  
First, I received a pop-up telling me that "The volume 'Filesystem root' has only 247MB left."  Not thinking much of it, I emptied my trash.  Then Myth crashed and I couldn't access the backend.

MythTV has always been wonky, so I did a soft reboot.  When the login screen came up, it told me that "config defaults for Gnome Power Manager have not been installed correctly," etc.  I checked my 8.10 partition, and everything is working there, so I knew it wasn't hardware.

I poked around the forums and tried a few suggestions:

```
sudo apt-get remove gnome-power-manager --purge
```
Followed by
```
sudo apt-get install gnome-power-manager
```

This followed by a 'sudo reboot' did not fix the problem. 

```
sudo dpgk-reconfigure gnome-power-manager
```

I *think* that's the right syntax. At anywho, it was typed in from another forum post, and terminal ran it.  Again, no dice.

Finally, I followed a suggestion to just uninstall it all together.  This allowed me to boot into my desktop, but MythTV still won't come up, and now the diskspace error says that I only have 52.3 MB of space left.


Any ideas out there?

---

### Post by Weidbrewer on 2010-08-26
Disturbingly, the more research I've done on this, the more the answers have come back to "reformat and deal with it."

I hope that there is another solution - both to save the hassle of a fresh install, and to find out of this issue is avoidable or can strike with any update.

---

### Post by Weidbrewer on 2010-08-31
I guess I should update this - before I went to reinstall everything, I reinstalled the manager and did another command line update.  Although it didn't do anything the first time, it worked this time.  Whatever the problem was, it fixed it.

---

