---
title: "CIFS VFS: Server not Responding &amp; Gnome network manager &amp; Wicd"
date: 2009-11-24
forum: General Help
---

### Post by Luka Batistic on 2009-11-24
*System: 9.10 Karmic Desktop on an Asus EEE 900, network shares on a winxp comp mounted over a wireless network.*

Writing about the (as I now see) well known CIFS error caused by shares not being unmounted and restart (importantly) & shutdown (less so) stalling for long periods of time.

I am new to linux/ubuntu so please bare with me.

Firstly, there are various bugs on this subject (vpn, cifs, smbfs mounts not unmounting and cifs giving the error) with the same cause - because the nework is down before cifs starts unmounting the drives.

And from what I can gather there are different workarounds from years old like moving around the order of unmounting in /etc/rc0.d and /etc/rc6.d (doesn't work for my system) to newer ones like including unmount commands in the postsession gdm script (doesn't work either) to writing an unmount script and running it manually before restart (don't care so much about shutdown; works for any system I guess but is not really a solution).

 I'd like to share I've found another workaround I haven't seen mentioned on these forums or in the bug reports - installing [Wicd]("http://www.wicd.net/") (an alternative network manager to the default gnome one). After installing Wicd (and uninstalling gnome network manager - you can do both in System->Administration->Synaptic PM) this problem went away - no more slowdowns. :)

Don't know enough to say with certainty but it seems my wireless connection gets killed sooner with gnome NM than with Wicd, causing the stall under GNM but not Wicd. 

Which brings me to...

Secondly, how does one go about posting this as a bug on launchpad?

There seem to be so many bug reports already it's hard to decide where to put this. Lots of bugs are marked as duplicates but they're not really the same apart from the fact that a lack of network is causing them.
The chronologically first ones seem to (have?) been caused by the incorrect sequence in in the shutdown/restart scripts.
The one I'm describing seems to be connected to the gnome network manager and me mounting drives over a wireless connection.

Anyway, there's a lot of confusion on the issue already and I'd like to avoid adding to it.

And thirdly...
Installing Wicd brought another 'problem' with it (for me anyway). I'm mounting my shares over a wireless network and naturally cifs reports and error when it tries to mount them through fstab since the network isn't up yet (I'm assuming).

The weird thing about this is that when I had gnome network manager installed, the drives would mount anyway (i.e. show up on my desktop after login).

But with Wicd, they are not there so I had to add a small post connection script to Wicd (mount -a # to mount the drives from fstab). Tried putting 'mount -a' in etc/rc.local but that didn't work. Just realised the better idea would be to make a whole mounting script to be exectued after a connection is made as the entries in fstab just slow down bootup now :)

To expand my knowledge... Does gnome network manager issue a remount of fstab once it establishes a connection?

Yikes, just realised how much I wrote.. Sorry :)

To sum up:
1. If you're getting a ' CIFS VFS: Server not Responding' error on shutdown/restart, try replacing the gnome network manager with Wicd
2. Should I report this as a new bug or spend hours trying to find the bug that describes my exact situation?
3. Does gnome network manager remount fstab drives once it establishes a (wireless) connection?

---

### Post by Luka Batistic on 2009-11-30
A bump and some new info...

Reinstalled 9.10 and reproduced the same as above on a completely fresh install.

---

### Post by ubradford on 2009-12-06
I found a fix for this issue that works on Ubuntu 9.10 (Karmic) and wireless (WPA). I posted it here:
[http://ubuntuforums.org/showthread.php?p=8449027#post8449027](http://ubuntuforums.org/showthread.php?p=8449027#post8449027)

---

### Post by Luka Batistic on 2009-12-07
Thanks  for the tip.

I've now installed various flavors of Ubuntu and this problem is present in everything I've tried.

So I just use Wicd now and put the script for automatic mounts of win shares in the postconnect part of Wicd (instead of mounting them through fstab as I did with gnome-network-manager). 

Unmounting and shutdown/restart works as it's supposed to without any script in Wicd.

The only drawback is no VPN support in Wicd but they say it's coming in the next version and in the meantime, I've made scripts which take care of VPN.

---

