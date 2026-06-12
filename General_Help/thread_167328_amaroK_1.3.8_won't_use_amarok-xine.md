---
title: "amaroK 1.3.8 won't use amarok-xine"
date: 2006-04-28
forum: General Help
---

### Post by jomtois on 2006-04-28
EDIT:  Problem solved -- a reboot fixed it, I do not know what step I took along the process that caused that to happen?? Anyway, thanks if anyone was going to reply.
==
Hello,

I am new to Kubuntu, but generally computer savvy.  I have searched extensively and not found a solution to my problem.

My problem is I cannot seem to get amaroK to install any additional engines besides gstreamer.  I have installed amarok-xine and any other engine I could find in the repositories, and none ever show up in the Settings => Configure amaroK => Engine menu.  I have unistalled and reinstalled amaroK countless times, and even upgraded to 1.3.8 from the 1.3.7 it was defaulted to (use KDE 3.5.2).

I even searched my entire / (and subdirs) for amarok* after (I had completely removed all amarok stuff thru synaptic) and deleted any file it found and that did not work either.

I had no problems with this on my previous install of Ubuntu but I just wiped the drive and installed kubuntu fresh from the cd a couple of days ago and now cannot get xine.  It seems like no one else is having this problem?  What am I doing wrong?

amarok-gstreamer engine plays my music, but I would prefer xine.

Thanks in advance

Jon

---

### Post by awakatanka on 2006-04-28
Do you also have the right sources.list entry's?

For the right entry's try [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Also for mp3 playback you need the libxine-extracodecs. and maybe w32codecs

edit : damn didn't see youre edit ;)

---

