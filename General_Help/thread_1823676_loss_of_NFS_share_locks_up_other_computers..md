---
title: "loss of NFS share locks up other computers."
date: 2011-08-12
forum: General Help
---

### Post by rountrey on 2011-08-12
I have searched around but can't find a decent solution that works, and I don't like doing hard resets on raid systems (holding down the power button). Here's the problem, I have an older system that I use as a bulk downloader/encoder/nfs server (calling this A), it's nfs drive is shared with two other computers: media server (B) and desktop (C). B and C have UPS's on them, A does not, so when there is a power outage even for a second then A drops out, disconnecting nfs to B and C. This in turn will freeze B and C (no keyboard, mouse, basic computer coma) and I have to do a hard reset on both. Even when A comes back up the others are still frozen.

I wouldn't worry about this so much but the media server is a raid system and I don't like the dangers of having it freeze in the middle of a write. 

If you need more:

---B: Raid w/ UPS
|
|
------------------A: NFS w/ A&B, no UPS
|
|
----C: desktop w/ UPS

If it matters A and C are Ubuntu 10.04, B is Debian 6.

---

### Post by aeiah on 2011-08-12
you'll probably always get a bit of a hiccup, if the nfs is mounted somewhere currently being accessed by the client. what are your fstab settings for the nfs mounts on the clients?

have a look at the option flags: 'soft', 'sync' and timeout options

---

### Post by rountrey on 2011-08-12
all default but I'll look into that stuff

192.168.0.13:/media/working  /media/working  nfs  defaults  0  0

---

### Post by gsgleason on 2011-08-12
You might try adding _nefts and soft to the mount options.

---

### Post by gordintoronto on 2011-08-12
Have you considered samba?

---

### Post by rountrey on 2011-08-13
I use samba for my HTPC (it's Windows, couldn't get MythTV to work right). In my home network I have found that with samba I only get about 45 to 50% of network speed, with NFS I can get about 90 to 95%. I could use samba but I prefer native *nix protocols when all but one of the computers in the house are Linux or BSD. I have put in the soft option, but not the nefts yet, because I haven't tested the soft option yet.

---

