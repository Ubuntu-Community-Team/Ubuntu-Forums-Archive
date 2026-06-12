---
title: "File System Won't Remount After Brute Shutdown"
date: 2011-04-10
forum: General Help
---

### Post by dystope on 2011-04-10
Ubuntu use history:  Used Ubuntu intermittently since v6.   Now using v9.1 on a netbook.

User proficiency rating:  Dunce.

Ubuntu issues history:  Rare / always minor / always solved with one visit here.

Problem (never happened before):
- Firefox hung indefinitely while it was loading (no prior issues, no recent changes).  
- All "escape" options failed - couldn't unfreeze the firefox window, couldn't close the firefox window, couldn't minimize the firefox window, and couldn't get the system to respond to the cursor or keyboard. 

Dunce reaction:
Hard shutdown via the netbook's power button.

Subsequent boots produce only one result (I have a "screenshot" if necessary to resolve this).  

Truncated screen return follows in bold font:

[B]Maintenance shell will now be started
Control-D will terminate this shell and re-try
Give root password for maintenance[/B]

*- My root password didn't work, then the same message as above repeats itself on-screen*.
- *Out of desperation, I execute the only other option offered - Control-D - which produces*:

[B]mountall start/starting
fsck from util-linx-ng 2.16
/dev/sda1: Superblock last write time is in the future (by less than a day...)
[/B]
*... *which is followed by a dozen and a half lines of techno-babble, ending with:

[B]mountall: fsck / [1022] / terminated with status 4
mountall: Filesystem has errors: /
init: mountall main process (1018) terminated with status 3
Mount of filesystem failed.[/B] 
[B]A maintenance shell will now be started.
Control-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):[/B]

... which again leads back to my failed starting point.

I have only let the system boot on it's own, making the above attempt in generic mode:  NOT recovery mode.  I have NOT accessed F2 settings or anything else.   That's as far as I've taken it before asking for help.

I can provide a screenshot (cell phone cam image) of the full screen on request, if provided with instructions on how to upload it.

Thank you in advance for any assistance.


Dystope

---

### Post by TeoBigusGeekus on 2011-04-10
Boot up with a live cd/usb and try to scan and fix your drives
```
sudo fsck /dev/sda1
```
fsck will scan for errors and attempt to fix them.
You can do this for all your partitions once you get into a live system.

The next time an app freezes, open a terminal and give
```
killall nameofapp
```
and if that doesn't do it, give it the kill signal
```
killall -s 9 nameofapp 
```

---

### Post by coffeecat on 2011-04-10
@dystope, although the maintenance shell tried a fsck, +1 to TeoBigusGeekus' suggestion to run fsck from a live CD/USB.

This doesn't help the immediate problem, but this link below for your bookmarks. It's how to shutdown or reboot gracefully  when and if your system freezes solidly.

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)

On some keyboards/systems you need the AltGr key to the right of the spacebar rather than the alt key to the left. Other systems seem to be happy with the regular alt key or both.

---

### Post by dystope on 2011-04-10
@TeoBiggus + @CoffeeCat

Loud and clear on all counts.  Profuse thanks.

If you hear loud crashes, thuds and bangs, that's me fumbling around with how to download 9.1 onto a USB, and how to boot with it.

Dystope

---

