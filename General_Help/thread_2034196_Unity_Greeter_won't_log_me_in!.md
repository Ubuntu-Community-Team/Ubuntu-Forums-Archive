---
title: "Unity Greeter won't log me in!"
date: 2012-07-28
forum: General Help
---

### Post by linuxuser12345 on 2012-07-28
I cannot seem to get Unity-Greeter to log me in! Every time I put in my password and hit ENTER, it shows a black screen with some white text, but then flips right back to the login screen, not even letting me log in! The black screen doesn't even last long enough for me to comprehend the text... This doesn't happen on any other user account besides mine, and has happened twice before, and both times I had to either make a new user account, or format my hard drive... I don't want to do that again!

I was able to switch my login manager to GDM, but I like LightDM a lot ever since I fixed the slow mouse bug I had. Can someone help me?

---

### Post by spjackson on 2012-07-28
The fact that other users can login implies that it's not the greeter that's at fault but probably your GUI settings. I wouldn't take such radical steps as formatting your hard disk or creating a new account. What you need to do is remove whatever settings are causing the fault.

[B]You should make sure that you have a backup of your home directory. If you don't, then make one now.
[/B]
Are you reasonably confident with using the command line?

You should be able to login under your own account by pressing Ctrl+Alt+F1 together. Ctrl+Alt+F7 will get you back to the GUI.

Alternatively, you could login to the GUI using another account, but then you would probably need to use "sudo" for backing up your files and attempting repairs.

As for the best strategy for restoring to a working state, it depends a bit on where you are starting from.

If you have a good recent backup of all or your home directory, from before the time when it broke, then I'd do this.

[LIST=1]
[*]Backup data files newer than the backup you are going to restore from.
[*]Remove your home directory (or rename it).
[*]Recreate it, making sure that ownership and permissions are correct.
[*]Restore from the working backup.
[*]Restore the new files from step 1.
[/LIST]
If you don't have a good recent working backup, then you need to identify what to remove. There's a good chance that removing the whole of your .gconf directory will fix it, but that may mean you losing some settings that you don't want to lose.

If you'd rather be more selective about removing settings, you could see whether your failed login puts anything significant in .xsession-errors in your home directory.

It's also possible that it isn't .gconf but another directory beginning with a dot, e.g. .compiz

---

### Post by linuxuser12345 on 2012-07-28
Maybe it has something to do with CCSM settings? And even if I log in with the Ctrl+Alt+F1 terminal method, whenever I press Ctrl+Alt+F7, it brings me back to the old session, on the login screen.

---

### Post by spjackson on 2012-07-28
> **linuxuser12345 said:**
> Maybe it has something to do with CCSM settings? And even if I log in with the Ctrl+Alt+F1 terminal method, whenever I press Ctrl+Alt+F7, it brings me back to the old session, on the login screen.
Yes it could be CCSM settings which will be in .gconf or .compiz (as I mentioned before) or in .config (which I hadn't mentioned).

Ctrl+Alt+F7 is meant to bring you back to the same GUI screen that was displayed prior to pressing Ctrl+Alt+F1.

Since you managed to login via Ctrl+Alt+F1, did you find anything of interest in .xsession-errors?

---

### Post by jspike397 on 2012-07-28
Linuxuser12345,
I had this problem too.  Basically you can just use the recovery command prompt (CTRL+ALT+F1) and run a couple of commands.
```
sudo chown yourusername:yourusername .Xauthority
sudo reboot
```

If you would like to see the my post click [HERE]("http://ubuntuforums.org/showthread.php?t=1999552")

Hope it helps.
Jspike397

---

