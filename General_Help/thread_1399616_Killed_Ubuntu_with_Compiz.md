---
title: "Killed Ubuntu with Compiz"
date: 2010-02-05
forum: General Help
---

### Post by Robster2 on 2010-02-05
Dumb! Dumb! Dumb! I really did not have time to be mucking around with eyecandy.

I installed compiz but I found that after I did I could change to another desktop.  Ubuntu still worked.

I tried to remove it using the method in post #4

[http://ubuntuforums.org/showthread.php?t=488342](http://ubuntuforums.org/showthread.php?t=488342)

On reboot I got through the grub booted up OK then I get some distorted graph rubbish on the top of the screen and the rest black.  Ubuntu seems to try a few resolutions but finally hangs.

Any suggestions?

---

### Post by quixote on 2010-02-07
I looked at the linked thread, and the method he uses is pretty hairy.  He's uninstalling and reinstalling a whole set of important system files, which, so long as it all works, is no harm done, I suppose.  Sounds like it may not have worked in your case. :(  

If you have important data on that drive, first thing I'd do is boot from a liveCD, and move that data onto an external harddrive or whatever you have available.

Second, if it was me, I'd just reinstall the system at that point.  I've never had much luck recovering systems which have been borked, but maybe somebody who has will jump in with a better howto than I can give you.

If you don't want to reinstall, then you need to recover your X graphical system.  Can you boot into recovery mode?  If you can get recovery mode, then this command```
dpkg-reconfigure xserver-xorg
```will take you through a whole series of questions, at the end of which X should hopefully be rebuilt.  You don't need "sudo" because you're already root in recovery mode.  I've left out "-phigh" because I'm not sure you want to omit all the low priority questions.  I think accepting the default answer works if the question makes no sense.  (It's been a while since I've had to do this.)

To exit recovery mode, type "halt now" (no quotes) and then restart.

(In future, if you want to stop using compiz, no need to uninstall it, which is an iffy process.  Type "sudo metacity --replace" and compiz is switched off.  To swtich it back on: "sudo compiz --replace")

Hope this helps get your system back!

---

### Post by Robster2 on 2010-02-08
Cheers thanks very much.

To add insult to injury my laptop stopped working all together.  Will not power up, but that is OK fortunately I had backed up my /home tree not so long ago on to a terrabyte drive so I was able to get up and going pretty on another computer.

The re install of the Gnome desktop was I think failed.  Should have forced the install

Code:

```
sudo apt-get install -f && sudo apt-get update && sudo apt-get install ubuntu-desktop
```

A new install sounds like the way to go.   I will try to get the desktop back  for the experience, back up and do a clean install

---

### Post by quixote on 2010-02-08
> fortunately I had backed up my /home tree\\:D/

If you tried the --force switch to reinstall, did that help?  Or still borked?  

The reason I said I haven't had much luck is that even when it seems to work, I'd keep bumping into system weirdnesses and nonfunctions.  Some things obviously stayed broken and troubleshooting them as they came up got old real fast.  Plus, most of the time, I had no idea what to do anyway.

---

