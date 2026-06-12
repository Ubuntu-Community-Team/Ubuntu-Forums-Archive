---
title: "chmod help?"
date: 2009-07-18
forum: General Help
---

### Post by elcisitiak on 2009-07-18
Okay, perhaps I'm too stupid to own a computer. I've read the tutorials and man pages and everything but I'm still confused. 

I made my brother a user account on my computer with adduser, but now I'm lost. I want to make my folders/files private (preferably with one shared folder or something, or if I can JUST share my music folder or something like that). But whenever I use chmod I seem to screw something up! I either block everyone (myself included) off from it, or it remains available to everyone. I guess I need someone to hold my hand and spoon feed me commands. What should I do to get "jacob" to not be able to access "rel"?

---

### Post by michy99 on 2009-07-18
chmod 700 /home/rel

---

### Post by elcisitiak on 2009-07-18
ls -l still seems to show that everyone else has access to everything! What did I do wrong?

---

### Post by geoffjay on 2009-07-18
you might want to post the output of ls -al /home

---

### Post by moster on 2009-07-19
```
sudo chmod a=rwx -R FolderName
```

It mean that all users can ReadWriteExecute in FolderName including subdirectories.

a=all users
u=user (you)
g=group

Just enter chmod help in google, it will find something...

---

### Post by jerome1232 on 2009-07-19
> **geoffjay said:**
> you might want to post the output of ls -al /home

^ quoted for emphasis, seeing what the current situation is helps us know what's up.

---

### Post by elcisitiak on 2009-07-19
Nevermind, it works now. Misread something. Sorry!

---

### Post by c0mput3r_n3rD on 2009-07-19
What you need to know before you use chmod:

Linux sets up file permissions in this way.
----------
ex:
drwxrwxrwx

The first "-" says whether it's a Directory or not.  The next 3 are the Read, Write, and eXecute permissions for you.  The next 3 are Read Write and eXecute permissions for the group you are apart of.  The next three are for every one else on the system.

If say your home directory "~" is said to drwxr-xr-x, that would mean that you can Read Write and eXecute directories/files in your home directory; the users in your group and Read your directories (use the "ls" command, and execute any programs or scripts; and same for every one else (if it is a directory you can change to that directory with eXecute permissoins).

With that understanding, we get the actual command.

chmod is the command, with a option, either adding are taking away permission for user group or other, and what file it is for.
Ex:
```

chmod o+rx userName

```
That will allow any one who logs into the system able to see the files in you ~ directory, and execute any porgrams or scripts.  This is only for that directory how ever; any sub-directory would have it's own permissions. 

So say for me, if I want my other users to be able to access my Music directory, I would do something like this
```

chmod o+rx Music
chmod o+rx ~/Music/*.mp3

```

The last command uses the wild card, which means anyhting with a .mp3 extension will give permissoin to any user to read and execute.

The three option you have, are u, for user, g for group, and o for other, a plus or mins, and either Read Write or eXecute permissions.

Hopefully that will help you out :D

---

### Post by c0mput3r_n3rD on 2009-07-19
> **elcisitiak said:**
> Nevermind, it works now. Misread something. Sorry!


O man I typed all of that for nothing!?? lol

---

### Post by DeMus on 2009-07-19
> **c0mput3r_n3rD said:**
> O man I typed all of that for nothing!?? lol

No, there are plenty of others who will benefit from your excellent explanation. Thank you.

---

### Post by c0mput3r_n3rD on 2009-07-19
Haha as long as my tired fingers don't feel like their energy went to waste :D

---

### Post by bodhi.zazen on 2009-07-19
[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by moster on 2009-07-20
> **c0mput3r_n3rD said:**
> O man I typed all of that for nothing!?? lol

HAHAHA, NO, you build up my ABS by 15% :D

---

