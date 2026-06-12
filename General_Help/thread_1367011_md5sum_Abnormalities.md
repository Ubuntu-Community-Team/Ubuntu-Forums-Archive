---
title: "md5sum Abnormalities"
date: 2009-12-29
forum: General Help
---

### Post by crazyness003 on 2009-12-29
**[COLOR=Red]RESULT EDIT:[/COLOR]** It would appear that md5sum hashes are calculated in the CPU (obviously). But curroption in the CPU, or any other hardware that feeds the CPU (ex: RAM, or MoBo) can yield sporadic hashes. Basically, if someone else is experiencing this problem, you more than likely need new hardware.


Hi All.

I recently tried testing an iso for integrity and was using a nautilus script that came with Ubuntu Tweak to check the md5sum. Of course it failed and I thought "meh, another bad download". So, just for fun, I decided to use the terminal to check it as well. When I ran that, it gave me a completely different reading fro mthe first (still wrong though). SO this got me to wondering: Is my md5sum hasher broken?

I check a bunch of other .ISOs repeatedly, and after every hash ceck I get different results (for the same FILE)

Here's an example of an old Jaunty .ISO I used.
```
$ md5sum ubuntu-9.04-desktop-amd64.iso
**e2c3eaa53dc054f7c4dc5fa5d5f54904**  ubuntu-9.04-desktop-amd64.iso
$ md5sum ubuntu-9.04-desktop-amd64.iso
**5884dc5bd9facfb70b59da5133d4eb0d**  ubuntu-9.04-desktop-amd64.iso
$ md5sum ubuntu-9.04-desktop-amd64.iso
**92e4257032b2898b420a821011f3dd36**  ubuntu-9.04-desktop-amd64.iso
$ md5sum ubuntu-9.04-desktop-amd64.iso
**a740cb1888a7a70d298a9efc5f1e6bbd**  ubuntu-9.04-desktop-amd64.iso

```These were all run on the same file, a couple of seconds apart.

Now either I'm doing something wrong, the ISO is mutating or I'm expecting the wrong result (which I thought to believe was: it should yield the same hash repeatedly, regardless how many times it is run). The same thing happens with SHA1SUMs.

I read in another thread [[here]("http://ubuntuforums.org/showthread.php?t=1049785&highlight=md5sum+broken")] that hardware issues may affect hash calculations. Could that be the problem?
Can someone shed some light on this for me? 

Thanks

EDIT: Tested with sha256sum and sha512sum as well. Same abnormalities
```
$ sha256sum ubuntu-9.04-desktop-amd64.iso
**f6bc12c506fec6c8df24794034b4533387ae4ff40a932c327ce316b2877b02d9**  ubuntu-9.04-desktop-amd64.iso
$ sha256sum ubuntu-9.04-desktop-amd64.iso
**8e1b11aca0a5c0efcef655a20945dbd16e3fab81e0248b376be65850f370aa59**  ubuntu-9.04-desktop-amd64.iso
$ sha256sum ubuntu-9.04-desktop-amd64.iso
**599e859b7d43b3ab552b98a013aff73c7efb2a29883f389a2dfe3cf6ec556d6d**  ubuntu-9.04-desktop-amd64.iso

```

---

### Post by crazyness003 on 2009-12-29
bump

---

### Post by Vaphell on 2009-12-29
ext4 partition by any chance? i've seen some time ago a thread where one guy complaining about inconsistent md5 checksums on ext4 while it didn't happen on ext3

---

### Post by crazyness003 on 2009-12-29
no, actually the .ISOs sit on an ntfs partition. my root is ext3. I was skeptical of using ext4 (too new for my taste). 

The reason why my data drives are ntfs is because they used to belong to a windows machine, and I just yanked them and put them in here. I didn't wanna risk losing any data, so I just left them. ntfs-3g is doind a pretty good job maintaining them.

At any rate, you think the file system has something to do with it?
I'll copy them onto an ext3 partition and run md5sums again. Lemme see what happens.

---

### Post by falconindy on 2009-12-29
Definitely hardware related. You're not overclocking anything, are you? Modified kernel in any way?

---

### Post by crazyness003 on 2009-12-30
> **crazyness003 said:**
> ...I'll copy them onto an ext3 partition and run md5sums again. Lemme see what happens.
Same thing. Inconsistent readings on the same iso. Regardless which file system the file resides.

> **falconindy said:**
> Definitely hardware related. You're not overclocking anything, are you? Modified kernel in any way?
Nope. No overclocking or kernel modding
```
$ lscpu
Architecture:          x86_64
CPU(s):                1
Thread(s) per core:    1
Core(s) per socket:    1
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            15
Model:                 7
Stepping:              10
**CPU MHz:               1200.000**    #its capable of 2600MHz
L1d cache:             64K
L1i cache:             64K
L2 cache:              1024K

```
```
**2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009** x86_64 GNU/Linux
```

Which piece of hardware (or combination thereof) might cause this behavior?

And just to clarify, the SAME hash should be calculated, regardless of it being incorrect from the published one. Right?
I just wanna know if i'm expecting the right result from running that command.

Thanks

---

### Post by falconindy on 2009-12-30
Right, hashes are values that are calculated according to a specific algorithm (see RFC 1321 for md5) based on the contents of a file. Therefore, the same file should give the same resultant hash every time on every computer. 

It's entirely CPU based. That doesn't, however, rule out the idea of something else in your system feeding the CPU bad data, or corrupting it along the way.

---

### Post by Hallvor on 2009-12-30
It *could* be faulty memory.

---

### Post by crazyness003 on 2009-12-30
Alright. I don't know of anyway to perform tests for CPU 'sanity', but I surely know about memtest+ for RAM.

This kinda sucks. I like my current setup, even though it's a bit outdated. 

I think its time to upgrade.

Thanks guys. I guess I'll mark this a [SOLVED], since now I know it could be faulty hardware.

---

