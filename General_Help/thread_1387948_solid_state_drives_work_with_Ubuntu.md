---
title: "solid state drives work with Ubuntu?"
date: 2010-01-22
forum: General Help
---

### Post by ticket on 2010-01-22
I'm thinking of getting a solid state drive to install Ubuntu on.
Has anyone tried this?

Will Ubuntu treat it as a normal disc drive with regard to formatting and partitioning?

Can I use dd to clone the solid state drive to a standard mech. drive (copying the boot sectors, partition table, etc)?

30Gb SSDs are available for around £100.
They apparently make a system extremely responsive. But I read somewhere that you should not format them - so installing an ext3 file system might be a problem.

---

### Post by ibuclaw on 2010-01-22
Yes.

I recommend Intel SSDs.

> **ticket said:**
> .
But I read somewhere that you should not format them - so installing an ext3 file system might be a problem.

Installing any filesystem on them that has a journal might be a problem for **older generation** SSDs. But that myth is no longer: (see [http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/]("http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/")).

If anything, I recommend ext4 with **relatime** mount option.

Regards
Iain

---

### Post by PhoHammer on 2010-01-24
I'm also looking into getting a SSD. The price has gone down to my range (40 GB ~ $130).

Has anyone else gotten one lately? What's your experience with it?

---

### Post by nubbe on 2010-01-25
SSDs behave like hdds, u can partition, format and whatever.
Supposedly, the best (easiest) way is to use the win7 installer to partition an unused ssd to get it alligned.

I jumped the gun and installed ubuntu in the middle, then I removed the partition and tried to partition the whole ssd with win7. That didn't really work like I wanted, win7 saw that I had a used portion in the middle and didn't touch that. It still partitioned the part in the beginning that I allocated for it tho.

Then I moved on and repartitioned the rest with gparted and installed ubuntu with dual-boot.
no problems and real fast, probably not alligned tho.
I'll probably wipe it in the future when better tools come out or I can feel a slowdown...

I got an Intel X-25M g2 80GB

---

### Post by ticket on 2010-02-06
Thanks guys, good feedback!

---

### Post by dcstar on 2010-02-07
> **ibuclaw said:**
> Yes.

I recommend Intel SSDs.

Installing any filesystem on them that has a journal might be a problem for **older generation** SSDs. But that myth is no longer: (see [http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/]("http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/")).


"Myth"?!?, reading all of the posts on that blog - not just the initial article - clearly shows that only certain SSDs have reduced the various problems.

Unless people are **certain** that they are getting a SSD device that has solved these problems, then they could be in for some major disappointment.

---

### Post by Herman on 2010-02-07
Here's the full version of that link, [URL="http://thunk.org/tytso/blog/category/computers/ssd/"]http://thunk.org/tytso/blog/category/computers/ssd/

[/URL]Here's another link:  The SSD Anthology: [Understanding SSDs and New Drives from OCZ]("http://www.anandtech.com/storage/showdoc.aspx?i=3531&p=2") - AnandTech.

Don't forget though, these links are about a year old now and flash technology will have advanced a lot in a whole year.

File systems have advanced a lot in a year too, we're using ext4 now.

I have an 64 MB OCZ Vertex and I think it's great! Vertex is the model OCZ made in reply to that link I posted, in which solved they solved the stuttering issue. My OCZ Vertex SSD is quick and there's none of the stalling that is discussed in that link, which is about an earlier model. I have Lucid Lynx booting in it in around ten seconds in mine, and it's smooth.

OCZ have a their own user forum and they have a lot of Ubuntu users there too. Some of their mods use Ubuntu, and that's another reason why I like OCZ products. I''ll buy another OCZ SSD sometime soon, a larger one if I can afford it. :)

---

### Post by BOFH+ on 2010-02-08
Anyway, decent support for the discard infrastructure in libata is available in kernel _[[COLOR="Red"]2.6.33[/COLOR]]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=18f0f97850059303ed73b1f02084f55ca330a80c")_. SSDs need it for the internal garbage collector (increases lifespan and performance).

Unfortunately, according to [https://wiki.ubuntu.com/specs/KernelLucidKernelDecision](https://wiki.ubuntu.com/specs/KernelLucidKernelDecision) Ubuntu 10 will be using 2.6.32, so get your compiler ready ;-)

---

