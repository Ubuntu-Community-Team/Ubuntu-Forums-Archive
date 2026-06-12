---
title: "Startup problems from running out of space on new /home partition"
date: 2010-01-25
forum: General Help
---

### Post by kudzu on 2010-01-25
Hey everyone,

I'm a pretty new user.  I re-did my partitions; I deleted Windows, expanded my main Ubuntu partition and created a /home partition using the psychocats guide.  Unfortunately, I'm an idiot, and I made my /home partition smaller than the actual amount of data that I had in my /home folder, which proved to be a problem after copying my /home folder over to my /home partition.  I then got an error on startup: "Could not update ICEauthority file /home/*username*.ICEauthority."  I re-did my partitions, expanding my /home partition well beyond the amount of data that I had mistakenly copied from my /home folder (from about 10GB to 40GB, I believe I had roughly 10GB in my /home folder) and then followed the psychocats solution for this problem (chown and chmod), only to be confronted with more problems at reboot: 

- The same ICEauthority problem
- "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)" 
- "Nautilus could not create the following required folders: /home/*username*/ Desktop, /home/*username*/.nautilus.  Before running Nautilus, please create these folders or set permissions such that Nautilus can create them."

And although Ubuntu boots and lets me log in, the task bar doesn't appear.

I'm currently running the psychocats last-resort solution (sudo cp -R /recovery/home_bakcup /recovery/home) from the live cd terminal, but the process has been going on for a while now and I don't really know what's happening.  UPDATE: I finished the process, rebooted, and it didn't fix any of the three problem messages.

This problem seems to be documented on the Ubuntu bug site:  [https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215)

One poster, Colin Watson, said: 
                 "This may not be why it happens to everyone, but during beta ISO testing I noticed that this happens if you run out of space on /home. This is a regression of some feature work done in a previous release to make sure the user can always log in even if they run out of disk space (the overflow-tmpfs-on-/tmp init script).
 I dug into this a little bit. The cause is that an attempt to mkdir $HOME/.gconf fails due to ENOSPC. This is in the resolve_address function in backends/xml-backend.c, called via gconf_resolve_address from the check_gconf function in gconf/gconf-sanity-check.c."

But I don't know what that means, and I can't see any solution in there.

Can anyone give me any suggestions?

Thanks.

---

### Post by kudzu on 2010-01-25
Oh, and I forgot to mention - when I was only getting the .ICEauthority problem message I could still access my task bar, but there was no sound.  The volume icon never appeared.  And for some reason, the Google toolbar in Firefox wouldn't work.

---

### Post by kudzu on 2010-01-25
Bump!

---

### Post by kudzu on 2010-01-25
No advice?  I'd hate to have to start over with a clean install.  I had just gotten everything the way I liked it.

---

### Post by bdoe on 2010-01-25
Sounds like a massive file permissions problem to me.

Open a terminal and type:

[COLOR=Black]chown -R username /home/username [COLOR=SeaGreen](where "username" is your login name. This changes the owner of all files in your home directory, recursively, to you. You should be the owner of everything in your home directory)
[COLOR=Black]chmod -R 700 /home/username [COLOR=SeaGreen](where "username" is your login name. This gives you full permissions on all files in your home directory, while denying permissions for everyone else.)
[COLOR=Black]chmod 644 /home/username/.dmrc [COLOR=SeaGreen](this is a special case. The system needs read access to this file, otherwise you'll encounter problems when logging in).

[COLOR=Black]This should hopefully straighten you out.[/COLOR]
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by kudzu on 2010-01-25
EDIT: Hey, that worked!  Thanks a ton!  Everything seems to be working now.  Is there anything else I need to do to my system now that I'm logged in and everything?

---

