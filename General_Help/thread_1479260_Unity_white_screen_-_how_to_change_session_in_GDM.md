---
title: "Unity white screen - how to change session in GDM?"
date: 2010-05-10
forum: General Help
---

### Post by Bastanteroma on 2010-05-10
Installed Unity from the ppa, restarted the session and got a blank screen.

Now I can't figure out how to get back to GDM and reselect Gnome as my default session.

---

### Post by ElementoQuinto on 2010-05-10
If you still have the white screen then CTRL+ALT+1 log in then

sudo /etc/init.d/gdm restart

When on login screen select your account and select "Gnome" in the session menu below

---

### Post by Shadal on 2010-05-10
I get this too, my screen is black however.
The welcome sound and password dialog for network keys displays, but that's all I get...

I tried restarting gdm as ElementoQuinto pointed out, however the login screen for me is not displayed, I'm just brought back to the same black screen I started at. I think this is because in my admin settings I had it set to auto-login without displaying the login screen.

ElementoQuinto, can I restart gdm in a similar way, forcing it to display the login screen?

---

### Post by Bastanteroma on 2010-05-10
Thanks for the tip, ElementoQuinto. I'm sure it would work, and it's simpler than what I did, which was to boot from a usb stick and edit my gdm conf file to disable autologin.

---

### Post by DavidOC on 2010-05-10
I had the same problem.  Mine would automatically login into unity which was just a white screen.  I was able to get to the login screen by modifying the custom.conf file in /etc/gdm with Nano and rebooting.

---

### Post by Shadal on 2010-05-10
Thank you DavidOC!
--that worked ;-)

...I think Unity needs a bit more improvement yet-

---

### Post by DavidOC on 2010-05-11
I've checked on google and it seems that the ricotz gnome-shell ppa is causing this to happen.

I removed gnome-shell, ricotz ppa and unity and re-installed unity but still no luck.

---

### Post by valorin on 2010-05-11
You need to remove 'mutter' as well, as the version supplied by Unity is different to the version supplied via ricotz.

My method for getting Unity to work was:
```
1. Disabled my PPA for gnome-shell via 'Software Sources'
2. sudo apt-get remove gnome-shell unity mutter
3. sudo apt-get install unity
```

I hope that helps :)

---

### Post by CRIMPS on 2010-05-18
> **DavidOC said:**
> I had the same problem.  Mine would automatically login into unity which was just a white screen.  I was able to get to the login screen by modifying the custom.conf file in /etc/gdm with Nano and rebooting.

Similar fix for me.  I used an Ubuntu 9.10 LiveCD to mount the hard disk.  Then, I browsed to /etc/gdm.  I opened custom.conf and change the line:
```

[daemon]
DefaultSession=unity

```

to 

```

[daemon]
DefaultSession=gnome

```

Saved and rebooted.

---

