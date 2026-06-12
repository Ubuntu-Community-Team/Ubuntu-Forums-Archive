---
title: "do-release-upgrade is not a command?"
date: 2009-10-19
forum: General Help
---

### Post by Amadameus on 2009-10-19
Hello everyone, so here I am, stuck again.

My hard drive crashed in a spectacular ball of flames (well, actually, it was more like a couple bad sectors and a slow corrupting death, but that's much less dramatic) and so, new hard drive in hand, I go about to install my OS again.

Turns out the latest version I had of *anything* was Kubuntu 6.06. I shrugged, and figured I'd just find a way to upgrade it until it was current. There had to be a way, right?

Turns out there is. I followed the instructions [here](https://help.ubuntu.com/community/EOLUpgrades/Dapper) to the letter, and everything worked fine until I reached the final bit:
```
sudo do-release-upgrade
```
My computer gave me a _bash: do-release-upgrade: command not found_ error!

This left me completely bushwhacked. do-release-upgrade is a command, obviously. What could cause Konsole to think that it isn't?

(Just in case anyone presents me with a blinding flash of the obvious, no I do not have the ability to burn CDs. If I had, that's the first thing I'd have done.)

---

### Post by -Zeus- on 2009-10-19
You could use ShipIt (shipit.ubuntu.com).  I have never seen that command, and I wouldn't think that it's even possible to upgrade from 6.06.

---

### Post by P4man on 2009-10-19
you have to install "update-manager-core" package first
But frankly, you re better off downloading and burning a more recent version, as you dont really have an existing install anyway.

---

### Post by slakkie on 2009-10-19
> **Amadameus said:**
> Hello everyone, so here I am, stuck again.

My hard drive crashed in a spectacular ball of flames (well, actually, it was more like a couple bad sectors and a slow corrupting death, but that's much less dramatic) and so, new hard drive in hand, I go about to install my OS again.

Turns out the latest version I had of *anything* was Kubuntu 6.06. I shrugged, and figured I'd just find a way to upgrade it until it was current. There had to be a way, right?

Turns out there is. I followed the instructions [here](https://help.ubuntu.com/community/EOLUpgrades/Dapper) to the letter, and everything worked fine until I reached the final bit:
```
sudo do-release-upgrade
```
My computer gave me a _bash: do-release-upgrade: command not found_ error!

This left me completely bushwhacked. do-release-upgrade is a command, obviously. What could cause Konsole to think that it isn't?

(Just in case anyone presents me with a blinding flash of the obvious, no I do not have the ability to burn CDs. If I had, that's the first thing I'd have done.)

You haven't read the main page of EOLUpgrades, you need to:
```

sudo aptitude install update-manager update-manager-core

```

---

### Post by Amadameus on 2009-10-20
@slakkie: Thanks very much!

I installed update-manager and update-manager-core successfully, then performed do-release-upgrade successfully.

Or so it would seem.

Terminal went through the installation and I restarted the computer, but when I came back on it told me that _cat /etc/issue_ was 6.06.2, just like always.

**What the hey?!?**

(Just saying it again, I appreciate the obvious advice for boot CDs and burning boot CDs. I know this. I have no optical drives mounted on this rig and cannot burn CDs. Even if I could, there is an Ubuntu-supported upgrade from 6.06 to current. If it's there, it should work.)

---

### Post by slakkie on 2009-10-20
> **Amadameus said:**
> @slakkie: Thanks very much!
Terminal went through the installation and I restarted the computer, but when I came back on it told me that _cat /etc/issue_ was 6.06.2, just like always.


That seems weird indeed. Could you run lsb_release -a? And apt-cache policy base-files?

---

### Post by P4man on 2009-10-20
> **Amadameus said:**
> 
(Just saying it again, I appreciate the obvious advice for boot CDs and burning boot CDs. I know this. I have no optical drives mounted on this rig and cannot burn CDs. Even if I could, there is an Ubuntu-supported upgrade from 6.06 to current. If it's there, it should work.)

then use a usb stick. upgrades are great if you got a complicated setup you want to preserve, but even then there are problems with each distro upgrade, if nothing else, garbage that doesnt get removed. To give one example, just upgrading from 8.04 -> 8.10 -> 9.04 will result in having 3 different updatedb scripts running simultaneously in the morning, rendering your computer mostly unusable for several minutes.

Since you're doing a fresh install, you're really making things hard for no obvious reason. Download a recent iso and put it on a USB stick. Boot from stick, install, done. No garbage, no multi gigabyte downloads, no half day of downloading and upgrading.

---

### Post by slakkie on 2009-10-20
> **P4man said:**
> To give one example, just upgrading from 8.04 -> 8.10 -> 9.04 will result in having 3 different updatedb scripts running simultaneously in the morning, rendering your computer mostly unusable for several minutes.


Right, you will also have 3 instances of cron running etc etc, 3 instances of postfix, etc etc. This is so not true.

---

### Post by P4man on 2009-10-20
> **slakkie said:**
> Right, you will also have 3 instances of cron running etc etc, 3 instances of postfix, etc etc. This is so not true.

Im afraid it is true, no need for a strawman argument. i dont remember the names, but there was like an updatedb run from /etc/cron.daily/mlocate and /etc/cron.daily/update and a third script I dont recall. I ve seen plenty of posts of ppl complaining jaunty crawled to a halt after booting and it was always ppl who did a dist upgrade and having several updatedb scripts running simultaneously.

edit: have a look here:
[http://hightechsorcery.com/2008/11/cleaning-updatedb-cron-jobs-ubuntu](http://hightechsorcery.com/2008/11/cleaning-updatedb-cron-jobs-ubuntu)

that was pre jaunty. Upgrading to jaunty added another one iirc.

edit 2:
[http://shallowsky.com/blog/tags/boot/](http://shallowsky.com/blog/tags/boot/)
a quote:
> Worse, if I install mlocate (so slocate will work) and then look in my cron directories, **it turns out I now have, count 'em, five different cron scripts that run updatedb**.

---

### Post by slakkie on 2009-10-20
> **P4man said:**
> Im afraid it is true, no need for a strawman argument. i dont remember the names, but there was like an updatedb run from /etc/cron.daily/mlocate and /etc/cron.daily/update and a third script I dont recall. I ve seen plenty of posts of ppl complaining jaunty crawled to a halt after booting and it was always ppl who did a dist upgrade and having several updatedb scripts running simultaneously.

edit: have a look here:
[http://hightechsorcery.com/2008/11/cleaning-updatedb-cron-jobs-ubuntu](http://hightechsorcery.com/2008/11/cleaning-updatedb-cron-jobs-ubuntu)

that was pre jaunty. Upgrading to jaunty added another one iirc.

edit 2:
[http://shallowsky.com/blog/tags/boot/](http://shallowsky.com/blog/tags/boot/)
a quote:

I wonder what they did, I never seen that happen on any of my boxes. Perhaps they did not remove/purge unneeded packages after the dist-upgrade/do-release-upgrade. All I can think of..

---

