---
title: "kde Autostart shutdown"
date: 2009-12-08
forum: General Help
---

### Post by peterroots on 2009-12-08
Can anyone explain the following?
In Kubuntu 8.04 if I wanted a script to run at start up I put it (or a link to it) in ~/.kde/Autostart
If I wanted a script to run on shutdown I had to create a folder ~/.kde/shutdown and put my script or link there.

Under Kubuntu 9.10 there is a autostart icon in systems settings that lets me select scripts (or programs) and select if I want to run them at startup or shutdown  - very nice and friendly.
~/.kde contains both Autostart and shutdown, no surprise there I thought, but I just found that a link to a script I set to run at startup and one I set to run at shutdown are both in Autostart.

Now as the start up script mounts a samba share by smbnetfs and the shutdown script unmounts it I would expect to have no share if the start script ran and then the stop scrip ran but I do have a share so just a bit odd.

No big deal, just seems odd even though it works as intended (by me)

---

### Post by peterroots on 2009-12-08
OK forget all the above - a total load of rubbish!

I entered a script in the autostart dialogue, and selected 'startup'
I entered another script in the same dialogue and selected 'shutdown'

I checked it all
I restarted my computer
I checked my shares were available (as done by startup script)
Later, while doing the same on an 8.04 setup I checked in .kde to see what I had there on my 9.10 setup
Then I got puzzled and wrote the above.
Then I went back to autostart and found both my scripts now showed as being run on startup.
I changed the wrong one and now the links are just where I would have expected them to be.

Put it down to one of those 'was it me, was it the computer, am I under attack by gremlins?' sort of things.

---

