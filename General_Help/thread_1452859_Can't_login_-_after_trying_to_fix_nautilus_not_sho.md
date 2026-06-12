---
title: "Can't login - after trying to fix nautilus not showing desktop"
date: 2010-04-12
forum: General Help
---

### Post by bryanosaurus on 2010-04-12
I am using Ubuntu 9.10, and is the only OS installed on my system. 
Yesterday, my desktop stopped working - no right-click function / display of icons. My wallpaper was still intact. 

I tried a few of the solutions proposed on this thread
[http://ubuntuforums.org/showthread.php?t=1331247](http://ubuntuforums.org/showthread.php?t=1331247)

The last thing I did was pressed ALT + F2 and executed "gksudo nautilus". This fixed my desktop for the time being, but wasn't showing the correct icons/wallpaper.

The real problem started when I restarted. I get the normal login screen, and when I enter my info, it just restarts back to the login screen. I know I am entering the correct information, my caps lock isn't on etc. If I enter my password incorrectly it doesn't reload, it just acts normal and says the pw was wrong. Only when I enter my info correctly does it go to a black screen really quick, then come back to the boot screen. 

I am at work right now, but will be checking this thread again later tonight. Please help, I am locked out of my computer which I desperately need to log in to!

Thanks in advance for any help!

---

### Post by bryanosaurus on 2010-04-12
bump.

---

### Post by doas777 on 2010-04-12
reboot and select "Recovery Mode" for your current kernel (if recovery mode is not displayed hit escape to enter the grub list when prompted).

then run 
```

ls -l /home/<username>

```

your output shoudl look a lot like this:
```

karmic:~$ ls -al /home/karmic
total 40
drwxr-xr-x 6 karmic karmic 4096 2010-03-22 14:31 Desktop
drwxr-xr-x 2 karmic karmic 4096 2010-03-23 08:22 Documents
drwxr-xr-x 4 karmic karmic 4096 2010-03-22 08:31 Downloads
drwxr-xr-x 2 karmic karmic 4096 2010-03-23 08:22 Music
drwxr-xr-x 2 karmic karmic 4096 2010-03-23 08:22 Pictures
drwxr-xr-x 2 karmic karmic 4096 2010-03-23 08:22 Public
drwxr-xr-x 2 karmic karmic 4096 2010-03-23 08:22 Templates
drwxr-xr-x 2 karmic karmic 4096 2010-03-23 08:22 Videos
...

```

note that all the folders/files are owned by the user 'karmic' and the permissiosn all the user full rights.

do your files look much the same?

---

### Post by bryanosaurus on 2010-04-12
No it does not look like that - they are formatted like 

permissions bryan bryan size date file

obviously, bryan is my user name

---

### Post by doas777 on 2010-04-13
> **bryanosaurus said:**
> No it does not look like that - they are formatted like 

permissions bryan bryan size date file

obviously, bryan is my user name

what are the permissions?

---

