---
title: "Problems installing - graphics card?"
date: 2006-04-11
forum: General Help
---

### Post by Tim Thumb on 2006-04-11
Even though a complete novice, I've managed to easily install Breezy on a couple of Intel based laptops over the last month or so. But now I'm trying to get it on an AMD desktop and not succeeding. It's an XP2000 with I believe a ProSavage 8 graphics card.

The machine currently has WinXP on it so I just did a boot from the Breezy cd and got it to set up a new partition etc without any problem with Grub to sort out booting. When the system was restarted it went through several processes and then died with a Grub error 17. 

Even after lots of searching on these forums I couldn't fix this problem and don't fully understand it now. I couldn't even get into Windows any more. So all I could do with my limited experience was to reinstall Windows with a full format of the hard drive. This got the machine working again.

So next I decided to go down the Live cd route to eliminate the Grub factor and try to work out what the problem is. The boot goes fine until it gets to "checking battery state" and then it just hangs. Reading many threads gave me the impression that this is a problem with X as it's next to load - is this correct, I don't even know what X is.

So more fumbling in threads allowed me to pull up a prompt at this point with alt/ctrl/F1. Then I did:

```
sudo dpkg-reconfigure xserver-xorg
```

Went through this config basically answering yes to everything. Noted that it had 'picked up' what I assume to be my graphics card - ProSavage 8 and finished the config edit. Then did:

```
sudo /etc/init.d/gdm restart
```

At this point Ubuntu loaded fine although I've no idea what I did!

Now when I try to reboot I have to do all this again as presumably the Live cd has no other way of knowing these settings each time. So I now want to install the full version again, but not before I know what to do to fix the problem. I don't want to just get stuck with the Grub error again.

Any help much appreciated and I hope this all makes sense.

---

### Post by Tim Thumb on 2006-04-12
For anyone who's interested, I went ahead with the full install and came to the point where the machine seemed to freeze again - not the Grub error though, just monitor going dead and then woke it up with alt/ctrl/F1. 

So I then did exactly as outlined for the Live CD - reconfiguring xserver-xorg. This fixed the problem and the machine appears to be working fine now with the new install in place.

---

### Post by Mustard on 2006-04-12
[QUOTE=Tim Thumb]For anyone who's interested, I went ahead with the full install and came to the point where the machine seemed to freeze again - not the Grub error though, just monitor going dead and then woke it up with alt/ctrl/F1. 

So I then did exactly as outlined for the Live CD - reconfiguring xserver-xorg. This fixed the problem and the machine appears to be working fine now with the new install in place.[/QUOTE]

/me slaps the 'Official Linux Video Guru' badge on Tim Thumbs chest.

You've now be promoted to official fixer upper of video problems. ;)

Well done!

---

### Post by justleen on 2006-04-12
*thumbs up* Grats :)

Looks like the installer for some reason had the wrong setting.drivers for the savage card.. running a reconfigure of the Xserver allow you to change the settings... obviousliy you knew the better, and fix it! yey!

---

### Post by Tim Thumb on 2006-04-12
Well thanks, you both made me feel real proud :p

---

