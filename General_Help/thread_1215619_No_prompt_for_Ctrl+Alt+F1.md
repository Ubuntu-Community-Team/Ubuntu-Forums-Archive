---
title: "No prompt for Ctrl+Alt+F1"
date: 2009-07-17
forum: General Help
---

### Post by tkrisz on 2009-07-17
No prompt for Ctrl+Alt+F1. Help me, how to fix this?
I have a quite rapidly flashing "_" and a black background, but can't command my PC.

---

### Post by rampageoberon on 2009-07-17
> **tkrisz said:**
> No prompt for Ctrl+Alt+F1. Help me, how to fix this?
I have a quite rapidly flashing "_" and a black background, but can't command my PC.

```
ps aux | grep getty
``` The above code will tell you if the terminals are running

I'm assuming the flashing "_" is wanting you to login. try login with your username and password and see if it brings you a shell. (It should really show you some text I'd imagine)

---

### Post by tkrisz on 2009-07-17
```
root      2243  0.0  0.0   3944   604 tty4     Ss+  17:32   0:00 /sbin/getty 38400 tty4
root      2244  0.0  0.0   3944   604 tty5     Ss+  17:32   0:00 /sbin/getty 38400 tty5
root      2247  0.0  0.0   3944   604 tty2     Ss+  17:32   0:00 /sbin/getty 38400 tty2
root      2248  0.0  0.0   3944   604 tty3     Ss+  17:32   0:00 /sbin/getty 38400 tty3
root      2249  0.0  0.0   3944   604 tty6     Ss+  17:32   0:00 /sbin/getty 38400 tty6
krisz     5159  0.0  0.0   7548   916 pts/0    S+   18:03   0:00 grep getty

```

No, i can't enter anything, it's just flashing and laughing at me.

---

### Post by CatKiller on 2009-07-17
For some reason you don't have a TTY1. Ctrl-Alt-F2 should still work, though.

---

### Post by jonobr on 2009-07-17
Yikes, multi response in the time it took me to answer.>
Removing my pearls of wisdom

---

### Post by tkrisz on 2009-07-17
Tried Ctrl+Alt+F2. Same. Then after switching back (Ctrl+Alt+F7), tty2 disappears from the above list.

```
root      2243  0.0  0.0   3944   604 tty4     Ss+  17:32   0:00 /sbin/getty 38400 tty4
root      2244  0.0  0.0   3944   604 tty5     Ss+  17:32   0:00 /sbin/getty 38400 tty5
root      2248  0.0  0.0   3944   604 tty3     Ss+  17:32   0:00 /sbin/getty 38400 tty3
root      2249  0.0  0.0   3944   604 tty6     Ss+  17:32   0:00 /sbin/getty 38400 tty6
krisz     6469  0.0  0.0   7548   916 pts/1    S+   18:19   0:00 grep getty

```

---

### Post by tkrisz on 2009-07-17
Rebooted, tty1 is back again. 
```
root      2234  0.0  0.0   3944   604 tty4     Ss+  19:15   0:00 /sbin/getty 38400 tty4
root      2235  0.0  0.0   3944   600 tty5     Ss+  19:15   0:00 /sbin/getty 38400 tty5
root      2238  0.0  0.0   3944   604 tty2     Ss+  19:15   0:00 /sbin/getty 38400 tty2
root      2239  0.0  0.0   3944   604 tty3     Ss+  19:15   0:00 /sbin/getty 38400 tty3
root      2240  0.0  0.0   3944   600 tty6     Ss+  19:15   0:00 /sbin/getty 38400 tty6
root      3047  0.0  0.0   3944   604 tty1     Ss+  19:15   0:00 /sbin/getty 38400 tty1
krisz     3461  0.0  0.0   7548   912 pts/0    R+   19:16   0:00 grep getty

```
Then try to input something, changing back to graphic mode and tty1 disappears from the list.

---

### Post by tkrisz on 2009-07-17
I noticed a very strange thing:

I have the kernel 2.6.28-14 and 2.6.30-020630, too. tty1 (etc.) working perfectly on 2.6.28-14. The above problem only appears if i boot to  2.6.30-020630. 

The problem may be related to the following. In 2.6.30-020630 Alt+Ctrl+F1 puts me into 720x400@70Hz which i never set, it came with 2.6.30 kernel. During the bootup my PC also puts itself into this strange resulution 2 times for a second. In startupmanager i set 800x600@60Hz, color depth 16 for the grub and Ubuntu works in 1680x1050@60Hz once it is booted.
With the 2.6.28-14 kernel there's no sign of 720x400@70Hz during the bootup and Alt+Ctrl+F1 puts me into 800x600@60Hz i think.

Can this be the problem? Any idea how to get rid of that 720x400@70Hz?

---

### Post by master_kernel on 2009-07-17
Where'd you get the 2.6.30 kernel from?

---

### Post by CatKiller on 2009-07-17
> **tkrisz said:**
>  I have the kernel 2.6.28-14 and 2.6.30-020630, too.

So you've been installing third-party kernels, then? You might want to read [this bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928/"), and [this post]("http://ubuntuforums.org/showthread.php?t=1130582"), in that case.

EDIT: fixed link.

---

### Post by tkrisz on 2009-07-17
Got from here, following a Guide (probably that one you suggest) here in Ubuntu Forums:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

Isn't it normal to have the old kernel as an option to load?

The bug report link is not working for me.

---

### Post by CatKiller on 2009-07-17
> **tkrisz said:**
> Isn't it normal to have the old kernel as an option to load?

Yes.

The post that I linked to mentions a script posted for that bug report specifically to fix a problem with the TTYs when using that kernel. You might find it useful.

> The bug report link is not working for me.

Ta. Fixed it.

---

### Post by tkrisz on 2009-07-17
Thx for the help.
So i should run that 2 scripts? Is the 1st one starting with the 1st diff and ending at } the 3rd line from below?
I'll try them tomorrow, getting too late.

---

### Post by hibliss on 2009-07-17
What is the purpose of running that kernel? What does it offer that you need?

---

### Post by CatKiller on 2009-07-18
> **tkrisz said:**
>  So i should run that 2 scripts?

I have no idea. I only came across that thread to help someone who'd hosed their computer by running that kernel...

---

### Post by master_kernel on 2009-07-18
Next time, compile your own! JK, but it would probably be safer (not necessarily faster) if you have 3 hours to spare next time you need a new kernel.

---

