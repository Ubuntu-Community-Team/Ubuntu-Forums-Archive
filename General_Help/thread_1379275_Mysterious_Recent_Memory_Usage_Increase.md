---
title: "Mysterious Recent Memory Usage Increase"
date: 2010-01-12
forum: General Help
---

### Post by trifthen on 2010-01-12
I've looked around for this on the forums and Google and can't find anything but it's pretty new.

Recently I noticed my system was using more memory than I seemed to remember from the past. At first, I thought this was a general memory leak, but then I did this:

```

ps axo rss,command:50,pid | sort -n

```

Hmmm... those RSS totals aren't accounting for about 500MB of the used memory. Something fishy going on. Time to reboot!

After rebooting, ctrl-alt-f1, log in, and:

```

sudo system gdm stop
free

             total       used       free     shared    buffers     cached
Mem:       2016984     761844    1255110          0        988     144416
-/+ buffers/cache:     607580    1409404
Swap:      2104472          0    2104472

```

Huh!? Usually, even with GDM and an Xserver running after reboot, this was below 200MB. Now, even with everything off, it's over 600MB after subtracting buffers and cache? What? I'm reluctant to call it a leak, since it happens right after a reboot and stays that way afterwards. Something is allocating about 500MB and just not letting go, but why?

Any ideas here?

---

### Post by trifthen on 2010-01-12
After more digging, this is related to [Bug 501715]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715"), and is completely irritating because I rebooted several times, but of course, after running an apt upgrade, which deletes the existing ureadahead pack and renders the next memory report invalid.

So as a PSA for others, and I can't yell this loudly enough:

> If you upgrade any packages on Karmic and then reboot, **reboot again** or you might have 500MB or more mysteriously allocated and unusable by the rest of your system! If you see any weird or unexplained memory usage that isn't cache or buffers, reboot twice right now!

This is, IMO, a *terrible* bug, because it's both insidious and makes Linux feel like Windows, where rebooting is the best way to solve all your woes. But in this case it's worse, because it doesn't [solve them]. No, you have to reboot twice now, with really no explanation. Can we get people to go in and vote this bug up?

---

### Post by Sef on 2010-01-12
Run top in the terminal.   It shows how much cpu and memory are being taken by what application and other processes.

---

### Post by philinux on 2010-01-12
> **trifthen said:**
> After more digging, this is related to [Bug 501715]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715"), and is completely irritating because I rebooted several times, but of course, after running an apt upgrade, which deletes the existing ureadahead pack and renders the next memory report invalid.

So as a PSA for others, and I can't yell this loudly enough:



This is, IMO, a *terrible* bug, because it's both insidious and makes Linux feel like Windows, where rebooting is the best way to solve all your woes. But in this case it's worse, because it doesn't [solve them]. No, you have to reboot twice now, with really no explanation. Can we get people to go in and vote this bug up?

Why dont you change the status of the bug to confirmed. It,'s at new. Just click the new button and change it's status.

---

### Post by trifthen on 2010-01-12
> **philinux said:**
> Why dont you change the status of the bug to confirmed. It's at new. Just click the new button and change it's status.

Still waiting for my account request email to come in. I intend to do just that.

---

### Post by trifthen on 2010-02-05
I had thought rebooting a couple times would fix this, but alas, with the latest kernel, four reboots later and it was still using 350MB (after subtracting buffers and cache) immediately after booting.

So, I removed sreadahead and ureadahead. Suddenly my system uses 80MB after booting. I'm fairly certain that either sreadahead or ureadahead is horribly flawed somewhere. Until Ubuntu fixes it, I'll put these packages on my list of things to uninstall immediately after a release upgrade.

---

