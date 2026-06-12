---
title: "Cannot log into 12.04"
date: 2012-05-05
forum: General Help
---

### Post by Paddy Landau on 2012-05-05
In the past three days, a new problem has occurred with my 12.04 Precise installation.

It was a fresh installation, and is fully updated.

[LIST]
[*] When I start or restart my machine, I get to the login screen.
[*] I enter my password.
[*] The screen says, "Logging in..."
[*] Nothing else happens.
[*]I can shut down or restart by using the button in the top-right corner. I can also press Ctrl-Alt-F1 to enter the console.
[/LIST]
 Work-around (which I found through trial-and-error):

[LIST]
[*] If I boot into the previous kernel version (3.2.0-17-generic) -- I don't have to log in, just boot into it -- then restart into the newest version (3.2.0-24-generic), I can log in again.
[*] But it only works once; when I restart, I again cannot log in.
[/LIST]
  I have tried removing [FONT=Lucida Console]~/.ICEauthority[/FONT] and [FONT=Lucida Console]~/.Xauthority[/FONT], but it makes no difference.

I don't know whether it's relevant or not, but I also found that when I boot into Recovery Mode, the home partition is not mounted, leaving [FONT=Lucida Console]/home[/FONT] completely empty.

---

### Post by hal8000 on 2012-05-05
Thats a strange problem.
Only thing I can suggest is log in via the console , ctrl-alt-F1 and try changing your user password.
Its almost as if it is rejecting your password with a count of 1 login.
I have not upgraded the kernel on Ubuntu 12.04, still using minor revision
17.

From the console, can you login with startx?

---

### Post by Paddy Landau on 2012-05-05
Oh, it just gets worse.


[LIST]
[*]I sign onto Recovery Mode, and find that I cannot change my password or startx, because... the file system is read-only!
[/LIST]

[LIST]
[*]I changed my password the normal way (booted normally and used System Settings > User Accounts), and it failed to change my keyring password. Grrr! Surely this is supposed to be done automatically when you change your password!
[/LIST]

So, I'm still stuck. Why is the Recovery Mode booting into a read-only file system? This may be a clue as to what is going on.

Fortunately, I still have the work-around, but it is bizarre.

---

### Post by meanpt on 2012-05-05
That happened to me when I partitioned the sd card, the test bed where ubuntu lives, either with gparted either with the disk utility. With the later, it doesn't matter if I choose, or not, to take the ownership of the file system, cause in the end I may not boot or not be able to do anything else, even with sudo, beyond surfing the net and creating documents. The same applies to the gparted partitioned device. In the end, I opted to use only the partitioning offered through ubiquity, the installer, and was able to move on.

---

### Post by Paddy Landau on 2012-05-06
> **meanpt said:**
> That happened to me when I partitioned the sd card...
Oh... I wonder if this has something to do with it.

I have an empty slot for an SD card, which was recognised by Disk Utility on Natty 11.04, but which does not show in Disk Utility on Precise 12.04.

A driver problem, perhaps?

---

### Post by Paddy Landau on 2012-05-06
Who would have believed it? It has to do with the wallpaper you choose!

See [post #4 in the Precise known bugs thread]("http://ubuntuforums.org/showthread.php?p=11887754#post11887754").

Also see [the relevant bug]("https://bugs.launchpad.net/ubuntu-tweak/+bug/888186").

Marking this as solved.

---

