---
title: "tonight's update broke netbook launcher"
date: 2011-10-18
forum: General Help
---

### Post by jimrz on 2011-10-18
ran tonight's updates on my Dell Vostro A90 running 10.04 Netbook Edition. When I restarted the launcher was gone. I can choose gnome in sessions and that works or I can choose netbook edtion 2d and it works but is kind of funky but no luck with normal netbook edition. Any ideas how I can get the regular launcher back?

---

### Post by cariboo on 2011-10-18
Moved to General Help, as this isn't a cafe question.

Have you tried:

```
unity --reset
```

in a terminal?

---

### Post by jimrz on 2011-10-18
> **cariboo907 said:**
> Moved to General Help, as this isn't a cafe question.

Have you tried:

```
unity --reset
```

in a terminal?

tried your suggestion, but this is 10.04 so ```
code unity not found ... did you mean units
```
thanks for the thought

---

### Post by areddin on 2011-10-19
I think I'm having the same problem.  Restarted after an update today, and everything seems to work but there is no launcher on the desktop.  

I tried running netbook-launcher in the terminal and I got this:


X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  17
  Current serial number in output stream:  17

I'm not a big linux expert so I'm kind of at a loss...
I'm also running 10.04, on an old 701SD eeePC.

---

### Post by HIPS on 2011-10-19
Exactly the same happend to me. I first thought something went wrong with my Dropbox installation, but when I start to think about it I did run the latest update, and after restart the launcher was gone.
 
I get the same message as arredin when I try to run the launcher in Terminal.
 
I have an Asus EeePC 1101.

---

### Post by mikewhatever on 2011-10-19
Same here. Looks like the recent update broke the netbook launcher. Could it have something to do with the xserver-xoeg-core update?

From the update history log:
> Start-Date: 2011-10-19  13:06:36
Upgrade: libkrb5-3 (1.8.1+dfsg-2ubuntu0.9, 1.8.1+dfsg-2ubuntu0.10), python-desktopcouch-records (0.6.4-0ubuntu3.2, 0.6.4-0ubuntu3.3), byobu (2.68-0ubuntu1.1, 2.68-0ubuntu1.2), libkrb5support0 (1.8.1+dfsg-2ubuntu0.9, 1.8.1+dfsg-2ubuntu0.10), desktopcouch (0.6.4-0ubuntu3.2, 0.6.4-0ubuntu3.3), upower (0.9.1-1, 0.9.1-1ubuntu1), apt-transport-https (0.7.25.3ubuntu9.7, 0.7.25.3ubuntu9.8), **xserver-common **(1.7.6-2ubuntu7.6, 1.7.6-2ubuntu7.8), libupower-glib1 (0.9.1-1, 0.9.1-1ubuntu1), libdevkit-power-gobject1 (0.9.1-1, 0.9.1-1ubuntu1), **xserver-xorg-core** (1.7.6-2ubuntu7.6, 1.7.6-2ubuntu7.8), libk5crypto3 (1.8.1+dfsg-2ubuntu0.9, 1.8.1+dfsg-2ubuntu0.10), apt-utils (0.7.25.3ubuntu9.7, 0.7.25.3ubuntu9.8), apt (0.7.25.3ubuntu9.7, 0.7.25.3ubuntu9.8), nvidia-current-modaliases (195.36.24-0ubuntu1~10.04, 195.36.24-0ubuntu1~10.04.1), libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.9, 1.8.1+dfsg-2ubuntu0.10), python-desktopcouch (0.6.4-0ubuntu3.2, 0.6.4-0ubuntu3.3), nvidia-96-modaliases (96.43.17-0ubuntu1, 96.43.17-0ubuntu1.1)
End-Date: 2011-10-19  13:07:23


I've tried filing a bug report, but 'ubuntu-bug' doesn't work either - a bug that's supposedly fixed.
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/865199](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/865199)

Any ideas what now?

---

### Post by wayeast on 2011-10-19
> **mikewhatever said:**
> Could it have something to do with the xserver-xoeg-core update?

Mikewhatever,

Do you know a way to revert to the previous versions of xserver and xorg-core to see if that fixes the problem?

FYI, my problem is not exactly as described above -- my netbook is starting normally and I get a desktop background with the toolbar at the top.  I just don't have the netbook remix desktop with all my application icons on the desktop.  I've never had to deal with a launcher.

---

### Post by naledi on 2011-10-19
I seem to have the same problem - running a Compaq netbook - I ran the update and after reboot, lost the launcher - was time for a tidy up so I actually formatted the hard-disk and re-installed from a USB drive - all worked fine until I ran the update - then on reboot lost the launcher again.  So quite sure the problem is with the update - Any ideas on how to 'claw back' to the previous version would be most welcome.  I'm afraid I'm completely lost without the launcher.

---

### Post by sybille on 2011-10-19
This thread might help for downgrading the packages, although it's maybe not the best solution since it was a security update. See:
[http://ubuntuforums.org/showthread.php?p=11365760](http://ubuntuforums.org/showthread.php?p=11365760)

Also, could everyone who is experiencing the problem with the updated packages go to the  following Launchpad bug and click at the top of the page to confirm that  the bug is affecting you?
 
 [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905)
 
 Thanks!

---

### Post by mikewhatever on 2011-10-19
> **wayeast said:**
> Mikewhatever,

Do you know a way to revert to the previous versions of xserver and xorg-core to see if that fixes the problem?

FYI, my problem is not exactly as described above -- my netbook is starting normally and I get a desktop background with the toolbar at the top.  I just don't have the netbook remix desktop with all my application icons on the desktop.  I've never had to deal with a launcher.

Unfortunately, no, I've no idea how to revert to the previous versions.
Just in case, I'd like to mention that alt+f1 opens the menu in 10.04, and one can also bind the Super key to the menu.
[http://www.howtogeek.com/howto/27038/use-the-windows-key-for-the-start-menu-in-ubuntu-linux-10.04/](http://www.howtogeek.com/howto/27038/use-the-windows-key-for-the-start-menu-in-ubuntu-linux-10.04/)

---

### Post by 0zymandias on 2011-10-19
Same problem here! At least it wasn't me who broke the launcher. Thought I killed some package and was busy all day figuring out what went wrong .. until now.

---

### Post by krizze on 2011-10-19
Same problem here after update. Acer netbook.
Not good for a LTS-release. Hope it will be fixed soon.

---

### Post by wayeast on 2011-10-19
> **mikewhatever said:**
> Just in case, I'd like to mention that alt+f1 opens the menu in 10.04...

Yes, this works for me.  Another solution (rather, workaround) is to log out and log back in in a GNOME session.

I've added a comment to the bug report referenced by sybille.

---

### Post by boufer on 2011-10-19
> **jimrz said:**
> tried your suggestion, but this is 10.04 so ```
code unity not found ... did you mean units
```thanks for the thought

I have the same problem (I think) and I'm not that good with Ubuntu and programming and all. I tried the same thing and got the same message. All I got now is a black screen, see the dump from my screen.

If I try to click somewhere in the upper menu all I get are "preferences" or "about", (these preferences only deals with when windows are visible). I would like (that is, need) the launcher or at least menus so that I can start programs. I don't like to watch this black screen! Got to learn more about Ubuntu!!

---

### Post by boufer on 2011-10-19
> **wayeast said:**
> Yes, this works for me.  Another solution (rather, workaround) is to log out and log back in in a GNOME session.

I've added a comment to the bug report referenced by sybille.

ALRIGHT!

This solved the problem with getting the launcher at least partially! Now I'll spend some time trying to get this to stick to the screen :p

THX a lot always great using these fora!

---

### Post by wedge9s on 2011-10-19
> **wayeast said:**
> Yes, this works for me. Another solution (rather, workaround) is to log out and log back in in a GNOME session.
 
I've added a comment to the bug report referenced by sybille.
 
I must admit after installing Ubuntu 10.04 LTS (Netbook Edition) less than 48 hours ago I am not overly impressed at how a bug of this magnitude slipped through testing especially for an LTS release!
 
Oh well I guess the people doing the testing are only human after all ;), 
I'm currently hoping for a quick resolution (now that its listed as a critical bug).

---

### Post by krizze on 2011-10-19
Yup, looks like they are looking into it pretty quicly at least. Guess that's one major pro of using a LTS-version :)

---

### Post by boufer on 2011-10-19
Right, now I can access the launcher by using the old windows button... But I still want to get back to the old launcher. Is it possible to get the launcher to stick to the desktop the way it used to do?

Maybe a simple problem but hey I'm a simple guy.

Another related possible solution or question: is it possible to get links on the desktop? ("windows-style")

thx everybody for helping out

---

### Post by kcyw on 2011-10-19
Same problem here.
I managed to partially fix it by adding netbook-launcher-efl to startup programs.
Basically what I did was change the already existing netbook-launcher entry from:
```
sh -c "CLUTTER_VBLANK=none netbook-launcher"
```
to:
```
sh -c "CLUTTER_VBLANK=none netbook-launcher-efl"
```

Netbook launcher would then show up at startup.
The go-home-applet is still broken though and I have no idea how to fix it. Meddling with the source sounds like the best option. Reinstalling it didn't help.
Still, a pretty good temporary fix.
Hope that it helps anyone.

---

### Post by sybille on 2011-10-19
It looks like new, fixed packages are on the way:
[https://bugs.launchpad.net/ubuntu/+s...05/comments/20]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905/comments/20")

So hopefully everything will be sorted soon!

---

### Post by krizze on 2011-10-19
Works now :)

---

### Post by jimrz on 2011-10-19
fix provided by today's updates took care of the problem ... thread marked "solved"

---

### Post by boufer on 2011-10-20
Yes this works for me too, the launcher is back after the latest upgrades:p

---

