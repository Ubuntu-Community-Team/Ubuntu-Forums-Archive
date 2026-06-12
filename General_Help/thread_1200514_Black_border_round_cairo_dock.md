---
title: "Black border round cairo dock"
date: 2009-06-30
forum: General Help
---

### Post by de049 on 2009-06-30
Hi all,

I dont know what i've done, but i have a permanent black border around my cairo dock.  I have checked and still have Compiz installed, but not sure if i've mucked up that install.

One other thing i've noticed, my Ubuntu keeps trying to loock for a plugin (not sure for what) every time i reboot the PC.  It never finds one though and so keeps asking me for the password and to acknowledge the plugin search after every reboot.

How can i get these 2 issues fixed, please?

thanks loads!!!!

---

### Post by drs305 on 2009-06-30
> **de049 said:**
> Hi all,

I dont know what i've done, but i have a permanent black border around my cairo dock.  I have checked and still have Compiz installed, but not sure if i've mucked up that install.


For this issue, are you running the conflicting compositors or none at all? 

To turn off metacity;s:
```

gconftool-2 -s -type bool /apps/metacity/general/compositing_manager false

```

If you aren't running a compositor, turn one on. For metacity, you can use either the one above, changing the value to 'true', or:
```

metacity -c

```

---

### Post by de049 on 2009-06-30
Thanks!!!  the Metacity -c command fixed the black border issue.

I noticed the plugin being searched for after each reboot is a multimedia plugin.  No more details available.

It always searches for said plugin but never seems to find one.  Any idea how i can get rid of this check?

thanks

---

### Post by drs305 on 2009-06-30
You don't know the name of the plugin? What multimedia apps do you have autostart? (System, Preferences, Sessions or Startup Applications). You could prevent them from autostarting and then turn each one on via command line to see if you get any messages that way.  

There are various logs you could check in System, Administration, Log File Viewer, including aptitude.log

---

