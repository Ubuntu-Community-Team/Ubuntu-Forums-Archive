---
title: "Updates being installed without permission"
date: 2010-05-25
forum: General Help
---

### Post by dvdram on 2010-05-25
I noticed this today for the second or third time since getting 10.04: all my machines are installing security updates automatically, despite the fact that KPackageKit is set to 'only notify about available updates.'

Am I just being stupid, missing a setting somewhere, or is this a bug? Aside from the fact that I like to know what's being installed, I often use my laptop on satellite or other bandwidth-metered connections (as was the case when it happened today), and I don't want the OS to start dictating how much I owe my ISP at the end of the month!

Thanks,

Alex

---

### Post by Lion-san on 2010-06-02
You aren't the only one seeing this.  I just caught it installing  security updates without asking, or needing a sudo password.

I see in KPackageKit where you can set it to "Install security updates  without confirmation", but I do not have it selected.  It's set for  "Only notify about available updates".

This needs to get fixed.

(Edit:  Looks like Kubuntu sets it up to put KPackageKit as always allowed in kwallet, which is annoying, so I've zapped that.  Too early to say if that'll actually fix the problem, though.)

---

### Post by Lion-san on 2010-06-03
Nope, that doesn't stop it.  Caught it doing it again.

KPackageKit history shows kpackagekitsmarticon as the program doing it, so I'm just renaming and chmoding it for now.  It was trying to install a new kernel this time, no less.  Not exactly what I want to happen without permission.  Might be time to check in to gNewSense again.

---

### Post by Dave.G on 2010-06-04
Happened to me too, and while I caught it and canceled it the first time it did it again before I could stop it today. I think it actually updated the kernel packages automatically *twice in a row*. The first updates downloaded and applied included the kernel packages and snmp packages, after which point I got a notification asking for a restart, then it right away seemed to download and apply the kernel packages' updates again with another restart request afterwards. (no snmp the second time, according to the KPackageKit history)

Any ideas? One of us need to file a bug report?

---

### Post by dvdram on 2010-06-04
Yes, did it again for me today. I'm surprised that this topic hasn't received a lot more attention, which is what made me think I might be missing something in the configuration.

It looks like a bug report is in order; I couldn't find an existing one for either KDE or Kubuntu. I don't have any other distros running at the moment though, so I'm not sure if it's a KDE4 problem or something Kubuntu-specific. Can anyone confirm?

---

### Post by 7th on 2010-06-05
Just got around to googling this myself after my laptop installed a kernel update without asking for permission or a password, the first I knew of it was when the notifier asked for a reboot :confused:. When I checked the settings for updates (software sources - weekly updates with ask for permission for all) it seems to be ignoring my preferences. :(

Did find a bug report on launchpad though

[https://bugs.launchpad.net/ubuntu/+source/kpackagekit/+bug/559364](https://bugs.launchpad.net/ubuntu/+source/kpackagekit/+bug/559364)

---

### Post by dvdram on 2010-06-05
> **7th said:**
> Did find a bug report on launchpad though

[https://bugs.launchpad.net/ubuntu/+source/kpackagekit/+bug/559364](https://bugs.launchpad.net/ubuntu/+source/kpackagekit/+bug/559364)

Ah thanks, several searches of Launchpad and I still managed to miss that!

---

### Post by CloneSan on 2010-06-14
Same problem here: updates in kubuntu 10.04 are applied automatically, but the option to do so in kpackagekit is turned off (only notify about available updates is checked) .

The bugreport(s) mentioned above don't seem to get a lot of priority/attention as far as I can see. Weird, since this is really, really bad behavior for any production system (like my work laptop).

---

### Post by Onychophoran on 2010-06-15
Seriously, this is not appropriate update behavior.  I'm testing Lucid Lynx on my personal system and there is no way I'm recommending it for anyone until this issue is resolved.

---

### Post by Lion-san on 2010-06-29
Great.  Getting rid of kpackagekitsmarticon is only a temporary fix.  One of the other recent updates put everything back in place, so I caught it doing another unauthorized update again today.  Guess I'll need more drastic measures.

This wouldn't be nearly as frustrating if kpackagekit appeared to actually have a text config file, like any normal linux program.

(Side note: Hate having to allow yahooapis.com javascript to post to this forum)

---

### Post by Dave.G on 2010-07-05
I just got a forced automatic security update again, coincidentally followed by an optional update that claims to fix said unwanted automatic updates. Looks like the bug it's originating from is:

[https://bugs.launchpad.net/ubuntu/+source/kpackagekit/+bug/586497](https://bugs.launchpad.net/ubuntu/+source/kpackagekit/+bug/586497)

Someone should forward dupe 559364 there, then. Hopefully this is fixed now.

---

