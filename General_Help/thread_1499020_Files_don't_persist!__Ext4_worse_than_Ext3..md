---
title: "Files don't persist!  Ext4 worse than Ext3."
date: 2010-06-01
forum: General Help
---

### Post by BillRebey on 2010-06-01
I'm attempting to use Ubuntu in a high-reliability, industrial environment, and it's not doing well at all.  Specifically, I'm testing power failure and recovery:

If a file is created and written to, and the power is pulled shortly thereafter, the file will either not exist at all when the system reboots, or it will be 0 bytes long.   

Using Ext4 (Ubuntu 9.10 and 10.4), "shortly thereafter" may be a VERY long time - 10 seconds or more!  On Ext3, the files seem to get persisted much faster, but the problem still occurs.

This can be **very easily tested** as follows:

```
~> ls -l /etc > fooDir;cp fooDir fooCopy;ls -l foo*
<note that fooDir and fooCopy are non-zero in size, then pull  the plug and reboot the system>
```

When the system reboots, the files either won't exist at all, or will be zero bytes in length.

What can I do about this?  

[LIST]
[*]- Is there a cache setting of some sort that I can disable or otherwise configure?
[*]- Alternatively, is there a C library call that I can make, or even an external/shell command that I can run, that will force my file to be flushed/persisted  (I'd much rather use a C library call)?
[/LIST]

If I can't correct this problem, I can't use Ubuntu!  

Thanks for any help!

---

### Post by Jay Car on 2010-06-01
> **BillRebey said:**
> I'm attempting to use Ubuntu in a high-reliability, industrial environment, and it's not doing well at all.  Specifically, I'm testing power failure and recovery:

If a file is created and written to, and the power is pulled shortly thereafter, the file will either not exist at all when the system reboots, or it will be 0 bytes long.   

Using Ext4 (Ubuntu 9.10 and 10.4), "shortly thereafter" may be a VERY long time - 10 seconds or more!  On Ext3, the files seem to get persisted much faster, but the problem still occurs.

This can be **very easily tested** as follows:

```
~> ls -l /etc > fooDir;cp fooDir fooCopy;ls -l foo*
<note that fooDir and fooCopy are non-zero in size, then pull  the plug and reboot the system>
```

When the system reboots, the files either won't exist at all, or will be zero bytes in length.

What can I do about this?  

[LIST]
[*]- Is there a cache setting of some sort that I can disable or otherwise configure?
[*]- Alternatively, is there a C library call that I can make, or even an external/shell command that I can run, that will force my file to be flushed/persisted  (I'd much rather use a C library call)?
[/LIST]

If I can't correct this problem, I can't use Ubuntu!  

Thanks for any help!

If it is truly a high-reliability, industrial environment, maybe it would be best to address the power situation first. Even in my small business, I have battery backups for everything important. Power outages are common here.  Rather than expect my computers and software to survive an outage, I'd prefer to do everything I can to protect the hardware against such outages.  

But, perhaps I am misunderstanding your issue.

---

### Post by arsenic23 on 2010-06-01
Wouldn't it be easier just to use a different file system?

---

### Post by redmk2 on 2010-06-01
> **BillRebey said:**
> I'm attempting to use Ubuntu in a high-reliability, industrial environment, and it's not doing well at all.  Specifically, I'm testing power failure and recovery:

If a file is created and written to, and the power is pulled shortly thereafter, the file will either not exist at all when the system reboots, or it will be 0 bytes long.   

Using Ext4 (Ubuntu 9.10 and 10.4), "shortly thereafter" may be a VERY long time - 10 seconds or more!  On Ext3, the files seem to get persisted much faster, but the problem still occurs.

This can be **very easily tested** as follows:

```
~> ls -l /etc > fooDir;cp fooDir fooCopy;ls -l foo*
<note that fooDir and fooCopy are non-zero in size, then pull  the plug and reboot the system>
```

When the system reboots, the files either won't exist at all, or will be zero bytes in length.

What can I do about this?  

[LIST]
[*]- Is there a cache setting of some sort that I can disable or otherwise configure?
[*]- Alternatively, is there a C library call that I can make, or even an external/shell command that I can run, that will force my file to be flushed/persisted  (I'd much rather use a C library call)?
[/LIST]

If I can't correct this problem, I can't use Ubuntu!  

Thanks for any help!

The maintainer of ext4 is Ted Tso.  He addresses this problem in his blog [**_here_**]("http://thunk.org/tytso/blog/2009/03/12/delayed-allocation-and-the-zero-length-file-problem/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+ThoughtsByTed+(Thoughts+by+Ted)").

---

### Post by dtfinch on 2010-06-01
There is a mount option you could try, data=alloc-on-commit, which supposedly makes ext4 behave more like ext3, committing all data every 5 seconds. Or there's also a nodelalloc option which disabled delayed allocation altogether, with a greater performance impact. I haven't tried either.

Otherwise (unless your program calls fsync after writes) ext4 will hold onto data for a minute or so because the delayed allocation helps it reduce fragmentation. XFS does this too, which made it notorious for zeroing files upon crashing. Now everyone seems to want to emulate it, and they try to shift the blame to apps for not calling fsync after every write, ignoring that it tends to bring systems to their knees when they do.

---

### Post by prodigy_ on 2010-06-01
> **BillRebey said:**
> If I can't correct this problem, I can't use Ubuntu!

Buy a good UPS to correct this problem. Or, if you need complete power independence, implement your own off-grid power solution.

Please understand that neither filesystems nor HDDs are meant to survive power failures with 100% reliability. It's not about ext and it's not about Ubuntu. NTFS will sooner or later fail you too, and sooner is more likely.

Furthermore, you're complaining about one of the key features of ext4 (delayed allocation) which makes it performance-wise superior to ext3. So I'm sorry, but your post sounds a bit silly. And yes, you can disable delayed allocation simply by mounting an ext 4 partition with ```
-o nodelalloc
``` option, but please don't think this will give you any real protection against sudden power outages.

---

### Post by BillRebey on 2010-06-01
Jay:     sorry...in the interest of brevity, I left out the details.  I'm running Ubuntu on very small, battery-powered, headless PCs.  They are "black boxes" that collect data.  They are routinely allowed to run down their batteries by less-than-attentive users.  Permanent, reliable power is not an option.

redmk2 and dtfinch:   Thanks for the input!  Ted's blog is extremely useful, and the EXT4 configuration options you mention are nice to know, too.  Fortunately, it sounds like I can simply call fsync on the target file and the target directory and I'll be good to go!

Thanks, all!

---

### Post by dragos2 on 2010-06-01
1. Are you using RAID ?
2. Do you have an UPS ? If you have a UPS system then you don't have to worry about
power failures.

Also read some options for ext4 here
[http://www.kernel.org/doc/Documentation/filesystems/ext4.txt](http://www.kernel.org/doc/Documentation/filesystems/ext4.txt)

---

### Post by prodigy_ on 2010-06-01
> **BillRebey said:**
> I'm running Ubuntu on very small, battery-powered, headless PCs.  They are "black boxes" that collect data.  They are routinely allowed to run down their batteries by less-than-attentive users.  Permanent, reliable power is not an option.

Hmm. In this case your best bet is SSD hard drives and nodelalloc option to ext4. Still, if your box will power off during a disk write, some data loss is imminent.

Also it's technically possible to monitor battery charge level and shut down the system when it falls below a certain threshold. Laptops do that, for example. I'm not an expert in this area though, so I don't know the details.

---

### Post by BillRebey on 2010-06-02
As pointed  out by  redmk2, "The maintainer of ext4 is Ted Tso. He addresses this problem in his blog [[COLOR="Red"]_***here***_[/COLOR]]("http://thunk.org/tytso/blog/2009/03/12/delayed-allocation-and-the-zero-length-file-problem/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+ThoughtsByTed+(Thoughts+by+Ted)")."

He discusses the matter further [[COLOR="Red"]_***here***_[/COLOR]]("http://thunk.org/tytso/blog/2009/03/15/dont-fear-the-fsync/")

The correct solution to the problem is to use fsync at appropriate times on both the file in question and the directory that contains it.

---

### Post by StuartN on 2010-06-02
> **BillRebey said:**
> As pointed  out by  redmk2, "The maintainer of ext4 is Ted Tso. He addresses this problem in his blog

There is some terrible, defensive groupthink (digital Maoism, even) in the reaction to this perfectly sensible question - plus Ted Tso's little hissy fit.

Comparative benchmarks don't show any compelling reason to use EXT4 (especially if you have to cludge it anyway) over EXT3 - e.g. [http://www.phoronix.com/scan.php?page=article&item=ubuntu_netbook_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_netbook_fs&num=1) and previous reports.

---

### Post by wkulecz on 2010-06-02
> If you have a UPS system then you don't have to worry about

Not it the real world!  Actual batteries sometimes go dead in ways that they pass the UPS tests, but can't keep the system up for more than a few seconds once the power actually goes out.

I've seen it multiple times, multiple UPS brands.

I consider a UPS essential and its the first thing I suggest for a randomly crashing or locking up system, next would be new larger capacity power supply, but to assume you can't have power problems because you have a UPS is absurd.

You also have to shop carefully for your UPS if you expect proper shutdown monitoring for it.

---

### Post by BillRebey on 2010-06-09
dtfinch, 

Thanks for the pointers to the mount options - I'll read up, learn, and experiment!  Good to know!

---

