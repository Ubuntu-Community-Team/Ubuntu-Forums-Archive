---
title: "Create a launcher in script"
date: 2010-10-21
forum: General Help
---

### Post by BroshizzleDizzle on 2010-10-21
I want to create a launcher that will mount a ssh location.  That's easy enough.  I just create a launcher that does:
```
sshfs user@host:/remotefolder /media/whateveriwant
```

Well... turns out you can't unmount a mount of that kind by the typical methods, I have to use a different method, created a launcher that:
```
fusermount -u /media/whateveriwant
```

Here's where I'm stuck.  I want mount launcher to automatically create the unmount launcher, and the unmount launcher to destroy itself after it is run.

So, instead of having the mount launcher do a command I point it to a script.  How do I make a launcher from shell/bash?  How do I have a file remove itself from shell/bash?

---

### Post by trikster_x on 2010-10-21
you can create a launcher using 
```
/usr/lib/gnome-panel/gnome-panel-add --launcher=/path/to/your_script
```

Unfortunately, there is no way to remove the launcher using the command line, unless you write your own script for that.  And judging by the gnome-panel-add script the devs used to add a launcher, that won't be easy.  It would probably be easier to just type the name of your umount script in the terminal.  Or make an alias for your umount script in .bashrc.

---

### Post by Vaphell on 2010-10-21
does mounting sshfs work different than mounting sftp? i mount sftp and it can be unmounted just fine from nautilus' places or from desktop shortcut that appears

---

### Post by BroshizzleDizzle on 2010-10-24
Well... thank you for your suggestions, but I decided to go for a different approach.  Rather than creating/destroying, I'm just renaming it so it is unhidden/hidden and manually creating the launchers.  Not quite as nice as I'd like, but it works.

---

