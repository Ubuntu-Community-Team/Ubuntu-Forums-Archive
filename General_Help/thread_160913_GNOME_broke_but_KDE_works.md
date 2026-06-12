---
title: "GNOME broke but KDE works"
date: 2006-04-15
forum: General Help
---

### Post by JacksonL on 2006-04-15
I was messing around in KDE (installing various themes and such) and when I logged out and relogged in a GNOME session it wouldn't start GDM. visually, my panels flash every four seconds or so, and then after about a minute the screen just stays brown with my curser on it. the curser is mobile.

---

### Post by trent dillman on 2006-04-15
First, look and see if there's a stray lock file in tmp...should be in /tmp/gconf-<user name>

You could also try deleting any .gnome* folders in your home directory, but this will get rid of any config you had before...

---

### Post by JacksonL on 2006-04-16
I tried both of these and neither one worked =/

---

### Post by JacksonL on 2006-04-16
help

---

### Post by Sutekh on 2006-04-16
Changing themes in KDE, now flashing panels, and maybe that bongo sound repeating itself a couple of times, then just a brown screen?   Sorry to hear you've got this problem too.

Create a new user in KDE and then log into GNOME with that new user, copy all your files and settings from the old user to the new one.

Then just let the old user fade into memory.  

That was the only way I could solve this problem for me.

---

### Post by JacksonL on 2006-04-16
bump because although this worked I would prefer to use my old account and am wondering if any body has an other solution.

---

### Post by Ramses de Norre on 2006-04-16
Copying over all settings and mv /home/old_username /home/current_username should give you almost the same user..

---

### Post by JacksonL on 2006-04-16
the permissions will get all messed up when I do that, won't they?

---

### Post by Ramses de Norre on 2006-04-16
Why would they? Do chown -R new_username /home/new_username.
Maybe using sudo is necessary.

---

### Post by JacksonL on 2006-04-16
fixed for the most part by uninstalling kubuntu-desktop and related programs and deleting the .kde folder in the corrupted user's home for future reference. haven't tried (nor am I going to) installing KDE again.

---

### Post by LxP on 2006-04-18
I also just experienced what the original post describes after installing kubuntu-desktop an hour or so ago.

I re-installed gnome-panel to find that when I log into my GNOME session, the fonts are all ugly and every panel applet failed to load (so I had about 10 error boxes on my screen). I also couldn't start anything as their window would flash on and then disappear.

There's also [this thread]("http://ubuntuforums.org/showthread.php?t=154921") proposing [FONT="Courier New"]rm ~/.gtkrc-2.0[/FONT] which may prove useful (as I'm not particularly keen on rebirthing my home directory and losing all my settings). I'll post back in a minute or two with my success.

**Woohoo:** I'm now back in GNOME and everything is looking good. I might wait a little longer now before trying Kubuntu out.

---

