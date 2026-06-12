---
title: "Gparted crashed system during resize"
date: 2010-05-29
forum: General Help
---

### Post by Gene Lewis on 2010-05-29
I was trying to resize my main partition using gparted, and create a few new partitions, on the primary drive, in preparation for the upgrade to lucid. my /home folder resides on another drive, so there *should* be no major loss, but just a pain in the .

initially, karmic resided on the entire hard drive, sda1, with just the 1 partition, 500gb, the whole drive. After moving home to a second drive, I ran lucid from live cd, used gparted to shrink karmic's partition to about 64GB, and create a couple other 64GB partitions for other distros to live in, and an extended partition 150GB for backups and 5gb for swap, so as to have /home on one drive, and it's backup on another.

Anyhow, when I applied the changes, it got ~5minutes into the process, past the filesystem checks, and began the resize, and the comp. shut down! everything still works, but[COLOR=Red]now gparted believes the 500GB drive to have just the 1 partition, with 460GB used, when actually there's only about 8GB used.[/COLOR]

Is there anything I gan do to get gparted to recognize this drive/partition correctly, so I can continue with my move to Lucid? I don't want to overwrite the karmic install just yet, I'd rather dual boot until i'm sure lucid will work out.

I'll just overwrite the whole drive with Lucid if I have to, but I'd rather not take such a drastic step yet.

~/Gene

---

### Post by Stigmata13 on 2010-05-29
I believe that's part of the risk... it's always best to make sure you have everything backed up before doing resizing and such (but not everyone does.)
I'd recommend booting to another hard drive or a live cd and saving everything you want to keep, and just reformatting the whole drive. I don't think there is much you can do to fix it.

---

### Post by wilee-nilee on 2010-05-29
> **Stigmata13 said:**
> I believe that's part of the risk... it's always best to make sure you have everything backed up before doing resizing and such (but not everyone does.)
I'd recommend booting to another hard drive or a live cd and saving everything you want to keep, and just reformatting the whole drive. I don't think there is much you can do to fix it.

Do not give advice you know nothing about, when it comes to this sort of situation this person can probably recover the whole setup.

Thread starter check out this link for testdisk chances are your partitions can be found and repaired or at least some recovery can be done.

Also I hope you were trying to resize with a live cd, never do it on a running system your using. Do not boot the computer with anything but a live cd or testdisk or another recovery program.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by John Bean on 2010-05-29
> **wilee-nilee said:**
> Do not give advice you know nothing about, when it comes to this sort of situation this person can probably recover the whole setup.

Success with testdisk will not necessarily mean the data in the recovered partitions is intact, depending on how far into the process gparted got before it was interrupted. It's certainly worth a shot but I wouldn't go so far as to say it will *probably* recover "the whole setup" but it is certainly possible if a little unlikely in my experience.

> Also I hope you were trying to resize with a live cd, never do it on a running system your using. Do not boot the computer with anything but a live cd or testdisk or another recovery program.If you actually read the OP he said that he booted it from a CD.

---

### Post by wilee-nilee on 2010-05-29
> **John Bean said:**
> Success with testdisk will not necessarily mean the data in the recovered partitions is intact, depending on how far into the process gparted got before it was interrupted. It's certainly worth a shot but I wouldn't go so far as to say it will *probably* recover "the whole setup" but it is certainly possible if a little unlikely in my experience.

If you actually read the OP he said that he booted it from a CD.

You are partially correct but advice to trash the whole setup was not good so without quoting the original post I don't always remember everything. I think we are talking about technicalities here. If it hasn't worked for you that is fine but this is the best solution at this point. I also said that **chances are your partitions can be found and repaired or at least some recovery can be done.**

---

### Post by Gene Lewis on 2010-05-29
Yes indeed I was running from a live cd. the resize had just begun, after having run through the filesystem checks gparted does at the start of the process, when it crashed.

I have to believe that some or all is recoverable, because the system boots up fine (keep in mind the partition in question is the one the OS is installed on! so everything works fine, it's just that gparted reports the usage of the drive wrong.

If I use Baobab (disk usage analyzer) it shows the entire contents of the filesystem / to be 118.8Gb, but 114Gb of that is the home folder, which is on a different drive, and simply mounted under /.  So the total amount used on this disk is about 5GB.

However, when i start up gparted, It lists the drive as having the one, 500GB partition, which is around 8o% full. coincidentally or not, that is about the total of the sizes of the partitions I was creating at the size of the crash. I'm guessing the partition table got created, or at least partially, but the partitions themselves didn't???

I wonder if I tried a different partition manager if it might pick up on the problem?

~/Gene

---

### Post by John Bean on 2010-05-29
> **Gene Lewis said:**
> I have to believe that some or all is recoverable, because the system boots up fine (keep in mind the partition in question is the one the OS is installed on! so everything works fine, it's just that gparted reports the usage of the drive wrong.

I wish you'd mentioned that earlier ;-)

Forget testdisk, it's not the tool for the job. Have you tried a forced fsck? If fsck says it's ok then I'd guess that gparted has reserved a load of space somewhere in the filesystem. Shouldn't be too hard to find and clean up - I haven't looked but I'll bet you're not the first to have had the problem :-)

---

### Post by wilee-nilee on 2010-05-29
John Bean may know more about this, so carry on, my main concern here was not just throwing out the whole thing without some options. ;)

---

### Post by Gene Lewis on 2010-05-29
Yeah, Testdisk wasn't able to help. I was just about to do a fresh install of lucid anyway, I just didn't want to lose all the settings and programs installed, etc without a way to go back. I think what I'll do is copy the entire filesystem to somewhere safe, install karmic fresh, and then replace the whole filesystem with what I had copied before. if that doesn't work, Ill just dive into Lucid, Since /Home is on a separate drive, all I should lose is all my installed programs, which are all replaceable.

I figure since I have been running off the HD, I'm probably getting further and further from an easy rescue anyhow. I'll let you know how it works out.

Thank you for your help!

~/Gene

---

### Post by Gene Lewis on 2010-05-29
Fsck said all was fine. I searched quite a bit before posting, and didn't find much that was similar to what I had going on.

Oh well. The important stuff is all thoroughly backed up. not really as big a problem as it seems

Thanks

~/Gene

---

### Post by Gene Lewis on 2010-05-29
HAHAHA

booted the live cd and told gparted to resize the (messed up) partition, and create a new little one in the empty space, and guess what? It figured out whatever it had done wrong! i thought it might, but figured it was risky.

So, now I'm back to where I started. Yay!

Thanks again everyone for your help!

~/Gene

---

### Post by John Bean on 2010-05-29
Nice one. Whatever the reserved space was it's obviously used to recover from exactly this sort of thing. I'm not sure I'd have been brave enough to try it but now that you have - and with a successful outcome - I'll make a mental note in case I need to do the same thing some day :-)

I know that Linux disk tools are pretty robust and reliable but it's especially nice that they exceed expectations when you need them most - quite the opposite of a certain other well-known OS.

---

