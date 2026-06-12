---
title: "Shoud dd be a process that automatically starts?"
date: 2009-11-22
forum: General Help
---

### Post by pmdkh on 2009-11-22
I'm running Ubuntu 9.04.  I was using **dd** to write random data over my swap partition, and I think that something is messed up.

I used this command to write random data over my swap:

```
dd if=/dev/urandom of=/dev/sda2
```

Without thinking about this, I did this while booting from my hard drive, instead of while booting from a live cd.  This caused my computer to freeze.  I restarted my computer and it froze shortly after starting.

I then booted from a live cd and used **gparted** to take a look at my partitions.  Sure enough, the swap partition was not recognized as swap space.  So I reformatted it and edited my fstab to reflect the new UUID.

Now my swap partition is working correctly.  However, after I restart my computer, **dd** is always running.  It usually has a PID of 2315, give or take 1 or 2.  It's PPID is 1, so it was called by **init**.

After the computer has been on for a few hours, it looks like it hasn't done any work (see below), but I still don't think it should be there.  Unless I'm mistaken and a **dd** process is always called on startup for some reason.

```
pmdkh@laptop:~$ ps -e | grep 2313
 2313 ?        00:00:00 dd
```

Under **Sytem -> Preferences -> Startup Applications -> Options**, I have unchecked the **"Automatically remember running applications when logging out"** option.  This has not stopped **dd** from being automatically started.

I also deleted the contents of the **~/.config/gnome-session/saved-session** folder because I thought that it might be the culprit.  This also has not helped.

So finally, my questions are:
1)  Should **dd** be acting this way?  If yes, why?
2)  If no to 1, what can I do to stop **dd** from starting automatically?

Let me know if you need any more information.  Thanks for the help.

---

### Post by dcstar on 2009-11-23
> **pmdkh said:**
> 
........
So finally, my questions are:
1)  Should **dd** be acting this way?  If yes, why?
2)  If no to 1, what can I do to stop **dd** from starting automatically?


[LIST=1]
[*]Because the system uses it for other things
[/LIST]

---

### Post by mgol on 2009-11-23
> **pmdkh said:**
> 
Under **Sytem -> Preferences -> Startup Applications -> Options**, I have unchecked the **"Automatically remember running applications when logging out"** option.
Try to kill all dd processes (if there are any) and AFTER that go to that tab and click "Remember currently running applications" - when You unchecked automatic restoring applications present on system shutdown (IMHO) it remembers apps from the last time this option was active - which could potentially include dd.

---

