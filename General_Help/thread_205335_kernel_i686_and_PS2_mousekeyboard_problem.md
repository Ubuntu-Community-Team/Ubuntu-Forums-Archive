---
title: "kernel i686 and PS/2 mouse/keyboard problem"
date: 2006-06-28
forum: General Help
---

### Post by vas56 on 2006-06-28
Hi everyone,

I installed Ubuntu 6.06 few days ago and since then I am trying to find a solution for the following problem.

when using kernel i686 SMP, the mouse and the keyboard (both PS/2) don't respond at the login screen (or at the desktop if the automatic login option is enabled). Selecting the i386 at boot time both devices work fine.

The behavior is similar to a freeze but Ubuntu actually works just fine because when the automatic login is enabled and gets to the desktop, the screen saver is triggered normally and the update software notification pops up etc. so it looks like it is explicitly the mouse and the keyboard that don't activate properly when the i686 kernel is used.

Any ideas of what might be causing this?

Do I have to change any of the mouse or keyboard settings in the xorg.conf file or elsewhere?

Funny thing is that right after the required restart when the i686 installation completed everything worked fine until the next restart.
Now even if I remove completely the i686 kernel and the glx nvidia drivers and start all over again, the problem persists.

I did a thorough search and it seems that problems with either devices is frequent, but trying few of the suggestions offered in other posts didn't help.

---

### Post by dicecca112 on 2006-07-09
I'm having the same issues, can some please help us?

---

### Post by vem0m on 2006-07-09
maybe try configuring X11? i dunno which guide did u use to install or what method?

---

### Post by dicecca112 on 2006-07-10
nope I've reconfigured X11 all day.  I used the automatix way, and easy ubuntu way.  No dice on either

---

### Post by vem0m on 2006-07-10
maybe a bad compile then have u tried recompiling the kernel?

---

### Post by dicecca112 on 2006-07-10
> **vem0m said:**
> maybe a bad compile then have u tried recompiling the kernel?

downloaded from the repos.  I'm gonna try Kubuntu to see if the issue persists.  if it does, I may have to try another distro, and wait to reinstall Ubuntu when they fix this issue

---

### Post by vem0m on 2006-07-10
hmmmmm well i use Kubuntu so hope it works out for u if not someone here soon should be able to help or get the kernel thu another method such as in [THIS TOPIC]("http://ubuntuforums.org/showthread.php?t=85917") i used it to update to a 686 and it worked great best of luck to u

---

