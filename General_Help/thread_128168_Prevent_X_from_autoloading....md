---
title: "Prevent X from autoloading..."
date: 2006-02-10
forum: General Help
---

### Post by moTaro on 2006-02-10
on boot, wihtout removing gdm or xorg?

So basicly, I want to boot to terminal console, with all the services up and running, and when I want to jump to X, I would want to do it normaly with startx.

How to do that?

---

### Post by mr_ed on 2006-02-10
In order to do that, you have to disable gdm.

Go to System->Administration->Services, enter your password, and uncheck gdm.  That should do the trick.

---

### Post by moTaro on 2006-02-11
[QUOTE=mr_ed]In order to do that, you have to disable gdm.

Go to System->Administration->Services, enter your password, and uncheck gdm.  That should do the trick.[/QUOTE]

Did that, but on every other reboot, gdm is still on. I probably need to update-rc.d to prevent gdm load permanently, but how ? I need the code.

---

### Post by rsmereka on 2006-02-14
I also had the same issue. I loaded stock breezy from the CD but I did not want to go into X automatically. I first went into services and unchecked gdm but right after the next reboot up comes the !@^#&6 graphical logon screen. Here is what I did:

```
update-rc.d -f gdm remove
``` 
I did this from the root account. Of course, if you are not root, you will have to prefix this command with sudo.

This command removes gdm from the startup and, as a result, the startup goes right into console where you can use startx anytime you want.

Caution: As far as I know, it will be difficult to put gdm back into the startup once it has been removed using this method. A safer but kind of kludgy method of doing the same thing is to rename the /etc/init.d/gdm script to something else (I have done this successfully with other Debian-based Linux's. You may get an error message during the startup but it boots fine and to put gdm back into the startup, just rename it back to gdm.

---

### Post by mr_ed on 2006-02-17
Hm, maybe we should file a bug.

---

### Post by rsmereka on 2006-02-19
I am not sure that behavior is a bug. A good case could be made that unchecking gdm from the services dialog is only valid for that session. If that were the case, there should also be the ability to turn off gdm permantly from the GUI without having to resort to what I had to do.

---

### Post by jchau on 2006-02-21
Unchecking GDM from services works, but u have to do it twice.  The first time, X dies (losing all changes before you can save).  Then you have to startx (from command prompt) and uncheck GDM again.  This time, X won't die. Click OK to save settings.  

That is what I did.

---

