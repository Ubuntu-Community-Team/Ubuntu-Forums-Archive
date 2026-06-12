---
title: "Hang after Activating Swapfile Swap [OK]"
date: 2009-08-10
forum: General Help
---

### Post by jtp755 on 2009-08-10
I am not 100% sure when this started happening but im 85% sure it was after i upgraded KDE to 4.3 and/or my kernel to 2.6.28-14-generic. I was running KDE 4.3 beta3 from a PPA and then when it went live i disabled that PPA, rebooted, and ran the update checker again. There were only a few packages that needed updating at that point.

I noticed this problem on Saturday when i shutdown my computer and then started it back up. Everything goes smoothly until it displays Activating Swapfile Swap   [OK] and then it just sits there with the HD light solid. I can do a hard power off and turn it back on and it comes up fully like nothing ever happened. i can replicate this EVERY time. It also does not seem to matter how long i wait after the failed attempt. As long as it failed and then i try again it always comes up the second time. Is there some type of "lock" file in play?

I started researching around the net and the forums and thought my swap partition was the problem. I have turned it off, ran mkswap, turned it back on, rebooted, tried my old kernel, check the UUID in /etc/fstab, checked the UUID using blkid, everything i have found thus far and the problem still exists.

Whats weird to me is that i can hibernate and resume all day long with out any problems. RESUME-UUID in initramfs/conf.d/resume is the same UUID that is in /etc/fstab.

It seems to me that my swap is working fine so what could be my problem? Ive watched it load when it works and right after it displaying Activating Swapfile swap  [OK] is starts AppArmor. I removed that from startup and the hang still exits so i added it back to startup.

Any ideas?

---

### Post by jtp755 on 2009-08-10
I have tried kernels back to .11 and none work..

---

### Post by antoniosanct on 2009-08-19
> **jtp755 said:**
> I am not 100% sure when this started happening but im 85% sure it was after i upgraded KDE to 4.3 and/or my kernel to 2.6.28-14-generic. I was running KDE 4.3 beta3 from a PPA and then when it went live i disabled that PPA, rebooted, and ran the update checker again. There were only a few packages that needed updating at that point.

I noticed this problem on Saturday when i shutdown my computer and then started it back up. Everything goes smoothly until it displays Activating Swapfile Swap   [OK] and then it just sits there with the HD light solid. I can do a hard power off and turn it back on and it comes up fully like nothing ever happened. i can replicate this EVERY time. It also does not seem to matter how long i wait after the failed attempt. As long as it failed and then i try again it always comes up the second time. Is there some type of "lock" file in play?

I started researching around the net and the forums and thought my swap partition was the problem. I have turned it off, ran mkswap, turned it back on, rebooted, tried my old kernel, check the UUID in /etc/fstab, checked the UUID using blkid, everything i have found thus far and the problem still exists.

Whats weird to me is that i can hibernate and resume all day long with out any problems. RESUME-UUID in initramfs/conf.d/resume is the same UUID that is in /etc/fstab.

It seems to me that my swap is working fine so what could be my problem? Ive watched it load when it works and right after it displaying Activating Swapfile swap  [OK] is starts AppArmor. I removed that from startup and the hang still exits so i added it back to startup.

Any ideas?

I have the same problem. I reply two posts about the same and i don't have answer. I suposed that my fragmented ntfs partitions didn't mount perfectly, but deactivating the swap partitions and ntfs partitions doens't fix the issue.

Install bootchart and attach your boot image. Maybe I can help you. Regards!

---

### Post by sola on 2009-08-22
I also have the same problem and it started recently like in your case. So it is quite likely that an update broke our systems.

I have also tried the steps with recreating the swap partition but no change.

In my case I found that compcache was active on my system for some reason (this shouldn't happen in any case apart from the Live-CD sessions). I uninstalled compcache but nothing has changed.

My system was installed with Unetbootin because my Toshiba m200 doesn't have a CD drive and doesn't boot from USB drives.

---

### Post by sola on 2009-08-22
Fragmented NTFS drives are likely NOT the problem because I have tried to start the system with my windows drive commented out from fstab.

My root filesystem is formatted to ext4. How about yours?

---

### Post by antoniosanct on 2009-08-22
> **sola said:**
> Fragmented NTFS drives are likely NOT the problem because I have tried to start the system with my windows drive commented out from fstab.

My root filesystem is formatted to ext4. How about yours?

Yes, all my filesystems are formatted to ext4. Months ago was an update that "broke" our systems, and nobody knows how to fix (or almost don't reply in this post or anothers).

However, there is a open issue in Launchpad [here]("https://bugs.launchpad.net/bugs/369291").

Regards!

---

### Post by gastly on 2009-08-22
Hi, can you try disabling apparmor and then see if it works?

```

sudo invoke-rc.d apparmor stop
sudo update-rc.d -f apparmor remove

```

---

### Post by antoniosanct on 2009-08-22
> **gastly said:**
> Hi, can you try disabling apparmor and then see if it works?

```

sudo invoke-rc.d apparmor stop
sudo update-rc.d -f apparmor remove

```

 Thanks for the tip, but disabling AppArmor doesn't fix the problem.  However, disabling cleaning process (S36mountall-bootclean & S46mountnfs-bootclean), moves hang process to mysql start service  :sad:. That's very strange!!

Any other ideas??

---

### Post by gastly on 2009-08-23
It seems something related to the kernel. Try this:
Disable the splash screen by adding **nosplash** as a kernel option in your menu.lst and then see what error it gives.

---

### Post by P4man on 2009-08-23
since you mention a kernel update, did you try booting with an older kernel from the grub menu ? Does the recovery mode work?

---

### Post by antoniosanct on 2009-08-24
> **P4man said:**
> since you mention a kernel update, did you try booting with an older kernel from the grub menu ? Does the recovery mode work?

I have only kernel 2.6.28 versions, and I couldn't try other versions. is it possible to force installing other kernel versions?

TIP : ext4 filesystem by default

Thanks by the answers! Regards!

---

### Post by sola on 2009-08-24
Recovery mode results the same on my system (~90 seconds of disk-grinding during startup)

---

### Post by sola on 2009-08-24
The Ubuntu Launchpad issue you mention is the same problem that we are discussing here. I am taking part in the launchpad discussion too.

---

### Post by P4man on 2009-08-24
> **antoniosanct said:**
> I have only kernel 2.6.28 versions, and I couldn't try other versions. is it possible to force installing other kernel versions?

```
sudo aptitude install linux-image-<kernel version>
```

Think that will add the grub entries as well, so you just have to pick a kernel from the grub menu. If not, we can add those manually.

---

### Post by antoniosanct on 2009-08-24
> **P4man said:**
> ```
sudo aptitude install linux-image-<kernel version>
```Think that will add the grub entries as well, so you just have to pick a kernel from the grub menu. If not, we can add those manually.

I've using dkms, and installing other kernel outside official repositories give me installation problems (nvidia, vboxdrv, etc)

Going back at initial problem, I don't understand anything, because if I deactive some boot process at rcS.d (S36mountall-bootclean and S46mountnfs-bootclean, by example), the hang scrolls forward, always 55 secs. It's very very strange! :(

---

### Post by P4man on 2009-08-24
> **antoniosanct said:**
> I've using dkms, and installing other kernel outside official repositories give me installation problems (nvidia, vboxdrv, etc)

I wasnt suggesting you use anything outside the canonical repo's.. but I guess Im clueless about dkms

> Going back at initial problem, I don't understand anything, because if I deactive some boot process at rcS.d (S36mountall-bootclean and S46mountnfs-bootclean, by example), the hang scrolls forward, always 55 secs. It's very very strange! :(


You mean it always locks up at 55s ?

This is a wild guess and could be pointless,  but hey, worth a try I suppose, if you boot can you try adding this kernel parameter:
clocksource=[hpet|pit|tsc|acpi_pm|cyclone|scx200_hrt] 

Select one. acpi_pm has the most chance of working, hpet would be best.

---

### Post by antoniosanct on 2009-08-24
> **P4man said:**
> I wasnt suggesting you use anything outside the canonical repo's.. but I guess Im clueless about dkms



You mean it always locks up at 55s ?

This is a wild guess and could be pointless,  but hey, worth a try I suppose, if you boot can you try adding this kernel parameter:
clocksource=[hpet|pit|tsc|acpi_pm|cyclone|scx200_hrt] 

Select one. acpi_pm has the most chance of working, hpet would be best.

Sorry, man, this tips don't have any differences about boot times.

My resume of all of my tests:

- not starting mountall-bootclean, the hangs starts about mountnfs-bootclean
- not starting mountnfs-bootclean, the hangs starts about mysql
- not starting mysql, my boot time is time I expected, but the hang starts after I login, with a black screen.

In both cases, I see a lot of HDD activity in the HDD light and at Bootchart, assuming disk-grinding of other people

I supose some kind of ext4 error, but I have no idea. Thanks for all your help!

---

### Post by P4man on 2009-08-24
> **antoniosanct said:**
> Sorry, man, this tips don't have any differences about boot times.


well, your system is not booting, if I understand you correctly, it seems to hang after a fixed period of time, not while loading anything in  particular. I doubt thats somehow related to the filesystem, a problem with the kernel timer seems at least remotely more likely.

---

### Post by antoniosanct on 2009-08-27
MY SOLUTION: Remove TOTALLY /tmp and create new one, because /tmp/. has a HUGE size

```

$ sudo rm -rf /tmp
$ sudo mkdir /tmp
$ sudo chmod 777 /tmp
$ sudo chmod +t /tmp
$ sudo reboot

```

This method fix the hang boot but I don't know the origin of the problem.

---

### Post by syswalla on 2009-09-01
I have a server running 8.04 with four RAID drives that was exhibiting the same symptoms, taking several minutes to boot while hitting the drive lights. The above removal and recreation of /tmp fixed it. Thanks anoniosanct!!

Also, don't forget to add the sticky bit when chmod'ing /tmp. 
```

chmod 1777 /tmp

```

---

### Post by antoniosanct on 2009-09-01
> **syswalla said:**
> I have a server running 8.04 with four RAID drives that was exhibiting the same symptoms, taking several minutes to boot while hitting the drive lights. The above removal and recreation of /tmp fixed it. Thanks anoniosanct!!

Also, don't forget to add the sticky bit when chmod'ing /tmp. 
```

chmod 1777 /tmp

```

I'm glad to help you.

chmod 777 /tmp && chmod +t /tmp is the same than chmod 1777 /tmp

Regards!

---

### Post by mahboop on 2009-11-20
I had the same problem and this solution fix it :D

> **antoniosanct said:**
> MY SOLUTION: Remove TOTALLY /tmp and create new one, because /tmp/. has a HUGE size

```

$ sudo rm -rf /tmp
$ sudo mkdir /tmp
$ sudo chmod 777 /tmp
$ sudo chmod +t /tmp
$ sudo reboot

```

This method fix the hang boot but I don't know the origin of the problem.

Thanks bro

---

### Post by sola on 2009-11-20
The total removal and recreation of /tmp has fixed my laptop. It now boots as fast as it did after the original install.

THANKS VERY MUCH.

---

