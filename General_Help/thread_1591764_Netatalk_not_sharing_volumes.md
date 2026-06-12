---
title: "Netatalk not sharing volumes?"
date: 2010-10-09
forum: General Help
---

### Post by BrutalSpoon on 2010-10-09
Hi everyone,

So, I've mostly set up my new server. It's awesome. Got the RAID running with a few minor kinks which won't take long to sort out concerning auto-loading which has to do with drive letters; however, I've run into a bit of a problem with file sharing.

I'm trying to set up AFP to talk with the numerous Macs in my house. I managed to get it working in a VM on my other computer without any hassle, but for some reason I can't get it to show anything other than the preset Home Directory folder for each user, even when logged in as the same user as the one logged in on the server.

I've checked everything in /etc/default/netatalk and /etc/netatalk/afpd.conf. Everything is the same as in my VM. All the avahi settings are correct, and all the Macs can see the server just fine. User permissions are all working as they're supposed to.

As far as I can tell this means that my problem must lie within the /etc/netatalk/AppleVolumes.default file.

This is the list of shared volumes in the file:
```
# By default all users have access to their home directories.
~/			"Home Directory"
/media/MainRaid/MainData "Media Server" cnidscheme:cdb options:usedots
/media/MainRaid/TimeMachine "Time Machine" cnidscheme:cdb options:tm,usedots,upriv
```

I've double checked and triple checked all the paths; they're correct. I've tried removing each variable/option to no available. There's no reason that I can see why it shouldn't be sharing.

Could somebody please shed some light on this situation? I'm at a loss and it's starting to get really frustrating.

Thanks in advance for any advice (as always),
BrutalSpoon

---

