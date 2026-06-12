---
title: "Urgent, system updates crashing Gnome!"
date: 2006-06-14
forum: General Help
---

### Post by turbojugend_gr on 2006-06-14
Well, I 've turned on my pc, after 2 days of absence, and I seem to lost a gDesklet application launcher, anyway is some trouble to remake that but I will manage.

The real problem is that I have some Updates (which count up to 6) alert and when I click the icon to view them, Gnome -or Xorg?- crashes and I am THROWN at the log screen again????

I can install the updates by right clicking on the icon and choosing to update with no view but I am concerned that this may further crash my system! Another weird thing is from a glance I managed to have on the updates they seem to be KDE updates???? Being a Gnome user that makes me wonder!

Finally I have to add that I did some installment of the Engage (E17) bar, with no succes, following a forum's tutorial, I don't thing that's any relevant but it's the only thing I remember altering to my system recently, though I am sure I did at least one or two boots after that.

Plz help me I am stunned!

---

### Post by pjman on 2006-06-16
I am having a similar problem. Viewing updates crashes gnome... Only thing I've done to my system since last update is play around with encrypting emails and I installed seahorse.. I'm getting this error in my system log

```
Jun 15 23:21:54 ubuntu-larson1 gconfd (root-1547): GConf server is not in use, shutting down.
Jun 15 23:21:54 ubuntu-larson1 gconfd (root-1547): Exiting
Jun 15 23:26:45 ubuntu-larson1 gconfd (root-1939): starting (version 2.14.0), pid 1939 user 'root'
Jun 15 23:26:45 ubuntu-larson1 gconfd (root-1939): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 15 23:26:45 ubuntu-larson1 gconfd (root-1939): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 15 23:26:45 ubuntu-larson1 gconfd (root-1939): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 15 23:26:45 ubuntu-larson1 gconfd (root-1939): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 15 23:26:45 ubuntu-larson1 gconfd (root-1939): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
```


Thank you

---

### Post by DancingSun on 2006-06-16
I can confirm this, definitely sounds like a bug!

For me, clicking on the second item in the update list will crash Gnome and kick me back out to the login screen.  All other items that I've tried did not crash Gnome.

However, clicking the update button will still update the system without crash.

---

### Post by turbojugend_gr on 2006-06-16
[QUOTE=DancingSun]I can confirm this, definitely sounds like a bug!

For me, clicking on the second item in the update list will crash Gnome and kick me back out to the login screen.  All other items that I've tried did not crash Gnome.

However, clicking the update button will still update the system without crash.[/QUOTE]

thanx for your reply, I would like you to inform me, after update, are you ok???

If the problem continues regardless of updating, we should get some more attention on this..

---

### Post by dejay703 on 2006-06-16
Haha, same thing happened to me today.. i thought i was going crazy!

The window says that the system is building the dependancy list or something, and when it's almost done, it crashes...

sounds like a common problem

---

### Post by Maggot on 2006-06-16
Ditto here. Obviously a bug. I just manually do it via apt-get until its fixed

---

### Post by DancingSun on 2006-06-16
[QUOTE=turbojugend_gr]thanx for your reply, I would like you to inform me, after update, are you ok???

If the problem continues regardless of updating, we should get some more attention on this..[/QUOTE]
The updates are on the linux kernel and modules, and unfortunately, it screwed up my mouse, which uses the evdev driver for X (and needs a kernel module, not sure why the generic ones did not work).  Xserver would not start, so I had to revert back to the default mouse settings in xorg.conf.  After this change I can then boot into Gnome.

I then installed the newest kernel for AMD64 K8 (the upgrade only upgraded the generic kernel, and not the K8 one that I was using).  However, this wasn't enough as my nvidia driver broked and X would not start again.  I then boot back using the generic kernel, installed the newest restricted modules for AMD64 K8, reinstalled my nvidia driver and module, and even evdev (because I want to use all the buttons on my mouse).  This fixed all the problems and I am now back in business.

However, after the kernel update, I now have 51 various updates on Gnome and gtk...and that is making a bit nervous.

---

### Post by turbojugend_gr on 2006-06-17
Well, I have about 20 updates here, the problem still exists, any suggestions???

If I manually update will I be ok??? If not most propably I will go for a reinstall.

Post if you have a similar problem, the more we are the better the attention we 'll receive!

---

### Post by DancingSun on 2006-06-17
OK, I installed the 51 updates yesterday, and the new ones just released today, and so far I haven't experience any anomolies.

---

### Post by turbojugend_gr on 2006-06-18
Yap I manually updated and until now everything wporks like a grace again, no issues so far, except now Dapper is even more faster... hehe thought that wasn't possible!

---

### Post by pjman on 2006-07-26
I'm still getting this error whenever I view the updates available. Does anyone know how to fix this?

---

### Post by pjman on 2006-07-26
I've narrowed the problem to the Nvidia drivers. Does anyone have any suggestions on how I can pinpoint the problem in the drivers/configuration so I can find a fix?

My AGP card is a Ti-4200.

Thanks!

---

