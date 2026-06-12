---
title: "can't login, keeps going back to login screen"
date: 2011-01-17
forum: General Help
---

### Post by krack3rz on 2011-01-17
so i fiddled with this for 2 days, and i give up...after reading and randomly troubleshooting nothing works.

just as title says, every time i try to login, it goes black, some text printed (.5 sec), then back to login box thing.

Info gathered on problem & steps taken:
-it happens in multiple kernels
-same if i log into another acc i made for just in case
-reconfigured Xserver-xorg
-reinstalled xserver-xorg
-uninstalled compiz
-uninstalled ibus, and installed
-updated, upgraded, dependencies fixed
-logs looked at, results: more confused...
-freed space, now using less than 12% hdd
-tried booting into licecd, could figure out wat to do tho
-banged head against wall
-checked "sudo chage --list usr_name" -->> all is ok
-restarted X server and pc multiple times (>10 times)

background info: using 10.04, latest everything
Problem: started randomly, not doing anything worth mentioning, no changes  in any options during and rite before failure (like i said randomly failed, cant remember how exactly i noticed -- prolly booted and cant login)

monitored syslog -- as soon as i try to login this is printed:
```

Jan 17 04:48:19 krack-bigbox-desktop acpid: client 2431[0:0] has disconnected
Jan 17 04:48:19 krack-bigbox-desktop acpid: client connected from 2431[0:0]
Jan 17 04:48:19 krack-bigbox-desktop acpid: 1 client rule loaded
Jan 17 04:48:22 krack-bigbox-desktop gdm-session-worker[2467]: pam_sm_authenticate: Called
Jan 17 04:48:22 krack-bigbox-desktop gdm-session-worker[2467]: pam_sm_authenticate: username = [krack]
Jan 17 04:48:22 krack-bigbox-desktop gdm-session-worker[2467]: pam_sm_authenticate: /home/krack is already mounted
Jan 17 04:48:22 krack-bigbox-desktop kernel: [ 1658.276236] type=1503 audit(1295257702.822:19):  operation="open" pid=2585 parent=2467 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/krack/.profile"
Jan 17 04:48:23 krack-bigbox-desktop acpid: client 2431[0:0] has disconnected
Jan 17 04:48:23 krack-bigbox-desktop acpid: client connected from 2642[0:0]
Jan 17 04:48:23 krack-bigbox-desktop acpid: 1 client rule loaded
Jan 17 04:48:24 krack-bigbox-desktop gdm-simple-greeter[2675]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow

```please help!!  ](*,)

Edit: dunno if it matters, my home directory is encrypted (only 1 user of 2)
I can log into ctrl + alt + F{1-6} 
currently logged into tty2, so i gots command line toolz
Also i can login with ssh from my other desktop and control thru nautilus (sftp)

---

### Post by krack3rz on 2011-01-17
seriously not even a single comment? is this uninteresting? or does no1 know? i tried following multiple ubuntuforums guides that are similar and none help...

---

### Post by krack3rz on 2011-01-17
tired of waiting...gonna try distro update 10.04 -> 10.10

---

### Post by krack3rz on 2011-01-17
> **krack3rz said:**
> seriously not even a single comment? is this uninteresting? or does no1 know? i tried following multiple ubuntuforums guides that are similar and none help...

so far still installing, found 2 errors, one of which was spammed on screen for a good min, twice.

1. (the spammed one) GdkPixbuf-WARNING -- Cannot open pixbuf loader module file /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders.cache - No such file or directory

2. some kind of failure and it requires purging...i dunno, may be normal...

---

### Post by krack3rz on 2011-01-17
so, in conclusion, it now works, thanks to no1 besides myself...and my rambling for no reason....

---

### Post by krack3rz on 2011-01-17
cant mark as solved, as this was an ignored problem with a stupid work around.
no problem solved....not even a bumb or dunno or blank post...all i did was get some beans xD

that was the only +, i should do this more often, to see how much i am ignored, and yes previously i was ignored in posts as well, given some links that told me nothing related to my problem....

---

### Post by krack3rz on 2011-01-17
:popcorn: so wats up dock?

---

### Post by krack3rz on 2011-01-17
> **krack3rz said:**
> :popcorn: so wats up dock?
i meant to write doc*

---

### Post by DanaLou on 2011-01-18
Well, I'll reply :)

Maybe there was a problem with the hard drive? Did you have to wipe it clean and do a complete re-install?

---

### Post by krack3rz on 2011-01-18
yay, thanx for replying :D :D :D
i dunno if it was HDD, i thought of running fsck but i couldnt go thru with it since it said: "WARNING!! ..." so i decided not to :(

but its fixed now, i tried many things and deduced that the problem was with system files, something that involves running of system as a whole, i mean at first even GRUB disappeared, then after restarting 5 times and uninstalling a bunch of things and running update-grub and booting from cd, only then GRUB menu appeared (also the setting wer set so that it appears no matter what HIDDEN_TIMEOUT was # out before all those changes)

so yah my adventures began thinking it was graphics or driver related

oops wrote too much :P

---

### Post by krack3rz on 2011-01-18
> **DanaLou said:**
> Well, I'll reply :)

Maybe there was a problem with the hard drive? Did you have to wipe it clean and do a complete re-install?

Thanx for replyin :D
heres some :popcorn: and a gold :KS

---

### Post by krack3rz on 2011-01-20
still nothin, i guess i'm invis. cool, :popcorn:

well i guess since no1 sees this i should mark as solved thread huh...maybe later wen some1 else says anything :D

---

### Post by rvndmnmt on 2011-01-28
Ran into the same problem.  I am using Kubuntu 10.04.1 and 10.10.  

I figured that it's an issue with kernel/driver compatibility since I encountered the same problem on the same computer with Fedora 14.  Never dug too far into it though.  I just loaded what I knew worked and plan on sticking with it.

No, your not invisible :P

---

### Post by dhysk on 2011-01-28
I know the feeling I have many posts with nobody in them but myself.  Alot of times it's just that knobody knows I guess.  It's not like I go around posting "sorry dude can't help ya".

---

### Post by primeminister37 on 2011-10-17
Don't know if anyone's still looking for answers, but for what it's worth: I've had this problem under Ubuntu 9.10, *but only if I have an external monitor plugged in*. Yes I know that probably sounds weird, but if the monitor is plugged in when I power up, Ubuntu gets stuck in its login loop, until I unplug the monitor; then the next cycle "takes" and I get logged in.

But a few days ago, this started happening without an external monitor connected. First time, I powered down/pulled the battery and then it came up fine (rebooting hadn't resolved it). Just now, it happened again, so I Ctrl-Alt-F3'd to a command-line, killed the X process, and when it restarted it logged me right in (I normally have auto-login enabled).

Am looking for a real solution now, since I no longer have a consistent workaround (unplugging the external monitor). Anyone here ever find a definitive solution?

This is happening on an ASUS EEEPC 1005AH, quite a few years old, and no, no known changes recently to the configuration etc.

  Thanks! -Nick

EDIT: I seem to have found a fix for this, at least in my case. I removed all (seemingly) unnecessary startup applications, including EeePC-related ones. Somewhere, that did the trick; I can boot up normally with a monitor plugged in yay! :)

---

### Post by domzo on 2011-11-25
Just had exactly the same problem on 10.04 LTS

Fixed it by removing the file gpg-agent-info-<MachineName> in /home/<user>/.gnupg


e.g.

~/.gnupg$ mv gpg-agent-info-<MachineName> gpg-agent-info-<MachineName>.backup


As other people have said, ctrl+alt+f4 (or f3 or ...) should get you to a terminal so you can log in and apply this fix.



solution as described here:
[https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574](https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574)


(although I am not 100% sure if it was the same underlying problem - I didn't investigate enough before trying the solution).

---

