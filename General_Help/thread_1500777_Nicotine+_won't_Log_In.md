---
title: "Nicotine+ won't Log In"
date: 2010-06-03
forum: General Help
---

### Post by gwaar on 2010-06-03
I've recently installed Nicotine+ (v.1.2.14 edit: v.1.2.15 doesn't work either) and cannot connect to either the old server (port 2240) or the new server (port 2242). Nicotine seems to get stuck with the message, "connected to server server.slsknet.org:2240, logging in..." 

I've tried museekd and the related clients as well (Murmur and Museeq+) and neither of those seem to be able to connect as well. Neither does any version of soulseek I've tried to run in wine (157NS13c, 157NS13e, 156c), though I allow that that could be a different problem entirely.

I don't believe it's a problem with my ports because I can connect to soulseek on my windows machine with no extra setup, and the ports I use pass the port status test within nicotine+ itself.

It seems other people have had this problem intermittently, and though I realize soulseek and it's related clients aren't the most popular applications anymore, I'd be grateful to anyone who could help me out. Thank you.

---

### Post by cascade9 on 2010-06-04
This is what I would do, as I've seen bad config files will stop nic from opening. 

Backup your .nicotine folder (hidden files, in /home) and then delete the version in /home. Start Nicotine, and then it should be back to a vanillia version, enter a new username/password, and it should start. 

Yes, you wil lose all your settings, but you can either compare the dodgy config file and copy over the relevant bits, or you can try to fix the old config file.

*edit-  could be totally wrong on the config files, but hey, its worth a shot....

---

### Post by gwaar on 2010-06-04
Thanks for the reply, but it seems that the config files aren't the problem; removing the files and getting a clean setup didn't help. The message remains the same as in my first post. 

I wish I could give a more specific set of symptoms because I'm not sure exactly where the problem is unfortunately. There don't seem to be any bugs in the program that are showing up - even seeing all the debug output, there's nothing beyond what I gave before. 

On a possibly related note, I have a little message on the status bar that says, "2/921 connections." I'm not sure exactly what those connections would be to, since I can't actually be downloading. My thought is that it would be the server, but it seems as though I'm not really connected to that either.

---

### Post by alinux.deb on 2010-07-20
Found the same problem here with 1.2.14 and 1.2.15. Clean config files or re-installations don't work either.
Is anybody finding the same problem? Could it be a bug?

I'm using Ubuntu 10.04 by the way.

I might try to use the official soulseek client under wine, though I'm pretty unexperienced with wine tweaking. I'll post anything relevant if I succeed.

---

