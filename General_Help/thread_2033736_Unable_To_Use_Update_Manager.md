---
title: "Unable To Use Update Manager?"
date: 2012-07-26
forum: General Help
---

### Post by blacksilvershewolf on 2012-07-26
Can't use Update Manager gives me these messages?

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

and....

An error occurred

The following details are provided:
E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory

---

### Post by dino99 on 2012-07-26
sudo apt-get update

this work better :P (but close update-manager first)

---

### Post by blacksilvershewolf on 2012-07-27
None of the commands work and I even looked in the Ubuntu book I have, I think I'm screwed :(

---

### Post by 2F4U on 2012-07-27
There is probably only a problem with one of the repositories and it may be a problem with the mirror you are using. Have you already tried to use another mirror?

---

### Post by plucky on 2012-07-27
> **blacksilvershewolf said:**
> None of the commands work and I even looked in the Ubuntu book I have, I think I'm screwed :(

That error is caused by having more than one package manager open at the same time,or a package manager has taken over the lock file and not released it when it closed.

1) Reboot, then run the **Update Manager** and see if the problem still occurs.

2) If you still have the problem,then you should try deleting the lock file with ```
sudo rm /var/lib/apt/lists/lock
``` and then try running the **Update Manager** again.

Good Luck

---

### Post by blacksilvershewolf on 2012-07-31
> **2F4U said:**
> There is probably only a problem with one of the repositories and it may be a problem with the mirror you are using. Have you already tried to use another mirror?

I have no idea what a mirror is *sigh* I'm still a newbie :(

I will try the unlock thingy though and see what happens :)

---

