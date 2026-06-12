---
title: "Ext4 discard option (AKA TRIM) not working"
date: 2011-11-02
forum: General Help
---

### Post by Lem98 on 2011-11-02
OS: Ubuntu Oneiric 64bit, fresh install, kernel 3.0.0.12.

SSD: Crucial M4 64GB

AHCI enabled in BIOS

/dev/sda2 (my / ) is an ext4 filesystem created without journal, mounted with noatime,discard options. /proc/mounts confirms:
```
/dev/sda2 / ext4 rw,noatime,errors=remount-ro,user_xattr,acl,barrier=1,stripe=128,discard 0 0
```

ioscheduler is noop:
```
lem@biggy:~$ cat /sys/block/sda/queue/scheduler
[noop] deadline cfq 
```

BTW: in order to change it, You can run:
```
echo [ioscheduler] | sudo tee /sys/block/sd?/queue/scheduler
```

replacing ? with the appropriate letter.


So: "discard TRIMMING" is **not** working - double checked this way: [COLOR="Red"]_[http://andyduffell.com/techblog/?p=852]("http://andyduffell.com/techblog/?p=852")_[/COLOR]

However if I manually run:

```
$ sudo fstrim -v /
```

(remember: /dev/sda2 is mounted on / )

in a few seconds I get my device trimmed, and then I can see my zeroes on it.

And You? Are You sure Your ext4 is actually being trimmed?

Could You please check it? Please report Your results in this thread also specifying:

1) Your SSD model;
2) whether Your ext4 is journaled or not;
3) Your mount options.

Thanks a lot.

Bye, Lem

---

### Post by Lem98 on 2011-11-05
OK, I've got some feedback elsewhere, and I made myself some tests.

"Discard" mount option does NOT work with an ext4 filesystem, if it doesn't have a journal. It works with a journal, instead.

However, "fstrim" command works even without a journal.

What is really bad, IMHO, is that, when they work, every byte which is trimmed (AKA discarded) is immediately reset (AKA deleted) by my Crucial M4 firmware (ver. 02) even if it wouldn't be necessary (almost empty page in an almost empty block in an almost empty disk): which means a lot of unnecessary resets (every reset means that a whole block of 512kB loses one of its lives).

I don't know if this happens because of the discard/trim implementation in ext4, or because the firmware of my Crucial M4 (ver. 02) is *stupid*.

Bye, Lem.

---

### Post by dcstar on 2011-11-05
You do not seem to understand what "TRIM" does. All that happens is that the SDD is notified of blocks that the OS is no longer using, what the SSD does with that information is totally up to the SSD.

The reason it is better for the SSD to be notified of these no longer used data blocks is so the SSD can wipe them in background and make them available when a write command is sent to it because it is **faster** to write to an empty SSD block than to rewrite a used SSD block (basically read entire block, wipe entire block, write entire block with new info versus just writing the entire block on an already empty block).

If a block is already "wiped" by the SSD then I seriously doubt that the SSD will waste resources wiping blocks it already knows are done.

"TRIM" only comes into play when all of the empty blocks on an SSD device are used up, then the device will lose performance but still function because it will be forced to use the 3 step writing process instead of the single step write process **and** you be writing to the same physical blocks instead of spreading the writes across all unused blocks.

---

### Post by Lem98 on 2011-11-06
> **dcstar said:**
> You do not seem to understand what "TRIM" does. All that happens is that the SDD is notified of blocks that the OS is no longer using, what the SSD does with that information is totally up to the SSD.

I understand, please believe me.
TRIM is just informative. 

But discard and fstrim seem to work differently from how they should, at least with my Crucial M4. They seem to work more like a (partial) SSD wiper tool.

Try yourself.
Take an almost *empty* SSD. Then:

echo quack > quack

Now you have a very tiny file: just a few bytes in a 4kB empty page in a 512kB empty block.

Now delete the file.

With discard working (or by running fstrim), those few bytes will be **immediately** wiped. Which means of course that the whole 512kB block will be wiped, and its life shortened. This is stupid, in an almost empty disk.

On the contrary, if all or most of the pages of a block are discarded, it surely makes sense for the firmware to wipe the block **immediately** after the trim is issued: this is why, to verify whether trim is working, you should create and then delete a fairly **large** file (at least three SSD blocks large): otherwise you can get a false negative.

So my question was: my SSD firmware is stupid, or discard and fstrim are NOT only just mere TRIM?

> 
If a block is already "wiped" by the SSD then I seriously doubt that the SSD will waste resources wiping blocks it already knows are done.


I've never written anything like that. I've written that is stupid to wipe an *almost* empty block (127 free pages, 1  discarded) in an almost empty disk. You shorten the life of 128 times the space discarded, for whatever reason? You already have plenty of free space!

Of course empty blocks are not wiped. That would be insane.

Bye, Lem.

---

### Post by Lem98 on 2011-11-06
> **Lem98 said:**
> I understand, please believe me.
TRIM is just informative. 

But discard and fstrim seem to work differently from how they should, at least with my Crucial M4. They seem to work more like a (partial) SSD wiper tool.

Try yourself.
Take an almost *empty* SSD. Then:

echo quack > quack

Now you have a very tiny file: just a few bytes in a 4kB empty page in a 512kB empty block.

Now delete the file.

With discard working (or by running fstrim), those few bytes will be **immediately** wiped.

Perhaps I'm wrong thinking they are immediately wiped just for those zeroes. I immediately read zeroes, but maybe it's because of the SSD firmware **faking** those zeroes.

So it should be like that:

- don't see zeroes -> trim/discard not working;
- see zeroes -> trim/discard working.

When trim/discard is working, there's no way to know for sure whether the block has been actually wiped, or the firmware is faking the block content, showing zeroes even if the block hasn't been wiped yet.

I didn't think firmwares were so bad guys. ;)

Bye, Lem.

---

