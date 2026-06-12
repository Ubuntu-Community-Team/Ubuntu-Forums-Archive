---
title: "fsck on boot"
date: 2006-02-20
forum: General Help
---

### Post by monkblah on 2006-02-20
Hello, this is a question about fsck I have wondered about for some time.

When I boot my computer (ubuntu 5.10), there are a bunch of disk partitions  (ext2/ext3) that are mounted.  These are set to be checked with e2fsck every so often (mayber every 30 boots or so). According to the tune2fs man page, this is highly recomended to prevent disk corruption. But I have tow problems with this.

First, most of the partitions, when fsck is being run on them at boot, show a progress bar on the console, so I see how far the fsck has gone and how it is progressing (something like this):

```


|================65%  \            |

```

However, for some of the larger partitions, no progress bar, or any indication of progress or activity is displayed.  The system just sits there, for a long times, sometimes 15 minutes or more. It is frustrating not even knowing how long this will take or if any progress is even happening.

So my first question is, how can I get the progress bar / verbose display to happen for ALL of my partitions?

My second question is: if it is not convenient to wait 15 minutes or more for the fsck to complete, is it safe (or possible) to terminate it, by hitting Ctrl-C or something like this? 

Also, out of curiosity, why does Windows not do something like this?

---

### Post by dcstar on 2006-02-20
[QUOTE=monkblah]Hello, this is a question about fsck I have wondered about for some time.

When I boot my computer (ubuntu 5.10), there are a bunch of disk partitions  (ext2/ext3) that are mounted.  These are set to be checked with e2fsck every so often (maybe every 30 boots or so). According to the tune2fs man page, this is highly recommended to prevent disk corruption. But I have tow problems with this.

First, most of the partitions, when fsck is being run on them at boot, show a progress bar on the console, so I see how far the fsck has gone and how it is progressing (something like this):

```


|================65%  \            |

```

However, for some of the larger partitions, no progress bar, or any indication of progress or activity is displayed.  The system just sits there, for a long times, sometimes 15 minutes or more. It is frustrating not even knowing how long this will take or if any progress is even happening.

So my first question is, how can I get the progress bar / verbose display to happen for ALL of my partitions?

My second question is: if it is not convenient to wait 15 minutes or more for the fsck to complete, is it safe (or possible) to terminate it, by hitting Ctrl-C or something like this?

Also, out of curiosity, why does Windows not do something like this?[/QUOTE]
All fsck runs should show progress, if it doesn't then there is something wrong somewhere.

If you want to have any fsck errors automatically corrected, edit /etc/default/rcS to have:

FSCKFIX=yes

I would not interrupt a fsck - unless the HD activity light was off for a long time. If a large partition is having fsck run for the first time, it may be doing a thorough scan of the disk (not really sure about this, someone else may have more insight).

---

### Post by monkblah on 2006-02-21
Hi David, thanks again for replying!

> All fsck runs should show progress, if it doesn't then there is something wrong somewhere.

Well, as I said, I only see progress for some partitions and not others. Anyone have any idea on what I should do? 

> If you want to have any fsck errors automatically corrected, edit /etc/default/rcS to have:

FSCKFIX=yes

I don't know if I want this or not. Is there any reason why I wouldn't want this? Why is it not the default?


> I would not interrupt a fsck - unless the HD activity light was off for a long time. If a large partition is having fsck run for the first time, it may be doing a thorough scan of the disk (not really sure about this, someone else may have more insight).

Thanks for the info, I will not interrupt the fsck's then, since I don't want to harm my hard disks or their data.

My fsck's take a long time for the big partitions. They don't seem inordinately long, that is, they seem to go at about the same rate as the smaller partitions, but they are just bigger so it can take 15 minutes or more to check a 200GB+ partition.

Still, the point is, sometimes I boot my computer and I really need to use it, NOW, not in 15 minutes or more. So it seems there must be SOME way to prevent this delay. Does everyone usuing ubuntu have to sometimes just wait 15 minutes while their computer boots? Any suggestions or knowledge on this would be appreciated.

---

### Post by farfargoth on 2006-02-21
[QUOTE=monkblah]
Also, out of curiosity, why does Windows not do something like this?[/QUOTE]

I would suspect that there are a couple of reasons for this:
1) Microsoft has never been known for doing things the secure way
2) Linux is supposed to be used on servers (think zero-downtime) and so it can be assumed that the computer will not be restarted often and that any restart wuold have been the result of a power-failure or similar.
3) ext3 is based on ext2 (exactly the same, but with added journal) which was not very safe. Could be a leftover from those days.
4) To discover faulty hard-drives/controller cards before they result in major filesystem-corruption.

If you don't want this behaviour, consider switching to ReiserFS, another journaling filesystem. I think I've heard that it's not suppposed to force fsck's but relies on other methods to ensure data integrity.

---

### Post by dcstar on 2006-02-21
[QUOTE=monkblah]
.......
Still, the point is, sometimes I boot my computer and I really need to use it, NOW, not in 15 minutes or more. So it seems there must be SOME way to prevent this delay. Does everyone usuing ubuntu have to sometimes just wait 15 minutes while their computer boots? Any suggestions or knowledge on this would be appreciated.[/QUOTE]
Don't really know why you have this issue (I haven't seen any others with it), but you may want to make sure DMA is enabled for your disks - this can improve performance many fold (search the forums for the instructions on this).

Post the contents of your /etc/fstab file so we can see if it is set up ok.

As far as the FSCKFIX goes, I reckon it should be default and it may be in the next release of Ubuntu (hopefully.......).

Without it, you can spend a lot of time pressing "y" if a lot of errors are detected.

---

