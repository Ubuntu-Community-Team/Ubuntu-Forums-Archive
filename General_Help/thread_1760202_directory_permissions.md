---
title: "directory permissions?"
date: 2011-05-16
forum: General Help
---

### Post by Zeta-K on 2011-05-16
My mind sorta blanked and I set all directories and files on my ubuntu system to rwxr--r-- permissions with root as the owner. what do I need to change to get my system running again? I REALLY don't want to re-install.

---

### Post by wojox on 2011-05-16
There is no undo command. Reinstall is the only way to go. You have directories with sub-directories that are assigned all kinds of different permissions. Lesson learned. ;)

---

### Post by Zeta-K on 2011-05-16
> **wojox said:**
> There is no undo command. Reinstall is the only way to go. You have directories with sub-directories that are assigned all kinds of different permissions. Lesson learned. ;)

I know there's no undo command, I'd like to know which directories I need to switch the permissions to using a separate live boot. I can't reasonably reinstall right now due to dial-up speed internet and no handy ubuntu live boot disks.

---

### Post by mcduck on 2011-05-16
I doubt you could even find any list of all the files and directories and what are the correct ownerships & permissions for them. Even for the default setup, with no additional software, that would be quite a huge list (and lots of work to do to apply them to your files)

Even with a dial-up, downloading a new disk and making a fresh install would quite likely take less time than trying to repair the damage by hand.

---

### Post by bodhi.zazen on 2011-05-16
Reinstall is the fastest solution.

Otherwise , use the live CD as a template

```
ls -lA /
```

Them descend into those directories and set ownership / permissions directory by directory, file by file ...

---

