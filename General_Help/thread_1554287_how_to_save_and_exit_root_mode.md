---
title: "how to save and exit root mode"
date: 2010-08-16
forum: General Help
---

### Post by Sodear on 2010-08-16
I've re-set my password in recovery mode: now how do I save my changes and exit to a normal boot up ie to my desktop?  Right now my screen shows "username@Username-desktop:~$"
I've also done a sudo apt-get updates and sudo apt-get desktop for good measure.  But how do I get out?  If I force quit the change is not saved and I cannot log on.

---

### Post by panopticon on 2010-08-16
Try to hit ```
startx
```

---

### Post by sisco311 on 2010-08-16
> **Sodear said:**
> I've re-set my password in recovery mode: now how do I save my changes and exit to a normal boot up ie to my desktop?  Right now my screen shows "username@Username-desktop:~$"
I've also done a sudo apt-get updates and sudo apt-get desktop for good measure.  But how do I get out?  If I force quit the change is not saved and I cannot log on.

Type:
```
exit
```
to return to the recovery menu.

Then select the *resume normal boot* option.

---

### Post by Sodear on 2010-08-16
Typing exit just brought me back to Username-desktop login: so I typed in user name again and then password to be right where I was before.
Typing 'startx' brought a whole new can of worms: "Creating new authority file /home/username/.Xauthority" followed by Fatal Server Error.  Server is already active for display0.  If this server is no longer running remove /tmp/.XO-lock and start again.  Please consult X.Org foundation support at http://wiki/X.org."
Which I will do but am in way over my head.

---

