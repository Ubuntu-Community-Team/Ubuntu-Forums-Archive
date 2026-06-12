---
title: "GDM and Dvorak on Jaunty"
date: 2009-09-22
forum: General Help
---

### Post by Songwind on 2009-09-22
I am having a devil of a time figuring out what's wrong with my desktop installation of 9.04.  Ever since I upgraded, GDM no longer honors the keyboard variant I have configured.  Virtual consoles and the main X-session both use Dvorak by default, with the option of switching to standard US by pressing both shift keys.  (I posted how I did that in [a post on my blog]("http://dragonseptarts.com/blog/?p=152").)  The problem is that GDM ignores it and just gives me the US standard layout.  This isn't a deal breaker, since I can use the keyboard fine this way, but it is annoying.  The most annoying part is that I can't figure out *why*.

I have even gone through the configuration on my Netbook, which is Dvorak only (and works fine in GDM) to try to find the setting.  No dice.

Does anyone have any suggestions?

---

### Post by Witepa on 2009-09-27
I actually have a similar problem, but more of a deal breaker. My keyboard is currently stuck at the Greek layout in gdm and I have no way of switching it back. I've tried to change the /etc/X11/xorg.conf file, the /etc/default/console-setup file, and done dkpg-reconfigure gdm and console-setup, but no dice, I'm still stuck.  Tell me if working with any of those work for you, I'll be interested to hear what you did.

By the way, if you are curious, my thread for my issue is [here]("http://ubuntuforums.org/showthread.php?t=1271427").

Good luck!

---

### Post by knattlhuber on 2009-10-05
Songwind and Witepa, I had more or less the same problem. After a short unsuccessful stint with Dvorak, I reverted back to QWERTY but GDM wouldn't follow.

I did
```
sudo dpkg-reconfigure xserver-xorg
```
to redetect the keyboard and set it back to USA standard.
Then I edited /etc/default/console-setup, removing the line 'xkbd-variant=dvorak' (or something like that).
After that GDM was back to QWERTY.

---

