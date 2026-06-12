---
title: "Extreme slow down"
date: 2011-01-12
forum: General Help
---

### Post by kaspar_silas on 2011-01-12
Really not having a good ubuntu day! :( 

My desktop was down and after fixing it I finished work and discovered my sodding laptop is sick too. I even messed up submitting this post first time and had to report myself and start over again. 

Sincere apologies and thanks to whoever very promptly sorted out the original duplicates.  

Anyway this current laptop problem is a bit of a mystery. Basically suddenly everything is locking up or taking an incredibly long time (evolution took 5mins to load up, thread posting took a similar amount of time hence the balls up). This is really odd as it worked fine last night and nothing new was installed or updated.

If I watch "top" nothing is reported as using up memory or cpu when it locks. If I have another log in active at lock up this normally half works. Half in that it's runs fine provided the command input is very simple. For example:

$ Echo "blah blah" 

is okay, as is top but:

$ dmesg

will normally lock or again cause a 5 min delay.

If I look at dmesg however I get alarming stuff like this:
```

[  600.272096] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  600.272103] ubuntuone-syn D 00000000     0  1856      1 0x00000000
[  600.272113]  f132fcdc 00000086 f6e70000 00000000 f1196000 f132fcdc c08c4700 c08c4700
[  600.272129]  b4a7c9e2 0000006e c08c4700 c08c4700 00000000 0000006e f15efe00 c08c4700
[  600.272143]  c08c4700 f1728000 00000000 c23db684 f6172800 ef85e3c0 f132fd38 c02d2aa5
[  600.272157] Call Trace:
[  600.272175]  [<c02d2aa5>] do_get_write_access+0x215/0x3f0
[  600.272187]  [<c0165f10>] ? wake_bit_function+0x0/0x50
[  600.272195]  [<c02d2da8>] jbd2_journal_get_write_access+0x28/0x40
[  600.272205]  [<c02bc1ce>] __ext4_journal_get_write_access+0x2e/0x60
[  600.272216]  [<c029c87f>] ext4_reserve_inode_write+0x5f/0x80
[  600.272225]  [<c029c8d8>] ext4_mark_inode_dirty+0x38/0x1a0
[  600.272235]  [<c02afe80>] ? ext4_journal_start_sb+0xc0/0xf0
[  600.272244]  [<c029cb64>] ext4_dirty_inode+0x34/0x50
[  600.272253]  [<c0237441>] __mark_inode_dirty+0x31/0x190
[  600.272262]  [<c01d96e4>] ? file_remove_suid+0x24/0x80
[  600.272271]  [<c022cad5>] file_update_time+0xb5/0x130
[  600.272280]  [<c01dbb98>] __generic_file_aio_write+0x1b8/0x500
[  600.272290]  [<c02229ae>] ? path_to_nameidata+0x1e/0x50
[  600.272298]  [<c0224132>] ? link_path_walk+0x412/0x890
[  600.272308]  [<c0230bef>] ? mntput_no_expire+0x1f/0xd0
[  600.272316]  [<c01dbf37>] generic_file_aio_write+0x57/0xc0
[  600.272325]  [<c0296b81>] ext4_file_write+0x41/0xd0
[  600.272335]  [<c02188c4>] do_sync_write+0xa4/0xe0
[  600.272343]  [<c021c933>] ? cp_new_stat64+0xe3/0x100
[  600.272354]  [<c032ec46>] ? apparmor_file_permission+0x16/0x20
[  600.272365]  [<c03030b4>] ? security_file_permission+0x14/0x20
[  600.272373]  [<c0218a42>] ? rw_verify_area+0x62/0xd0
[  600.272382]  [<c0218b52>] vfs_write+0xa2/0x190
...
THE NEXT LINE REPEATS AFTER EVERY FREEZE EVENT
[ 2494.120050] usb 1-5: reset high speed USB device using ehci_hcd and address 2

```

All of which isn't exactly clear to me. The only thing I can thing of, solely as I see "ext4" in my computers stream of conscience, is that it is real disk errors. Both my home drive and /usr are SD drives mounted on boot up (I do this as my laptop is an ASUS and thus only has 4Gb ).

Still to say the least this is clutching at straws. Has anyone ever encountered anything similar or does anyone have any suggestions. Any help at all is appreciated, especially today.

---

### Post by Ranko Kohime on 2011-01-12
> **kaspar_silas said:**
> All of which isn't exactly clear to me. The only thing I can thing of, solely as I see "ext4" in my computers stream of conscience, is that it is real disk errors. Both my home drive and /usr are SD drives mounted on boot up (I do this as my laptop is an ASUS and thus only has 4Gb ).
Hmm...  I can't make out most of that dmesg vomit either, but can I safely assume that / is on an SSD?  (basing my assumption on the size).  If that is the case, it's entirely possible that the drive has reached it's write limit, and is getting ready to fail.

And just a word of advice, ext3/4 tend to chew on flash drives quite a bit more than ext2.  Especially if you don't have something intercepting /var/log and /tmp.  When I first got a computer with an SSD, I sat and watched the thing go blip, blip, blip about once a second with some write or another to /var/log.  Being the obsessive compulsive that I am, I promptly installed Ramlog, and set /tmp to a RAM drive.  I've also sworn off ext3/4 for SSD's.

---

### Post by kaspar_silas on 2011-01-17
Cheers for those fine points

> I safely assume that / is on an SSD? (basing my assumption on the size). If that is the case, it's entirely possible that the drive has reached it's write limit, and is getting ready to fail.


Actually I don't think it's the "/" SSD. I installed the netbook-ubuntu on "/" which booted up fine. However you did set me thinking that maybe the other 16Gb SSD which is partitioned as two and mounted at "/usr" and "/home" might be in trouble. Unfortunately this has happened before, three times (on two separate SSD). I solved it both times by backing up the SSD, reformatting/getting new SSD, then rewriting the data. ( Then normally spending about a whole day restoring all the permissions to get sudo back.)

> 
ext3/4 tend to chew on flash drives quite a bit more than ext2. Especially if you don't have something intercepting /var/log and /tmp. 

ah okay, damn, didn't know that. So I have just been lining up trouble.

So to be clear to avoid this I just install ramlog and switch the external SSD drive to ext2 (hopefully without bricking permissions)? 

Do you happen to know if it possible to change the main "/" drive format type without reinstalling?

EDIT: Did you do anything especially clever to install ramlog. I installed ramlog as the website advised but was only greeted with the boot up message:
ramlog pre-start process (255) failed with status (252)

---

### Post by kaspar_silas on 2011-01-18
It seems it was the external SSD drive. I reformatted it and all went swimmingly. Well for 5min then freezing reappeared and the cursed message: 

```

usb 1-5: reset high speed USB device using ehci_hcd and address 2
```

started repeating in dmesg. Given a reformat didn't solve this problem. I guess the only solution is to buy a new SSD. :frown:++

Incidentally when my big magnetic archive drive started to get sick I was warned by an elegant thou distressing pop up saying "Disk drive failure imminent". A similar thing for an SSD would be just lovely.

---

### Post by kaspar_silas on 2011-02-09
Incidentally just to conclude this event. It seems it is the SSD reader that has the problem. (The SSD reader appears as a USB connection).

I realized this after I bought a new SSD and the problem reappeared. Short of physically replacing the SSD reader this doesn't have a solution. I'll mark it solved as it seems it's hardware not software.

Sadness++;

---

