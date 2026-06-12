---
title: "Gnome Crashing"
date: 2010-12-21
forum: General Help
---

### Post by samfraser on 2010-12-21
I've been using Ubuntu 10.04 LTS - the Lucid Lynx for a few months now on my HP netbook 450.  There are a few problems I've been having.

1.  The mousepad can't select horizontally + the left and right mouse click buttons only work if pressed right at the bottom.

2.  The most annoying! Is that Gnome crashes, it just complete bombs out! I get an error X needs to start in low graphics mode, then BOOM I've lost all my work!

Any suggestions?

uname -a
Linux samfraser-laptop 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 2

---

### Post by matt_symes on 2010-12-21
Hi

> The most annoying! Is that Gnome crashes, it just complete bombs out! I get an error X needs to start in low graphics mode, then BOOM I've lost all my work!

Do you have compiz running?

What is your graphics card?

Are the any errors in /var/log/Xorg.0.log or ~/.xsession-errors

> The mousepad can't select horizontally + the left and right mouse click buttons only work if pressed right at the bottom.

Is this a hardware issue?

Kind regards

---

### Post by samfraser on 2010-12-22
Thanks for your reply.

ps aux | grep compiz
500       1871  0.0  0.0  89012   784 pts/0    S+   22:15   0:00 grep compiz

Nope, not running compiz.

There is a lot of output in those log files, is there anything specific I can search for?

The mousepad works fine in windows...

---

### Post by matt_symes on 2010-12-23
Hi

Post the output of 

```
xinput --list
```

This will tell us a bit about your mouse.

Also post the output of

```
lspci -v | grep -i -A10 vga
```

This will tell us a bit about your graphics card.

As far as the logs go, try to estimate where about the in the logs you think it died and then look around there.

You could post them on here after a crash but if you do that use code tags of it will be a real pain to read. Hopefully there will be something useful in one of them.

Kind regards

---

