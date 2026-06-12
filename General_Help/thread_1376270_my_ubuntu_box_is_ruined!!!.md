---
title: "my ubuntu box is ruined!!!"
date: 2010-01-09
forum: General Help
---

### Post by rahilm on 2010-01-09
Hello...
[LIST=1]
[*]I installed ubuntu 9.10 karmic koala
[*]I did a full system upgrade
[*]I installed kubuntu-desktop to try out kde
[*]computer is unbelievably slow and hangs (C2D 2.0Ghz 1GB RAM)
[*]I decide to remove kubuntu-dektop
[*]i select all packages in synaptic under K desktop environment section
[*]kde is removed
[*]i install xfce4 and lxd to try them out
[*]but wait...i 4got. my cursor theme is stuck to that of kde.. i cannot change it
[*]computer hangs a lot..cpu usage soaring by xorg and compiz
[*]i decide to switch back to an earlier kernel
[*]things are back to normal (kernel 2.......-14-generic)
[*]another system upgrade
[*]vlc refuses to start (tried reinstalling)
[*]to be continued
[/LIST]

Any suggestions for a full reinstall???

---

### Post by Sef on 2010-01-09
Try this from the terminal (Applications > Accessories > Terminal):

Copy and paste these commands:

```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by staf0048 on 2010-01-09
> **rahilm said:**
> Hello...
[LIST=1]
[*]I installed ubuntu 9.10 karmic koala
[*]I did a full system upgrade
[*]I installed kubuntu-desktop to try out kde
[*]computer is unbelievably slow and hangs (C2D 2.0Ghz 1GB RAM)
[*]I decide to remove kubuntu-dektop
[*]i select all packages in synaptic under K desktop environment section
[*]kde is removed
[*]i install xfce4 and lxd to try them out
[*]but wait...i 4got. my cursor theme is stuck to that of kde.. i cannot change it
[*]computer hangs a lot..cpu usage soaring by xorg and compiz
[*]i decide to switch back to an earlier kernel
[*]things are back to normal (kernel 2.......-14-generic)
[*]another system upgrade
[*]vlc refuses to start (tried reinstalling)
[*]to be continued
[/LIST]

Any suggestions for a full reinstall???

Afraid of commitment maybe?  :-)  LOL

I think you should switch to Gentoo.

---

### Post by rahilm on 2010-01-09
what's this???
```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release  Unable to find expected entry  multivers/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

and ubuntu-desktop is already the newest version

---

### Post by rahilm on 2010-01-09
continued from above:
[LIST=1]
[*]it is my personal opinion that docks can be run on my computer without any issue. cairo doesn't. so i change the xorg.conf file. now it does
[*]Xorg starts slowing down after modifying xorg.conf (which was in itself a modifed one)
[*]minitube doesn't play videos
[*]i think of removing xfce4 but that only removes xfce4 de and not the components
[*]The only player that works is mplayer (and totem)
[*]I suspect GNOME do to be responsible for my plight
[/LIST]
I am seriously thinking of a complete re-install. That will make 24 hours of more work to get all programs and configurations back

---

### Post by steveneddy on 2010-01-09
If you're gonna hack around on your machine you have to expect to reinstall sometimes.

We all went down that path. It's how we all get to the set up that we prefer.

Just reinstall and be done with it.

Make sure you back up your /home folder.

good luck

---

### Post by darkstaar on 2010-01-09
> **rahilm said:**
> I suspect GNOME do to be responsible for my plight

From what you've written, I suspect RAHILM to be responsible for your plight.

> **rahilm said:**
> I am seriously thinking of a complete re-install. That will make 24 hours of more work to get all programs and configurations back

Well, I've done enough fresh installs of Ubuntu to know that it can be accomplished in about an hour, more or less, assuming a fast connection to the internet and /home on a separate partition.

---

### Post by smerral on 2010-01-09
Yoe need to completely remove kde and xfce. You could try that as a last resort before re-installing:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by steveneddy on 2010-01-09
I was re-reading your original post and I recommend not upgrading.

If you want a newer version then do a complete reinstall to the newer version.

---

### Post by rahilm on 2010-01-09
i switched back to the original linux kernel of karmic 2.6.31-14. All else are creating problems. until i backup and do a full re-install.

---

### Post by 3rdalbum on 2010-01-09
If you suspect your troubles are due to /etc/X11/xorg.conf, then you can actually try removing that file completely, thus letting Xorg configure itself each time on startup.

---

### Post by HyperHacker on 2010-01-09
No, don't remove your xorg.conf; just rename it. X may just not start at all anymore if you do that, so you'll want to be able to put it back.

Anyway it does sound like you broke something in all that switching desktops, playing with the config files, etc. If you're going to do such things, make full backups first! Also have /home on a separate partition so you don't have to overwrite it on a reinstall, if possible. If not, still, keep a backup of it (I use rsync to back up to an external disk every night) so restoring it is effortless.

(Tip: don't just go using 'cp' without the --preserve=all parameter to back up/restore things... you lose date information that way. :( )

---

### Post by rahilm on 2010-01-09
> **3rdalbum said:**
> If you suspect your troubles are due to /etc/X11/xorg.conf, then you can actually try removing that file completely, thus letting Xorg configure itself each time on startup.

Well..when i installed karmic, there was no xorg.conf file. The reason there is one now is that unfortunately i have one of those intel onboard graphic cards ubuntu stopped supporting, so i had to put an xorg.conf file with a modeline. Then X started running slow. Then i replaced that xorg.conf file with the one generated by puppy and then X runs perfectly except that the cairo-dock fails to start in that configuration so i had to revert to the modeline one...

removing xorg.conf file will get me stuck with 800x600 resolution

---

### Post by rahilm on 2010-01-11
how do you use rsync to back up? i am curious? i  am new to making backups

---

