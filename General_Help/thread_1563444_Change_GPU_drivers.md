---
title: "Change GPU drivers"
date: 2010-08-29
forum: General Help
---

### Post by ultimate_aektzis on 2010-08-29
Hi all,

The last few months I have some problems with rendering.Sometimes even scrolling in sites is going slow!!!At first I thought that it was RAM's problem or hard disk's but it's not.So, I want to check for GPU frivers.I have an Nvidia 7650 AGP but I don't remember which drivers(open source or official ones).So I would ask for some help on the following:

Check the kind of drivers I have, reinstall them and install a newer version or the other kind.

Thanks in advance:)

---

### Post by varunendra on 2010-08-30
I'm not sure if I've understood your post correctly, but if it's just that you want to diagnose what driver(s) you are currently using, then perhaps these may help you:
```
lspci -v
```
and
```
lsmod
```

Make sure all the repositories are enabled in **Software Sources**, all the update options are enabled under 'Updates' tab, then try updating the system via Update Manager.

Also, check under **System>Administration>Hardware Drivers** (again- not sure if the path is same for hardy) whether there is any proprietary driver available/in-use for your AGP card. Try toggling it if there is any.

Maybe you've already tried this all, but as I said above, I'm not sure if I've interpreted your post correctly. So am suggesting what I guessed might be relevant.

Also, why don't you try Live CDs of Karmik/Lucid to see if your specs (I'd like to know what) are supported any better in them?

---

### Post by ultimate_aektzis on 2010-09-01
Hi, thanks for the answer and sorry for the delayed replay.You've guessed correctly and the instructions are correct

I checked them, and I have the proprietary drivers...the reason I dont check if I have better support in other is that the "slow scrolling problem" doesnt appear in certain times.Do you think that there are updated drivers in newest versions?

---

### Post by varunendra on 2010-09-01
Oh, that is certainly something you'll have to determine by yourself! If an updated version exists in the repositories or on their official site, it is always expected to be better than earlier one.

That's exactly why I suggested to try '**Live CDs**' of newer versions. It'll instantly demonstrate whether they have better drivers included or not.

Additionally, if you can use USB flash drive (persistent install), you can also safely try how it may go with proprietary drivers (just make a persistent install, switch to proprietary drivers if needed and see the final performance!).

To see details of any driver/module (including version info) try this command:
```
modinfo <module name>
```
(for example, to check info of module 'agpgart' the command will be:- **modinfo agpgart**)

---

### Post by ultimate_aektzis on 2010-09-01
The only reason I dont try upgrade is that I am afraid of losing data.I dont know if its FUD, although

---

### Post by varunendra on 2010-09-01
While it is possible to, an upgrade is NEVER recommended in Ubuntu. Instead, a fresh installation is encouraged.

Anyway, trying a Live CD or a Live USB doesn't make ANY change to your hard disk (choose the default "Try..." option during boot-up) unless you **intentionally** delete / manipulate your data or partitions. You can't think of a safer way to try an OS! :)

If you liked the experience with the new version, we are always here to walk you with the safe methods to finally switch to it.

---

### Post by ultimate_aektzis on 2010-09-02
Thnaks for your tips.I will think about it during the weekend.):P

---

