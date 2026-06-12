---
title: "Auto-Mount Windows Shares"
date: 2011-01-11
forum: General Help
---

### Post by swraman on 2011-01-11
Hi.

Im setting up a Mythbuntu box as a HTPC, and I want to be able to stream my media from my Windows box to the Mythbuntu box.

I got the windows shares mounted fine, everything works.  But I want them to auto mount so I modded my /etc/fstab file to mount the share.

The problem is the Mythbuntu box uses wifi, and during boot the computer can't connect to the Windows box, and it hangs on 

> Error while mounting /blah/blah/ press s to skip or m for manual recovery

and I am planning on not having a kbd hooked up to this computer once it is done.

My Questions:

1) Is there a better way to auto mount Windows shares - one that does the mounting after the computer is booted up?  Furthermore, the Windows box may be off, so I want it to just skip the mounting on error.

2) Right now when I mount the share, I have to specify the Windows computer by its IP address.  If I do it by PC name, it doesn't work, says it can't find the computer.  Is there a way to mount using the computer name, so that if my router decides to give the windows box a new IP I wont have to reload everything?

Thanks

---

### Post by swraman on 2011-01-12
I ended up just making a bash script that mounted the drives, and attempted (unsuccessfully) to get it to run at startup.

Its OK though, I ran into another problem with this HTPC setup (no audio on HDMI out) so I ended up using Windows.

Sad, I would run so many more Ubuntu machines if manufacturers made linux drivers...

---

