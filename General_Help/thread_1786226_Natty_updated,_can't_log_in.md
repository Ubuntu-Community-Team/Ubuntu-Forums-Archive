---
title: "Natty updated, can't log in"
date: 2011-06-19
forum: General Help
---

### Post by whalogreg on 2011-06-19
I recently ran the update manager on my Natty box and the next time I restarted, I made it to the login screen. When I enter my password and try logging in, the screen flickers and plays about a quarter second of the 'Ubuntu login music' and takes me back to the login screen. I have not recently installed anything, I have only updated my system. I've tried logging in under Ubuntu, Ubuntu classic, recovery console, and safe mode, all having the same result. Any ideas?

---

### Post by Dorsenstein on 2011-06-19
Are you dual booting or anything like that? Also, from grub, you might want to try booting in to text only and then manually starting gdm. I believe I've had a very similar problem before and it was graphics related. You could try using KDE and see if it's a problem with GNOME or vice versa.

---

### Post by jerrrys on 2011-06-19
try resetting your password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by whalogreg on 2011-06-19
> **Dorsenstein said:**
> Are you dual booting or anything like that? Also, from grub, you might want to try booting in to text only and then manually starting gdm. I believe I've had a very similar problem before and it was graphics related. You could try using KDE and see if it's a problem with GNOME or vice versa.

I am dual booting with Windows 7. As you said, from grub, I booted into text only and ran GDM. From there I got the same result, always being brought back to the login screen. Choosing a KDE session also gives me the same result..

---

### Post by whalogreg on 2011-06-19
I also tried the fail safe x from the recovery menu, and I didn't even get to GDM, it simply took me back to the recovery menu.

---

### Post by whalogreg on 2011-06-19
> **jerrrys said:**
> try resetting your password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I don't know if this will help. I am entering the correct password. I know this because when I enter the password correctly my system attempts to log in (screen flickers, a small portion of the system login music plays), and when I intentionally enter a wrong password, it says 'Authentication failure'..

---

### Post by jerrrys on 2011-06-19
too bad

---

### Post by jerrrys on 2011-06-19
try a

sudo dpkg --configure -a

can't hurt

---

### Post by whalogreg on 2011-06-19
> **jerrrys said:**
> too bad

So I tried updating my password as you said, and when I tried to log in i got a bunch of error messages, one after another..

"Could not update ICEauthority file /home/gregory/.ICEauthority"

"There is a problem with the configuration server.
 (/usr/lib/libgconfig2-4/gconf-sanity-check-2 exited with status 256)"

"Nautilus could not create the following required folders: /home/gregory/Desktop, /home/gregory/.nautilus. Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them."

"GConf error: No database available to save your configuration: Unable to store a value at key '/apps/nautilus/preferences/clutter_test', as the configuration server has no writable databases."

And then my system just hangs at a screen with nothing but the GDM wallpaper and my mouse..

---

### Post by Dorsenstein on 2011-06-19
Alright. Try this:

Boot into text-only mode, login, then type:
```
cd /etc/gdm/
```There's a file in there called gdm.conf
copy it and name it something like gdmbackup
delete gdm.conf and then start gdm and see what happens.

---

### Post by whalogreg on 2011-06-19
> **Dorsenstein said:**
> Alright. Try this:

Boot into text-only mode, login, then type:
```
cd /etc/gdm/
```There's a file in there called gdm.conf
copy it and name it something like gdmbackup
delete gdm.conf and then start gdm and see what happens.

In /etc/gdm/ there is no gdm.conf

there is 
custom.conf
failsafeBlacklist
failsafeXinit
failsafeXServer
gdm.schemas
Init
PostLogin
PostSession
PreSession
Xsession

That is all that is listed.

---

### Post by whalogreg on 2011-06-19
Thinking I may just do a fresh install..

---

### Post by jerrrys on 2011-06-19
if you have nothing to loose on this install do a 

sudo dpkg --reconfigure gdm

that should reset it

---

