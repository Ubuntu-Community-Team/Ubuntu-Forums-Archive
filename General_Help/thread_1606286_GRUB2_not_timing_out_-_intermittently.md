---
title: "GRUB2 not timing out - intermittently"
date: 2010-10-26
forum: General Help
---

### Post by Jethro_uk on 2010-10-26
I have an ubuntu 9.10 machine I keep in the loft (attic) with the purpose of using it as a torrent/file server.

Currently I am experiencing no end of problems with it (Samba seems to "lock up" every so often) which seem to require a reboot[1]. Unfortunately, when I SSH in and issue a "reboot" command, the machine does reboot, but when it comes back, the GRUB timeout seems to have been disabled. So it sits there waiting for me to climb the ladder and press a key, before it reboots.

As you can imagine, this is a PITA. However, mysteriously, it doesn't happen all the time ... in fact when I *test* it, it never happens (which seems to indicate it is somehow connected to the problem which neccessitates the reboot[1]).

Googling, I saw a few people suggest that somehow a key is being pressed, which aborts the GRUB timeout. But that isn't the case here.

Ideally, removing the timeout, so GRUB boots immediately into the desired OS, is best. However I'd love to know what is causing this.

[1] Yes, I know it's not windows etc etc, but I am a Linux newbie, with no time to trawl through gigs of logfiles for some clue ...

---

### Post by NessDan on 2011-06-18
This exact issue is one I'm experiencing.

I have an older computer that I'm using as a web server. Since I thought something must have went wrong with the installation, I just reinstalled all of Ubuntu Server 11.04 and the issue remains.

I edited my /etc/grub.d/00_header file so that the timeout will always be 2 seconds and ran update-grub and update-grub2 afterwards. Still, the issue persists.

Does anyone know how to solve this?

---

### Post by tigerstripedcat on 2011-07-21
Same issue as you two.  (Really annoying when it's a headless server.) The other problem is that it is so intermittent.  This seemed to work for me (we'll see if it works long-term):

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/657871](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/657871)

---

