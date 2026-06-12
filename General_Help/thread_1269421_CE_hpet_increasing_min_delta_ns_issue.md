---
title: "CE: hpet increasing min_delta_ns issue"
date: 2009-09-18
forum: General Help
---

### Post by pveurshout on 2009-09-18
Ever since installing Jaunty (amd64, kernel 2.6.28-15) I've been having quite some trouble with it (yesterday I was forced to reboot after some really weird errors in dmesg and I was told I had to do a manual fsck check. While executing this test it kept telling me really crazy stuff about 'orphaned inodes', whatever that might be :confused: ). Anyway, I may have found a possible cause (I came to this conclusing after reading many bug reports about users having this issue and having this cause their Jaunty to freeze). In the logs I quite often notice the following lines:

```
[   80.000254] Clocksource tsc unstable (delta = -351296609 ns)
[ 6234.705363] CE: hpet increasing min_delta_ns to 15000 nsec
[ 6234.705604] CE: hpet increasing min_delta_ns to 22500 nsec
[ 6962.600397] CE: hpet increasing min_delta_ns to 33750 nsec
[ 7356.076838] CE: hpet increasing min_delta_ns to 50624 nsec
[ 7900.620236] CE: hpet increasing min_delta_ns to 75936 nsec
```

Actually this is the first time I notice it going as far as 75936, but I guess in the past it just crashed before I had the chance to see this happen ;)

Although a fix would be awesome, a workaround would be fine as well. After some Googleing I found out it should be possible to tell Ubuntu not to use the hpet timer, but I'm not sure how to disable it. Can I simply add a line in menu.lst so it says something like "(...) quiet splash hpet=disabled", or is there more to it? (and could this even be dangerous?) Or should I better do something completely different?

---

### Post by pveurshout on 2009-10-04
Just letting anyone who's reading this know that I disabled hpet the way as described above and it's been working perfectly ever since. No freezes at all, uptimes up to 13 hours.

---

### Post by pveurshout on 2009-10-26
Unfortunately I had to mark this thread as 'Unsolved' again. It just froze on me again..seems it was a kernel panic, as the caps lock light went on (also, when I physically disconnected my USB mouse and then reconnected it, the red light underneath wouldn't turn on). Alt+Fn+REISUB didn't work; it was completely stuck. Nothing in the logs because of that. I just completed downloading a torrent containing four 2.1GB files to an ext3 partition. A minute or so after completion I started FF, checked my e-mail, clicked one of my bookmarks, *freeze*.

Anyway, as I'm not the only one who has Jaunty freeze on them all the time (although the frequency did go down from twice a day to twice in two months after switching from NTFS to Ext3 for my downloads - can't be a coincidence) I'm just letting anyone who reads this know that it's proabably _not_ the hpet-thing described above. I'm back to where I started :( Hopefully Karmic will be better..

---

### Post by draziw on 2009-10-29
Maybe add yourself to
[https://bugs.launchpad.net/bugs/270798](https://bugs.launchpad.net/bugs/270798) where some other people are getting hit by this too. (though the kernel version listed in the description is older, and mentions 64-bit, I think it's across the board for some hardware combinations. (it hits me on a Dell D620 w/ core duo + nvidia)

---

### Post by pveurshout on 2009-12-27
Recently I moved on to Karmic, which uses grub2. Does someone know how I can disable hpet in the boot options? In Jaunty I could just add 'hpet=disable' to menu.lst, but [here]("http://ubuntuforums.org/showthread.php?t=1195275") I read that grub.cfg should not be manually edited anymore. Can I just add hpet=disable to the bottom of /etc/default/grub?

---

### Post by draziw on 2009-12-27
> **pveurshout said:**
> Recently I moved on to Karmic, which uses grub2. Does someone know how I can disable hpet in the boot options? In Jaunty I could just add 'hpet=disable' to menu.lst, but [here]("http://ubuntuforums.org/showthread.php?t=1195275") I read that grub.cfg should not be manually edited anymore. Can I just add hpet=disable to the bottom of /etc/default/grub?

In /etc/default/grub.conf:
include hpet=disable in a uncommented GRUB_CMDLINE_LINUX_DEFAULT line.
eg:
```
GRUB_CMDLINE_LINUX_DEFAULT="hpet=disable"
```
or if you also wanted quiet boot and a boot splash graphic:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=disable"
```

Cheers

---

### Post by pveurshout on 2009-12-28
Thanks, that worked! :)

---

### Post by matt06 on 2010-01-31
I am getting this error on a Biostar TA790GX XE board with a 3.1GHz Dual-core CPU running both Mythbuntu 9.04 and 9.10 with all current updates.  During heavy system load, such as recording 2 shows and commercial flagging both of them in real-time, the MythTV frontend (idle or not) would eventually segfault and the entire system would freeze.  If I closed the frontend the segfault didn't happen, but still a hard lockup eventually.  I tried hpet=disable in the proper locations and acpi=off as well, but was still getting lockups so I then transplanted everything to a different board and the problem no longer occurred.

The only thing that seems to have worked so far is disabling 'Cool n Quiet' and 'CPU Smart Fan' in the bios.  When I do that, the CPU fan stays on full blast and on bootup my CPUFreq Monitor panel plugin complains that CPUFreq support is not present, but the problem is 'fixed'.

Is there another way to disable hpet or can I resolve this some other way that I'm missing?? Please help!  Could it be a cpu/chipset heat problem or power supply issue causing this?

EDIT:  possible solution [here]("http://ubuntuforums.org/showthread.php?t=698211&page=2"), will post back when I can test again.

---

### Post by 9tails on 2010-02-19
Using Ubuntu 10.04 alpha2 here, and I get the same error as OP except for the "clocksource tsc unstable" line.

I agree, a fix would be awesome...

---

### Post by matt06 on 2010-02-20
I had to give up on this issue with my Biostar board.  I simply don't have time to troubleshoot it right now.

---

