---
title: "Workspace Switcher 2.28.0 does not work"
date: 2009-12-31
forum: General Help
---

### Post by bball2601 on 2009-12-31
Hi

I recently installed ubuntu 9.10 and so far i really like it.  However this is my first linux os so im still learning and getting used to it.  

Initially, Workspace Switcher 2.28.0 was working perfectly, but now I am stuck on one workspace.  When i click on the box for the other workspace nothing happens and i cannot drag windows between workspaces from the boxes.   

Is there anything i do to fix this? Can i uninstall and reinstall it?

Im lost and appreciate any help because i thought this was a pretty cool app.

Thanks in advance

---

### Post by harmck on 2010-01-08
Hi, 

Likewise all of a sudden my Workspace Switcher is not working. I've had it set on 4 Cols since I installed Gutsy first. 

Recently however my Compiz has been acting up, occasionally my Visual Setting would revert to none, and it would wipe my Compiz Settings. So I had to keep enabling all of these. 

Does anyone know what has changed because these worked perfectly for me for the last few years, and even since I upgraded in Oct to Karmic. Only this weekend has there really been any problems. 

It was after all of this I noticed that my Workspace switcher now only has 2 Desktops. 

Anyone have a idea how I might resolve this?

Thanks in advance, 

Har

---

### Post by harmck on 2010-01-08
> **harmck said:**
> Hi, 

Likewise all of a sudden my Workspace Switcher is not working. I've had it set on 4 Cols since I installed Gutsy first. 

Recently however my Compiz has been acting up, occasionally my Visual Setting would revert to none, and it would wipe my Compiz Settings. So I had to keep enabling all of these. 

Does anyone know what has changed because these worked perfectly for me for the last few years, and even since I upgraded in Oct to Karmic. Only this weekend has there really been any problems. 

It was after all of this I noticed that my Workspace switcher now only has 2 Desktops. 

Anyone have a idea how I might resolve this?

Thanks in advance, 

Har

So it turns out I had changed some Compiz preferences to try and resolve the compiz crash problem, in the Preferences I changed the backend config from 'GConf Configuration Backend' to 'Flat-file Configuration Backend'. On reversing this change the Workspace Switcher is now working again.

---

### Post by hellocatfood on 2010-01-24
If there's anyone else with this problem it may be a good idea to look at this bug report [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/423493](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/423493)

---

### Post by JohnBUK on 2010-02-04
> **harmck said:**
> So it turns out I had changed some Compiz preferences to try and resolve the compiz crash problem, in the Preferences I changed the backend config from 'GConf Configuration Backend' to 'Flat-file Configuration Backend'. On reversing this change the Workspace Switcher is now working again.
harmck - thanks ever so much for that. My Workspace switch stopped working and I did as you suggested and all's fine now!
Ubuntu 9.10.

---

### Post by pallabbasu1234 on 2010-04-21
The same bug is affecting me also. Would somebody please put a detailed solution?

---

### Post by hellocatfood on 2010-04-21
This bug is apparently fixed upstream and there appears to be a patch available for this here [https://bugzilla.gnome.org/show_bug.cgi?id=594113](https://bugzilla.gnome.org/show_bug.cgi?id=594113) I don't know how to apply this patch, but do let us know if it works

---

