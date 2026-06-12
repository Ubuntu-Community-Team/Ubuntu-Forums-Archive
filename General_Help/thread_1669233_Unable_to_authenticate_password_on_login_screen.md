---
title: "Unable to authenticate password on login screen"
date: 2011-01-17
forum: General Help
---

### Post by Netemeyer on 2011-01-17
Long time reader, first time writer.

I may be a beginner to UBUNTU 10.10, but I'm fairly certain that this is weird: I have had no trouble logging into my Ubuntu 10.10 netbook until this morning. Now I am unable to get past the login screen.

It says that there is an Authentication Failure, which is bogus. Not only should the password work, but it does in the Terminal. I am able to login to the terminal and gain root access. I can even change my unix password, but no matter what I try I can't get to my desktop.

I'm sure I've overlooked something due to my inexperience, so any help would be most appreciated.

Note: I did run into a major issue with a frozen program. Rather than reboot, I tried to close it using the kill command. What ended up happening was that all that remained was my wallpaper... probably a bad move on my part, but I'm a rookie. I think I killed all running applications. This happened last night... so probably related.

---

### Post by Smart Viking on 2011-01-17
Hi, my mom had a similar problem where i decided to simply uninstall gdm and let her login through the shell.

Maybe this will help you get into X:

first go to a tty(terminal) with <ctrl>+<alt>+<F?>
log in
then run the following:
```
sudo /etc/init.d/gdm stop
```
*IF* the above command didn't work, try the following instead:
```
sudo /etc/init.d/gdm3 stop
```
The first one is probably the one that could kill gdm.
-
Then, run X with the following command:
```
startx
```

I hope this helped.

---

### Post by Netemeyer on 2011-01-17
Thanks! That seemed to do it, or at least do something to get me in. Hopefully this doesn't happen again any time soon.

---

