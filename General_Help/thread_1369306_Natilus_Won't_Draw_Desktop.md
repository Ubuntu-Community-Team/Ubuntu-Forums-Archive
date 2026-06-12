---
title: "Natilus Won't Draw Desktop"
date: 2009-12-31
forum: General Help
---

### Post by I Forgot My Username on 2009-12-31
I'm posting from Windows because when logged(auto login) in to Ubuntu I get a few messages ranging from Nvidia's kernel isn't loading to natilus doesn't have rights to create "/home/(username)/Desktop/.natilus".  When it does finally get to the desktop all I see is the default pic for the background, no menus or icons.

ANY help would be GREATLY appreciated.

---

### Post by I Forgot My Username on 2009-12-31
Could it be that I put myself in the group, "root"?  If so, how do I un-root myself from commandline because that's all that working right now?

---

### Post by Leppie on 2009-12-31
> **I Forgot My Username said:**
> Could it be that I put myself in the group, "root"?  If so, how do I un-root myself from commandline because that's all that working right now?

you can check your direct group memberships like this:
```
$cat /etc/group | grep $(whoami)
```

remove yourself from a group like this:
```
$sudo deluser $(whoami) <group-to-be-removed-from>
```

---

### Post by I Forgot My Username on 2009-12-31
Thanks, I'll try that, just waiting to see if I get any other suggestions before I take the time to restart.  Could me being in the "root" group cause natilus to not be able to write to my user file?  That is the only thing I changed last time I logged in except for changing to an auto login.

For those who don't know, natilus is the thingy that animates the desktop.  I think.

---

### Post by Leppie on 2009-12-31
AFAIK nautilus is to gnome kind of like what explorer is to windows (show the desktop, browse folders, etc.)

i am not sure what you mean by "root" group? what did you exactly do to put yourself in this group?

---

### Post by I Forgot My Username on 2009-12-31
This is embarrasing to admit, but all I had to do to fix it was cancel the automatic login and manually(type my pw) login as myself.  Thanks for trying, I can see why you didn't think of a solution, seeing as it's about the stupidest problem ever:).

---

### Post by Leppie on 2009-12-31
> **I Forgot My Username said:**
> This is embarrasing to admit, but all I had to do to fix it was cancel the automatic login and manually(type my pw) login as myself.  Thanks for trying, I can see why you didn't think of a solution, seeing as it's about the stupidest problem ever:).

did you automatically login as another user? that would prevent you from accessing your files.

well, glad it's working again.

---

