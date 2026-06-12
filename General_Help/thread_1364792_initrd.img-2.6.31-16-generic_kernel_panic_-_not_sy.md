---
title: "initrd.img-2.6.31-16-generic kernel panic - not syncing: OOM and no killable processe"
date: 2009-12-26
forum: General Help
---

### Post by adante on 2009-12-26
Hi guys,

I upgraded to 9.10 the other day and when I tried to reboot I got this (it's very early in the boot process):
[[IMG]http://img689.imageshack.us/img689/6903/distupgrade.th.jpg[/IMG]](http://img689.imageshack.us/i/distupgrade.jpg/)

The image is blurry so to transcribe:
```

[     3.660022] Kernel panic - not syncing: Out of memory and no killable processes...
[     3.660023]

```

I am still able to boot into 2.6.28-17-generic, although unfortunately my audio no longer works (it was working fine in 9.04) but that is a seperate issue.

Anyway a friend was encouraging me to file a bug about this. Of course I can't find a place to do this on the web and have been told that it is disabled. Ok.

When I try to run 'ubuntu-bug linux' it wants to submit a 345.8 MiB bug report. Unfortunately my upload speed is not fast enough to do this without inconvenience (plus I'm not sure how welcome it would be).

My friend is still encouraging me to report this somewhere anyway so, here it is.

Things I tried without any luck:
[LIST]
[*] Tried to cleanly reinstall the kernel
[*] Rebuild the initrd.
[/LIST]

In short the system is an e8400 on EG45-DS2H motherboard.

From 
A copy of dmesg is [here](http://pastebin.com/m7bcd7ba8)
Full lspci -v is [here](http://pastebin.com/m29fb5635)

---

### Post by AsianSpanker on 2009-12-26
Last night I downloaded the upgrades without looking at them. Trusting soul!
This morning I get black screen with this message:
[ 199362 kernel panic - not syncing - VFS: Unable to mount root fs om unknown block(op)..

What the heck? I have no idea what to try to fix this! What is this! any help out there???

---

