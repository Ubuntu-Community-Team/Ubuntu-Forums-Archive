---
title: "Odd times, Desktop crashed when wake up from Hibernation"
date: 2011-02-06
forum: General Help
---

### Post by luajunyi on 2011-02-06
Hi,

I've a very annoying(and strange) problem with hibernation. I'm using Ubuntu 10.10. 

It's been a month and the hibernation works exactly in the following pattern:

success->fail->success->fail->......

By success, I mean the machine hibernates OK and wake up exactly as before hibernation.

By fail, I mean the machine go to sleep and when wake up, all applications are gone and the login screen is displayed. I think gnome desktop has crashed in such cases.

Can anyone help? Or what more information should I provide?

Thanks.

---

### Post by fabricator4 on 2011-02-06
Make sure that your swap partition is larger than your memory size.  Some say it should be twice the size of your RAM but I'm not sure what the justification is for that...  maybe if you've already got the swap heavily loaded and then try to use hibernation you need even more space.

Use Krellm or System Monitor to keep tabs on your memory usage, paricularly before you put the machine into hibernation.

Chris.

---

### Post by luajunyi on 2011-02-06
> **fabricator4 said:**
> Make sure that your swap partition is larger than your memory size.  Some say it should be twice the size of your RAM but I'm not sure what the justification is for that...  maybe if you've already got the swap heavily loaded and then try to use hibernation you need even more space.

Use Krellm or System Monitor to keep tabs on your memory usage, paricularly before you put the machine into hibernation.

Chris.

Twice the RAM? I have 4G RAM on a 32-bit system, so do I need 8G for swap? Currently the swap size is slightly bigger than 4G. Is that enough?

---

### Post by luajunyi on 2011-02-07
Can anyone help? I'm losing sleep because of this.

I've verified.

1. X did crashed upon waking up from hibernation.
2. It will only crashed if the previous waking up was success. It's very weird.

The last lines in /var/log/Xorg.0.log.old was as below. 

[ 40922.787] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
[ 43222.641] (II) Open ACPI successful (/var/run/acpid.socket)
[ 43222.704] (II) NVIDIA(0): Setting mode
[ 43222.704] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:nvidia-auto-select+0+1200"
[ 43223.157] (II) Power Button: Device reopened after 1 attempts.
[ 43223.177] (II) Power Button: Device reopened after 1 attempts.
[ 43223.193] (II) HID 05f3:0007: Device reopened after 1 attempts.
[ 43223.205] (II) HID 05f3:0007: Device reopened after 1 attempts.
[ 43223.217] (II) Kingsis Peripherals  Evoluent VerticalMouse 3 : Device reopened after 1 attempts.
[ 43269.822] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
[ 53677.778] (II) Open ACPI successful (/var/run/acpid.socket)
[ 53677.856] (II) NVIDIA(0): Setting mode
[ 53677.856] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:nvidia-auto-select+0+1200"
[ 53678.189] 
Backtrace:
[ 53678.189] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80a955b]
[ 53678.189] 1: /usr/bin/X (0x8048000+0x6148d) [0x80a948d]
[ 53678.189] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb76f640c]
[ 53678.189] Segmentation fault at address 0x1d
[ 53678.189] 
Caught signal 11 (Segmentation fault). Server aborting
[ 53678.189] 
Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[ 53678.190] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 53678.190] 
[ 53678.190] (II) Power Button: Close
[ 53678.190] (II) UnloadModule: "evdev"
[ 53678.190] (II) Power Button: Close
[ 53678.190] (II) UnloadModule: "evdev"
[ 53678.190] (II) HID 05f3:0007: Close
[ 53678.191] (II) UnloadModule: "evdev"
[ 53678.191] (II) HID 05f3:0007: Close
[ 53678.191] (II) UnloadModule: "evdev"
[ 53678.191] (II) Kingsis Peripherals  Evoluent VerticalMouse 3 : Close
[ 53678.191] (II) UnloadModule: "evdev"
[ 53678.485]  ddxSigGiveUp: Closing log

---

### Post by fabricator4 on 2011-02-07
I thought I'd replied to your last.  Must have fallen asleep at the keyboard.:oops:

At this point I think I'd test the part of the drive that the swap partition is on.  On reaching this conclusion I realised that that a pending bad sector I've been chasing on my boot drive might actually be on the swap partition.  I've been chasing it on sda1 and have been unable to find it. (It's at this point my train of thought must have got derailed) 

In your log file the key part is obviously:
```
[ 53678.189] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80a955b]
[ 53678.189] 1: /usr/bin/X (0x8048000+0x6148d) [0x80a948d]
[ 53678.189] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb76f640c]
[ 53678.189] Segmentation fault at address 0x1d
[ 53678.189]
Caught signal 11 (Segmentation fault). Server aborting
[ 53678.189] 
```

There's obviously an addressing problem or a paging problem as the memory is being read back out of swap.  Since the (memory) problem was not there before you went into hibernation it must be getting corrupted on the swap partition.  I'm inclined to discount a software bug on the basis that such a gross error would have been corrected long ago and I'm not aware of any limitations in swap partition configuration that would cause this problem.

The test I'm about to do on my own drive might help you test yours:

1) Boot off live USB/CD or USB install - in my case a full install of Meerkat that I have on a 4 GB USB drive

2) Run Gparted and delete the swap partition, recreate a new ext2 partition where the swap was

3) Run tests on that partition using badblock in write/read destructive mode (its the best way of testing)

4) If the test comes up clean, and the bad sector gets remapped, put the swap partition back the way it was.

In the meantime you might want to look at the smartdata and run the test to check the health of your drive.

I've been thinking about the alternating nature of your problem also.  If the swap partition is used on a rolling basis then it might be that you are using about half the space each time.  If there's a problem only on one part of the partition then you might only be hitting it every other time.  It would make sense to use the partition on a rolling basis to balance wear on that part of the disk but I don't _know_ this is the case.  Perhaps someone who knows more about how swap is used would like to comment at this point.


Chris

---

### Post by fabricator4 on 2011-02-07
Update:
It's not necessary to reformat the swap partition.  I thought badblocks would need an ext partition to work, but it's quite happy with swap.  It did indeed find a block with errors in my swap partition.  Just waiting for the read/write test to finish so I an see if it got remapped.

Chris

---

### Post by luajunyi on 2011-02-07
Thanks, fabricator4

I've run badblocks on the swap partition but it seems no bad blocks is found. The output is as below. Any ideas? Do I need to run in destructive read-write manner?

$ badblocks -nvs /dev/sda4

Checking for bad blocks in non-destructive read-write mode
From block 0 to 4477951
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
Pass completed, 0 bad blocks found.

---

### Post by fabricator4 on 2011-02-08
> **luajunyi said:**
> Pass completed, 0 bad blocks found.

Well, that was a theory shot down in flames, unfortunately.

If there was a serious problem I would have expected it to show up.  However, the destructive test is a lot more vigorous and has the addition benefit that if there is a bad sector then the write operation with errors will force the drives own controller to remap the sector and so get rid of the sector causing problems.  This was what happened in my case.

If you've got the inclination I would suggest you run the destructive test in any case - it can't hurt and the multiple pattern testing is more vigorous than the simple read test.

The alternating nature of the problem would seem to be a clue as to what is going on, plus if it's x that always crashes...  but it's not adding up for me.

I got curious about what the system actually does during suspend and wakeup and found [this]("http://www.advogato.org/article/913.html").  It makes the point that the video driver/card is often the culprit, but I haven't got any bright ideas for testing this.

Googling suspend problems in relation to xorg also comes up with several items relating to video and video drivers, but nothing I've found is close to the nature of problem you're experiencing.

The only things I can think of doing are trying a different release (like 10.04).  I have a few USB memory sticks with full installs of different releases on them so it's simple to test different releases and setups.  I have small swap files on all of them (about 384 MB for the 4GB sticks) and they do seem to suspend OK.  I don't know if setting up something like this would be feasible for you to see if there's a release that works better for you.

If it's a driver problem then the problem is likely to follow all the releases, but that would also be important information.

Chris.

---

### Post by P4man on 2011-02-08
I suspect the BIOS has something to do with it. Hibernating once fine, and then upon resume (rather than fresh boot) some bios initialisation is not happening causing the next hibernate to fail.

Its a long shot, but I would try experimenting with nomodeset and acpi_osi kernel boot options. Check my signature for details.

---

