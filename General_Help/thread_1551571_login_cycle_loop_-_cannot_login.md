---
title: "login cycle loop - cannot login"
date: 2010-08-12
forum: General Help
---

### Post by rdbowers on 2010-08-12
I've spent all morning fighting with a sudden new problem.  The login cycles- I already have a problem with mounting something connected with USB (long term minor annoyance, but everything works), but suddenly I cannot log in.

When I put my username and password in, the screen flashes black for about half a second, then the login screen re-appears.  If I put the wrong password in, I get an authentication error message (as expected) without turning black and then cycling again.

I have no problems going into terminal mode and logging in.

I've tried all sorts of suggestions related to this problem- reinstalling ubuntu-desktop, apt-get clean, sudo startx, and the last indicates that x-windows is already running.  I've found a couple more things to try, but I'm not too sure how well they'll work.

It seems to be connected with x-windows, but I don't know what is causing it.  Last night I had a big problem that required reinstalling nautilus (couldn't set up a connection to a remote server), and that problem was fixed- but this developed when I booted this morning.

It's a real problem, and any suggestions/help is greatly appreciated.  I use  this computer for most of my work and for at home- right now I'm using Windows (uggh), but would like to get back to Ubuntu.

---

### Post by dabl on 2010-08-12
Either your filesystem is full, or you have changed the permissions on some hidden X-related files in your user's home folder (usually caused by running graphical packages with "sudo" instead of "gksu").  Try booting "recovery mode", navigate to your user's home folder, and issue:

```
rm .ICEauthority
```

```
rm .Xauthority
```

then ```
sudo shutdown now -r
``` to reboot, and try logging in normally.

---

### Post by rdbowers on 2010-08-12
Already tried that- no change in symptoms.

Thanks for the suggestion, however!

---

### Post by rdbowers on 2010-08-13
_**WORKING!!!**_

I tried a lot of things, and the system finally came up.  I've tried booting it twice, and both times it's worked normally.

How I fixed it:
(Besides the things I'd already checked...)

I checked all of the files in the home directory (and my directory), and found three that had root ownership- both owner and group.  I changed them to my login.  No change in symptoms.

I tried reinstalling the ubuntu-desktop.  No change.

I tried reinstalling gdm.  No change.

I checked the hard drive- over 6gb free (on a 50 gb partition).

I tried changing out the xorg.conf file with one that I've used for tests in the past and knew was good.  No change.

I completely deleted and reinstalled gdm.
I reinstalled ubuntu-desktop again.  

The system came back and worked.

I'm a bit puzzled (I'm no Linux guru, although I've worked with computers since 74)... the gut feeling I have is that it was somehow in the interface between gdm and the Linux kernel, maybe some sort of interplay between gdm, Ubuntu-desktop, and the kernel.  It also could have been some sort of interaction between the three files with root ownership and gdm.

If it stays stable for a couple of days, I'll mark this thread solved.  The reading I've done suggests that some people had the problem come back.

---

### Post by rdbowers on 2010-08-14
It seems to be stable.  The thing that seemed to make the difference was the complete removal of GDM, installing GDM, and then reinstalling Ubuntu-desktop.

---

