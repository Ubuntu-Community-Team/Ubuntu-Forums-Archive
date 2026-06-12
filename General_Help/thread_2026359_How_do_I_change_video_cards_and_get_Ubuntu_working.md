---
title: "How do I change video cards and get Ubuntu working again."
date: 2012-07-15
forum: General Help
---

### Post by ubnewbie2 on 2012-07-15
I have a machine with a and old nvidia geforce 6150 in it, running the latest prop. drivers, and I can only seem to get Unity 2D running.  

I have a Gigabyte Geforce GTS 250 card spare.  I tried it in the machine, but Ubuntu booted to command line only, so I have removed it again temporarily, to seek advice.  

I have googled some info about recovery mode.  Does that use some default video driver that will get me going, and then can I install the correct driver somehow?  I haven't done this before, so what is the best procedure when changing video cards like this, to get the graphical desktop going again.

---

### Post by Pilot6 on 2012-07-15
The easiest way for a newbie is to remove proprietory drivers before you change a vidio card. Then boot with a new card and install them again.

The other way is to boot into console with the new card and remove prop. drivers 
```

sudo apt-get purge nvidia*

```
Then reboot. If xorg does not start install prop drivers
```

sudo apt-get install nvidia-current

```

---

### Post by ubnewbie2 on 2012-07-15
I will try removing the drivers first.  Thanks.

---

### Post by ubnewbie2 on 2012-07-15
I had some success!   With the new card in place, and no nvidia drivers, I have a Unity desktop (not 2d), which means better graphics (faster too).   However, if I install nvidia-current, it will not boot to graphical mode at all.

The system info detail reports driver "Gallium 0.4 on NV92" and experience as standard, still it's better than before.

Now to find out if there's an nvidia driver that will work.

---

### Post by Pilot6 on 2012-07-15
1. Try to purge nvidia as I mentioned before and then install again. Some settings from the old card ramain and cause problems.
2. You may try newer nvidia drivers from x-swat

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by ubnewbie2 on 2012-07-15
> **Pilot6 said:**
> 1. Try to purge nvidia as I mentioned before and then install again. Some settings from the old card ramain and cause problems.
2. You may try newer nvidia drivers from x-swat

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

```

I already purged nvidia when it failed to boot into graphical mode, and that got me back up as I am now.(edit:  I haven't tried reinstalling since - need to try that)

Yes, I need to try the latest drivers I guess.  Thanks again for the help.

---

### Post by ubnewbie2 on 2012-07-15
No luck.

After adding swat, purging, upgrading, Ubuntu offered my 2 choices of nvidia drivers (different names to before) one free, one proprietary.  Neither will work however.  The system just boots to the command line login.  Luckily, now you armed me with that purge command, I can do that, reboot, and be working again.

So looks like my card just won't work and better than with the builtin drivers :(  unless there are other drivers somewhere else I should try.

---

