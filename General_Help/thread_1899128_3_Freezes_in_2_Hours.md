---
title: "3 Freezes in 2 Hours"
date: 2011-12-22
forum: General Help
---

### Post by jmadero on 2011-12-22
Hi All,

I've now had 3 freezes in the last two hours running Ubuntu 11.10. Clean installed last night, home partition was kept in tact. Need help diagnosing as I can't have a "stable" machine freezing 3 times in two hours. What logs should I be looking in. Below is my xorg log, I don't see anything worth noting in it. Any other logs that I can provide I'll be happy to do so as this is now becoming a "I might have to switch back to Windows after 10 years" type of scenario, and that is definitely not ideal for someone who has abandoned all MS products for so long. Thanks in advance, really need some help here as I've never seen this before running Linux.

My definition of "complete freezes"

1. No mouse
2. No keyboard
3. Cntrl + alt + f1 = no response
4. Hard drive spins at the beginning (hard shut down makes this obvious)
5. If I wait long enough (couldn't say how long, this last time I gave it about 30 minutes) the hard drive stops spinning despite monitor being "on" but completely frozen


edit: just happened fourth time....hard drive stopped spinning almost immediately

---

### Post by Shompol on 2011-12-22
What was this computer running before? Is it a new PC? You mentioned Windows -- does it have the same problem under Windows? Knowing this would give a fat hint if this is a hardware issue or an OS issue.

If it old hardware, you might have better luck installing "stable" version of Ubuntu, like 10.04. You can also downgrade to 32 bit version and see if that helps.

I heard something about power management issues -- maybe try to disable power management features.

Sorry, don't know about logs, I favor the "brute force" approach :)

---

### Post by |{urse on 2011-12-22
Does this same behavior occur when booting to the livecd instead?

I'm trying to decide whether its ubuntu crashing on your hard drive or your hard drive crashing on ubuntu.

---

### Post by jmadero on 2011-12-23
Froze again, 5 times tonight

 It's not old or new (about 2 years), wouldn't know about Windows as I haven't had it installed on this system. It came with Windows but I removed it first day, no need for that garbage on my machine. I don't know about livecd, it's my daily machine so switching to livecd would be troublesome as I do a lot of things every day. I don't think it's a hardware issue, I'm going to install gnome-shell and see if that freezes as well. As far as what I have been running....internet browser (opera) has been running every time, but that could just be coincidence as it's usually on. Otherwise, nothing consistently has been running. Right now I'm running opera to type this and it hasn't frozen. Downgrading to 32 bit is also not ideal, I'd rather pinpoint the problem at least first. I am going to be installing my second distro (Bodhi) soon, I did this reinstall because I didn't like my partition setup. Before the reinstall I can say it had frozen "a few times" not nearly like this though.

---

### Post by 67GTA on 2011-12-23
I'm fighting the same bug. It is a kernel bug, but it randomly freezes HARD, with no logs being captured before/after to investigate. This started with 3.0. I'm running 11.10 with 2.6.39 ATM with no freezes. I haven't reported the bug because I'm not able to capture any logs. The only thing I've seen is red zeros filling up /var/log/syslog during the times it is locked up.

---

### Post by jmadero on 2011-12-24
I have reported a bug, clearly doesn't have much information but I'd like if you (67GTA) can add whatever you can to it. This is a serious serious problem and needs to be corrected so I'm going to do whatever I can to help the devs track it down. Appreciate you taking the time to add. 

Link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908335](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908335)

---

### Post by |{urse on 2011-12-24
Hah I wasnt suggesting that you use the livecd a's a permanent solution. I was suggesting that running off livecd for a few hours to see if your system still locks up will help you/us to diagnose your issue.

---

### Post by 67GTA on 2011-12-24
Hopefully I can add to it after Christmas. I'm going to try and connect to the locked machine with ssh and get a crash dump. The same bug is present in openSUSE 12.1 also.

---

### Post by 67GTA on 2011-12-24
You can install the 2.6.39 kernel for 11.10 from here for now: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39.4-oneiric/")
This bug didn't show up until 3.0.

---

