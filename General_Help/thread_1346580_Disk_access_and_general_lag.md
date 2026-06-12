---
title: "Disk access and general lag"
date: 2009-12-05
forum: General Help
---

### Post by Zan0r on 2009-12-05
Hi,

I have a Q6600 based PC with 4gigs of RAM running Xubuntu Intrepid 64bits.
The hard drive in it is a WD 500gigs SATA in ext3.
Graphics is NVidia 9500GT.

Everything, as far as Intrepid is concerned is up to date.

Problem is, when I unrar a file, or move big files around the constant disk access creates such a lag that I cannot use firefox or anything for that matter and eventually my VPN connection drops too.

The CPU load is around 1-3% during that. (so "idle" really)

In gkrellm on the disk access graph I see around 4M/s.

Unpacking RARs or moving ISO files takes ages; sometimes up to 30minutes for 9gig ISO

Any ideas?

---

### Post by audiomick on 2009-12-05
What is your RAM doing in that time?
A busy disc shouldn't interfere with Firefox, I should think, but if your RAM is all used up, it could. Is your Swap big enough, and is it being accessed properly?

Your other specs look alright, although I actually have no idea if the quoted disc speed is good or not. I had a look at mine with gkrellm (had to install it first...), and only got up to a couple of hundred K whilst accessing folders of photos.

---

### Post by Zan0r on 2009-12-05
The 4M I am talking about on the HD is while transfering big files and when the lagging occurs.

The RAM is usually around 3Gig free...

```

MemTotal:      4055152 kB
MemFree:       1461708 kB
Buffers:         63216 kB
Cached:        1844044 kB
SwapCached:          0 kB
Active:         781268 kB
Inactive:      1602136 kB
SwapTotal:    11871992 kB
SwapFree:     11871992 kB
Dirty:            2824 kB
Writeback:           0 kB
AnonPages:      476196 kB
Mapped:         138420 kB
Slab:           116220 kB
SReclaimable:    71340 kB
SUnreclaim:      44880 kB
PageTables:      21924 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:  13899568 kB
Committed_AS:  1110216 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    318704 kB
VmallocChunk: 34359418875 kB

```

---

### Post by ibuclaw on 2009-12-05
You could try [renicing]("http://manpages.ubuntu.com/manpages/karmic/en/man1/renice.1.html") the priority of the unpack process.

It will mean that it takes longer to unpack, but should be less disruptive on the I/O scheduler.

By default, user processes have a Nice value of 0.
Setting it to about 10 should do, but you can play about with the "Change Priority" feature in the System Monitor to get it right.

Regards
Iain

---

### Post by Zan0r on 2009-12-05
Yes renicing is an option but really i'd rather not have to do such a thing every time...

---

### Post by ibuclaw on 2009-12-05
Try another scheduler then?

```
cat /sys/block/sda/queue/scheduler
```
The default is CFQ.

To set to Deadline
```
sudo bash -c 'echo deadline > /sys/block/sda/queue/scheduler'
```
Or Anticipatory
```
sudo bash -c 'echo anticipatory > /sys/block/sda/queue/scheduler'
```

Some people report better success with them due to their unique setups/computing style.


To make it semi-permanent, edit /etc/default/grub and set
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **elevator=IOSCHED**"
```
where IOSCHED is your io scheduler of choice.

Then:
```
sudo update-grub
```
to commit that change.

Regards
Iain

---

### Post by Zan0r on 2009-12-05
Ill give it a go, thanks.

---

### Post by Zan0r on 2009-12-05
After reading this [http://www.linuxjournal.com/article/6931](http://www.linuxjournal.com/article/6931) I decided to give anticipatory a go.

Seems alot better, at least doesn't cause severe lag, I don't lose my VPN anymore and firefox is useable.

I'll run more tests.

---

### Post by Zan0r on 2009-12-05
The part to make it semi-permanent doesn't work.

There was no /etc/default/grub so I created it, but didn't work.

---

### Post by ibuclaw on 2009-12-05
> **Zan0r said:**
> The part to make it semi-permanent doesn't work.

There was no /etc/default/grub so I created it, but didn't work.

What type of bootloader do you use?
The instructions I gave are for Grub2 only.

---

### Post by Zan0r on 2009-12-05
I use the default grub of intrepid

---

### Post by ibuclaw on 2009-12-05
> **Zan0r said:**
> I use the default grub of intrepid

Then you edit:
```
/boot/grub/menu.lst
```

I think the option you should be looking out for is "**DEFOPT**"

Add it to that line and again - run 'sudo update-grub' and it should update.

Regards
Iain

---

### Post by Cheesemill on 2009-12-05
What model number is your hard drive?
 
According to this thread there have been people suffering with very low write speed on a recent bad batch of Western Digital drives.
 
[http://ubuntuforums.org/showthread.php?t=1297342](http://ubuntuforums.org/showthread.php?t=1297342)

---

### Post by bamdad.khan on 2010-02-01
hi everybody,

i'm having a problem very similar to this one. i'm not using a western digital drive. i've tried ionice, but it's only good for a certain process, and since every process lags the system, i have a feeling i'm better off without it.

i'm on a thinkpad t42 running 9.10. i didn't have this problem under opensuse 11.2, debian 5 (lenny), or even windows xp. i have only 512 megs of ram (planning to get an additional 1gb stick), but when i borrowed an additional gig from a friend, nothing changed.

any kind of disk operation (be it on the local hard drive or a usb drive) lags the system while the processor is almost idle.

i've installed iotop to pinpoint a supposed runaway process, but alas, there isn't one. sometimes the weird disk activity doesn't stop after the operation has completed (like updating, apt-getting, dd'ing etc.), occasionally resulting in the same crazy disk i/o even after half an hour, and i can't even move the pointer.

i'm on ext3, since firstly i thought it's somehow connected with ext4.

can anybody help me? this is the only thing keeping me away from a perfect install after numerous xorg.conf and other edits.

thanks,
bamdad

---

### Post by bamdad.khan on 2010-02-01
okay, now i'm really stumped. i've been periodically checking ionice in tilda while doing stuff, and there are one to three processes with **no name** popping up out of nowhere, with only a PID, eating my resources.

any ideas..? please..?

---

