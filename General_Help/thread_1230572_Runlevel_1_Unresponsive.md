---
title: "Runlevel 1 Unresponsive"
date: 2009-08-03
forum: General Help
---

### Post by MadHatter21 on 2009-08-03
Hello,

I am just beginning with ubuntu and am exploring run-levels right now. I have gone into grub and edited the kernel boot option to boot into single or run-level 1. After booting into the menu screen i cannot scroll anything. Odly though when i type the words go over the first selection in the list. For some reason the scrolling is not working but a odd keyboard input is available.

Looks Like this:
```

Recovery Menu

dpkg       repair broken packages
fsck         file system check
grub        update grub boot loader
**I am writing here** auto repair graphic problems
netroot    drop to root ...

```

---

### Post by sisco311 on 2009-08-03
How did you edit the kernel line?

Btw, Recovery Mode = Single User Mode a.k.a. runlevel 1

---

### Post by MadHatter21 on 2009-08-03
no, went into grub, hit e to edit, went down to kernel, hit e, then typed "Single" at the end and booted into it with b.

---

### Post by sisco311 on 2009-08-03
> **MadHatter21 said:**
> no, went into grub, hit e to edit, went down to kernel, hit e, then typed "Single" at the end and booted into it with b.

You have to delete the splash boot option. It doesn't work so well with Single. Probably a bug.

Or select the second entry (recovery mode = ro single).

---

### Post by MadHatter21 on 2009-08-03
so take off  the quiet and splash options?


Works like a charm, thanks for the help. What does the splash option do?

---

### Post by MadHatter21 on 2009-08-03
I was under the impression from the book i am reading that when you boot into run level 1 you will get automatic root privledges, although i am not. Is it because i have set up the passwd root user to make su work?

---

### Post by sisco311 on 2009-08-03
> **MadHatter21 said:**
> I was under the impression from the book i am reading that when you boot into run level 1 you will get automatic root privledges, although i am not. Is it because i have set up the passwd root user to make su work?

Yes, sulogin is pathed in Ubuntu, if the root account password is locked(default), then you can boot in recovery mode and start a root shell without entering the root password. But if you have set a root password you are asked for it.

Other distros will ask for the root password even if it is locked.

---

### Post by wojox on 2009-08-03
Splash option is the splash screen you see while it loads everything. With it gone you'll see everything zip by while loading. As far as runlevel 1 does it ask for a username and password? is the prompt a # instead of $

---

### Post by sisco311 on 2009-08-03
> **wojox said:**
>  As far as runlevel 1 does it ask for a username and password? is the prompt a # instead of $

just for the root password (if the root account password is not locked).

---

### Post by MadHatter21 on 2009-08-03
> **wojox said:**
> Splash option is the splash screen you see while it loads everything. With it gone you'll see everything zip by while loading. As far as runlevel 1 does it ask for a username and password? is the prompt a # instead of $

> **sisco311 said:**
> Yes, sulogin is pathed in Ubuntu, if the root account password is locked(default), then you can boot in recovery mode and start a root shell without entering the root password. But if you have set a root password you are asked for it.

Other distros will ask for the root password even if it is locked.

Thanks for all of the quick help and replys.

Wojox, I have set up the su account on my computer so that i wouldnt have to do anything like sudo -i  so when i tried the root prompt on runlevel 1 I was prompted for a root password, the one i set for su. I have already solved the minor delma. 

What is run level 4 and 5 for ubuntu... anyone?

---

### Post by sisco311 on 2009-08-03
> **MadHatter21 said:**
> 
What is run level 4 and 5 for ubuntu... anyone?

Ubuntu uses Upstart, the runlevels are emulated for compatibility reasons. 

I think, that Ubuntu does not make any distinction between runlevels 2 to 5, but you have to check the symlinks in /etc/rc?.d/ if you want to be sure:) .

[http://en.wikipedia.org/wiki/Runlevel#Ubuntu]("http://en.wikipedia.org/wiki/Runlevel#Ubuntu")

---

