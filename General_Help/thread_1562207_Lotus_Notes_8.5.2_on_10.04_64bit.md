---
title: "Lotus Notes 8.5.2 on 10.04 64bit?"
date: 2010-08-27
forum: General Help
---

### Post by omniphil on 2010-08-27
With the release of Lotus Notes 8.5.2, it looks like Ubuntu 32bit support is there, however I am running 64bit Ubuntu 10.04.

I had 8.5.1 (32bit) installed and it was working fine. I did take alot of tweaking to get it running.

Just wondering if anyone has tackled the new 8.5.2 which is supposed to be much nicer in Ubuntu.

I've tried removing the old 8.5.1 and the install for the 8.5.2 doesn't really work correctly even with "--force" commands.

Always a challenge with Notes and Ubuntu :(    Why they didn't make 64bit debian packages is beyond me...

Thanks for any help!

---

### Post by omniphil on 2010-08-30
Well, after a few days, I got it running. I'm not sure how to do it from scratch, but I had to rip out the old 8.5.1 and then reinstall 8.5.1 without any fix packs (8.5.2 wont upgrade with fix packs install for whatever reason) Once I had plain 8.5.1 running then the 8.5.2 install could be run using the -force-all command and it upgraded right over.

So basically, follow the how to's on getting 8.5.1 working with 64bit 10.04 (there's some libraries and dependencies that you need as well), But don't install any fix packs, then just run the upgrade with the 8.5.2

Make sure to backup your "lotus" folder in your home directory before ripping everything else out, so you can put it back later and be up and running.

---

### Post by jdos2 on 2010-09-07
I'm stuck RUNNING Notes on 64 bit machines. I've a laptop that behaves very well, but if I connect to work through my Cisco VPN client and try to use Notes... Well, the Calendar and Sametime work fine, but as soon as I touch the mail tab, the computer freezes SOLID. No blinking lights, no more response to the network, nothing. The second screen in a xinerama session goes dark... And that's it. Hard/cold reboot will bring it back.
Haven't found the answer to that yet...
This is both Ubuntu 10.04 and Fedora 13, and Notes is a TON easier to get running on Ubuntu.

---

