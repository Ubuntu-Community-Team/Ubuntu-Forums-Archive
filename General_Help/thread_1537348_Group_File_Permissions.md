---
title: "Group File Permissions"
date: 2010-07-23
forum: General Help
---

### Post by TrevorBradley on 2010-07-23
OK, I feel really dumb asking this, but it must be too early in the morning and I'm stumped.  I'm attempting to fix the permissions on my server so that a group has access to certain files but new users don't.  I've created a group called home, added myself to it, and then ran chmod o-rwx... and then I can no longer change directory to these folders!

In this instance "dale" is another user (not me) but we're both in the "home" group:

trevor@pergamon:/mnt/bigdisk$ ls -l . | grep audio
drwxrwx--- 15 dale   home  4096 2010-07-18 12:52 audio
trevor@pergamon:/mnt/bigdisk$ id trevor
uid=1000(trevor) gid=1000(trevor) groups=1000(trevor),4(adm),20(dialout),24(cdrom),46(plugdev),110(lpadmin),119(admin),124(sambashare),129(mythtv),**1008(home)**
trevor@pergamon:/mnt/bigdisk$ cd audio/
bash: cd: audio/: Permission denied


I've tried googling for a solution but all I can seem to find is basic chmod tutorials.  I thought I knew how to do this.  What am I doing wrong?

---

### Post by Vaphell on 2010-07-23
maybe permissions the bigdisk is mounted with prevent that?

---

### Post by Bachstelze on 2010-07-23
Have you logged out and back in?

---

### Post by TrevorBradley on 2010-07-23
> **Vaphell said:**
> maybe permissions the bigdisk is mounted with prevent that?

I've tried the same with a text file in my /home directory (off the / mount), same result.

And I have tried logging out and back in again.

---

### Post by Vaphell on 2010-07-23
magic
maybe try with a different group?

---

### Post by TrevorBradley on 2010-07-23
Waaait a minute.. something's up:

trevor@pergamon:~$ id
uid=1000(trevor) gid=1000(trevor) groups=4(adm),20(dialout),24(cdrom),46(plugdev),110(lpadmin),119(admin),124(sambashare),129(mythtv),1000(trevor)

trevor@pergamon:~$ id trevor
uid=1000(trevor) gid=1000(trevor) groups=1000(trevor),4(adm),20(dialout),24(cdrom),46(plugdev),110(lpadmin),119(admin),124(sambashare),129(mythtv),1008(home)

"home" is in "id trevor" but not "id".. that's almost certainly the problem.

Would logging out/in require an actual logout from gnome, or just a new bash or terminal shell?

---

### Post by TrevorBradley on 2010-07-23
Well, apparently the solution is to physically log out of gnome and log back in again, that or ssh into the system... starting a new terminal window or running bash don't seem to fix the group membership... :(

---

### Post by AlphaLexman on 2010-07-23
The command:
```
groups
```
Will report what groups the current user is in.

---

