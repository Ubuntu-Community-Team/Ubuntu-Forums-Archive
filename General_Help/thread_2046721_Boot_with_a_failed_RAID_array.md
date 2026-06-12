---
title: "Boot with a failed RAID array"
date: 2012-08-23
forum: General Help
---

### Post by danBhentschel on 2012-08-23
Brief background:

Mythbuntu 12.04 LTS
Core i5 (4 cores)
4 GB RAM
17 hard drives:
40GB SSD
11 x 1.5 TB
5 x 3.0 TB

I am in the process of transferring data from an old 15TB array to a new 14TB array. Neither of the arrays contains the root filesystem. That is on a separate SSD. In addition to the SSD, there are 12 internal drives, and 4 in USB docking stations.

Unfortunately, the USB drives are periodically "disappearing" during the copy process. My best guess is that I am exceeding the power draw on my 650W supply. I am not too concerned, though. This jury-rigged setup is only temporary until I get everything copied over. Since the USB drives are part of the "old" array, which is mounted read-only, there is no data loss when they disappear. I just need to reboot, force-assemble the array, and then restart the copy process.

Here's where the problem comes in. When I reboot, I get dropped into a debug console until I can repair the broken array. Is there any way to disable this behavior? The debug console is completely unnecessary since the failed array isn't even in my fstab. I'd like to be able to remotely reboot the machine and fix the array. As it is now, I need to be physically in front of my machine to recover from this state.

Any recommendations?

 - dan

---

### Post by TheFu on 2012-08-23
Have you considered unplugging all the drives that aren't involved in the copies to reduce the total power needed?  If your array is only 4 wide, that should be doable.

Have you learned any lessons that you can share? I'd be interested.

---

### Post by intel on 2012-08-23
I'm confused by your description,

Is it an array(raid) or a LVM ?
I'm guessing you mean LVM as the "array" capacities seem to be same as disk capacities

In which case you just copy the LVM stripes/partitions/ 
(you did remember to do multiple stripes/partions/pv per disk  to LVs yes?)
over to the new VGs on new disks, one by one, copying with only involved disks connected.

Cheers!

---

### Post by danBhentschel on 2012-08-23
I actually have unplugged all the drives I can. One array is 11 x 1.5 TB drives (it's actually RAID 5 with 12 disks, but I'm running it degraded) and the second array is 5 x 3.0 TB drives (RAID 5 x 6 disks, running degraded).

I'm not sure what is worth sharing and what isn't. Here's a few tidbits that come to mind, though:

[LIST]
[*]To run with degraded disks, add "bootdegraded=true" into GRUB options
[*]When using software RAID, it is very important to disable write caching on each drive (hdparm -W0 /dev/XXX)
[*]You can disable write caching by default by editing /etc/hdparm.conf
[*]There is a script in /etc/cron.d/mdadm that checks the arrays monthly. For VERY large arrays, this can take such a long time and slow down the system enough that it is not worth it. I disabled this script.
[/LIST]

---

### Post by danBhentschel on 2012-08-23
They are not LVMs. They are mdadm RAID 5 arrays.The sizes match because I am running them degraded during the copy process. If I were to run them as full RAID 5 arrays, that would require 19 drives to be connected to the machine at a time. I would have needed to buy 2 more USB docking stations, which I was not willing to do.

---

### Post by TheFu on 2012-08-23
I would add that using more than 4 HDDs in a RAID 5 set adds complexities that are best avoided.  For large databases where performance is critical, an 8 or 16-way stripe can make sense, but when using USB drives, probably not so much.  I've always found USB device connections to be flaky.  Perhaps that is just my USB controllers and ports with this issue.

Using 4 drives gets you 80% of the theoretical performance improvements from having multiple drives.  4 drives are the easy answer for RAID sets. Using more than 4 is harder to justify due to the extra hassles, IMHO.

For $700 you can get a (20) HDD external eSATA array with the same performance as internal SATA connected drives. [http://www.addonics.com/products/rt55sn25sp.php](http://www.addonics.com/products/rt55sn25sp.php)

I like to limit the size of my file systems to the size that can be easily backed up to a single device - about 1.5TB by the time you count overhead on a 2G HDD.

Still, having all those drives connected is impressive.

---

### Post by danBhentschel on 2012-08-24
> **TheFu said:**
> I would add that using more than 4 HDDs in a RAID 5 set adds complexities that are best avoided.  For large databases where performance is critical, an 8 or 16-way stripe can make sense, but when using USB drives, probably not so much.  I've always found USB device connections to be flaky.  Perhaps that is just my USB controllers and ports with this issue.

Using 4 drives gets you 80% of the theoretical performance improvements from having multiple drives.  4 drives are the easy answer for RAID sets. Using more than 4 is harder to justify due to the extra hassles, IMHO.

**Be advised. This post contains a lot of boring historical drivel.**

I would agree with this, in principle, as my experience has been similar to what you describe. I started playing with RAID in 2008 soon after I setup my first MythTV box. My first attempts at RAID were all external USB drives connected to my combo frontend/backend. After outgrowing my first array of 3 1TB drives, I opted to add a second array of 3 1TB drives and separate my "videos" (recorded VHS and ripped DVDs) from my "recordings". I had a lot of problems with my two arrays as USB drives were flaky and kept dropping off. I eventually lost my entire array of recordings in 2009, and while this was disappointing to me, I would have been much more disappointed if I had lost my other array because it's a lot of work to re-record and re-rip my entire collection.

After this tragedy, I decided to buy a new machine to use as a separate backend, which would contain all of my storage as internal drives. I purchased 4 1.5 TB drives and set them up as a 4.5TB RAID 5 array. I kept my 6 USB drives and made a 5 TB array out of them. These drives were a "backup" array. The main array was rsync'd to the backup array on a weekly cadence, to protect against future failure. I opted for a single "main" array for the following reasons:

[LIST]
[*]A single array is easier to backup and restore
[*]It is easier to manage free space on a single array. With two arrays before, I was constantly frustrated with having free space on the "wrong" array.
[*]One array has less "wasted" space than multiple arrays. A single array needs a single extra parity disk. Two arrays need two extra disks. This was an important factor because extra disks use more money, drive bays, and SATA ports.
[/LIST]

Over time, as the array got full, I continued to add drives. Eventually, I ran out of SATA ports and needed to buy a new SATA card ([http://www.newegg.com/Product/Product.aspx?Item=N82E16816132008]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816132008")). Soon after the purchase of this new card, the stability of my array took a nose dive, and after struggling with it for a couple of months, in mid-2010 I decided to upgrade my backend with a much beefier power supply, and a new motherboard ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813131400]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131400")) with 9 onboard SATA ports. This improved the stability of my array greatly, and I continued to expand my array.

However, in 2011 I ran out of SATA ports again, and again I resorted to an SATA expansion card ([http://www.newegg.com/Product/Product.aspx?Item=N82E16815124027]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815124027")). I ended up buying 2 of these cards, which brought my RAID array to 12 x 1.5TB internal drives earlier this year. At about this time, I decided to drop my "backup" array. It had grown to 16 external 1TB USB drives, and the backup array itself was so unstable that I decided it wasn't worth it any more. I sold off all the drives on Ebay. My internal RAID array had been rock solid for a couple of years, and I was getting pretty confident in it.

Once I hit this mark, though, my system started showing instabilities again. I started planning to replace the 12 drives with a smaller number of larger drives, but the drive market was bad at the time, and the cost would have been too high. It wasn't until recently that 3.0TB drives hit $150, which would allow me to buy the 6 required drives for under $1000. I am eagerly anticipating having my main RAID array back down to "only" 6 drives again.

> **TheFu said:**
> For $700 you can get a (20) HDD external eSATA array with the same performance as internal SATA connected drives. [http://www.addonics.com/products/rt55sn25sp.php](http://www.addonics.com/products/rt55sn25sp.php)

I like to limit the size of my file systems to the size that can be easily backed up to a single device - about 1.5TB by the time you count overhead on a 2G HDD.

Still, having all those drives connected is impressive.

That box is very impressive, and I have considered getting something similar to it several times. I have never stumbled on something quite like that one, though. I have decided against hardware RAID solutions for the following reasons:

[LIST]
[*]Generally, they are pretty expensive. Even that $700 box you mention is beyond what I am willing to spend right now.
[*]The less expensive RAID enclosures that might be within my price range typically have pretty scary reviews that talk about port failures and so forth.
[*]If my RAID array is tied to a piece of hardware, then the only way to recover it is to replace the hardware. What if the enclosure dies two years from now, and I can't replace it with the exact same enclosure? What happens to my data? Software RAID doesn't have this problem.
[*]Software RAID is inherently much more flexible. Case in point: I am currently copying my old array to a new array, and I am only able to do so because I was able to pull 4 of my drives out of my box and connect them via USB. I would agree with the argument that this is due to poor planning on my part, but still, I am able to recover from this bad situation because of the flexibility of software RAID.
[*]There are a lot of tools out there to help me to deal with failed mdadm arrays. There is a lot of community knowlege available. If I go with some relatively obscure hardware solution and run into problems, I'm pretty much on my own.
[/LIST]

Just my $.02. Take it for what it's worth. I don't claim to be an expert. ;)

Now, if you're still reading (and still awake) I'll say that, while all this discussion has been fun, at least for me, it still doesn't answer my original question: How can I convince my Ubuntu machine to boot up when one of the non-essential mdadm arrays is in a "failed" state?

 - dan

---

### Post by TheFu on 2012-08-24
> **danBhentschel said:**
> <snip>
though. I have decided against hardware RAID solutions for the following reasons:

[LIST]
[*]Generally, they are pretty expensive. Even that $700 box you mention is beyond what I am willing to spend right now.
[*]The less expensive RAID enclosures that might be within my price range typically have pretty scary reviews that talk about port failures and so forth.
[*]If my RAID array is tied to a piece of hardware, then the only way to recover it is to replace the hardware. What if the enclosure dies two years from now, and I can't replace it with the exact same enclosure? What happens to my data? Software RAID doesn't have this problem.
[*]Software RAID is inherently much more flexible. Case in point: I am currently copying my old array to a new array, and I am only able to do so because I was able to pull 4 of my drives out of my box and connect them via USB. I would agree with the argument that this is due to poor planning on my part, but still, I am able to recover from this bad situation because of the flexibility of software RAID.
[*]There are a lot of tools out there to help me to deal with failed mdadm arrays. There is a lot of community knowlege available. If I go with some relatively obscure hardware solution and run into problems, I'm pretty much on my own.
[/LIST]
Just my $.02. Take it for what it's worth. I don't claim to be an expert. ;)

Now, if you're still reading (and still awake) I'll say that, while all this discussion has been fun, at least for me, it still doesn't answer my original question: How can I convince my Ubuntu machine to boot up when one of the non-essential mdadm arrays is in a "failed" state?
- dan

**Answer: **Remove the non-essential array from the machine.  Be certain you backup the configuration for that array so when you need to put it back, you can.

If you remove all arrays, does the machine boot?

I need to reread your posts to see if there is something more I can offer.

**More boring commentary:**
At my day job, I've worked with disk storage vendors at length. If they  make arrays and are a name-brand, I've been part of the deployment.  I  work as a technical architect for clients of all sizes, so not "hands  on" with the equipment, but I do know how they are deployed in the  largest enterprises to avoid issues.  That knowledge applied to a home  situation is what I'm trying to share.

BTW, that Addonics solution does not mandate hardware RAID use.  I have a 4 disk version  [http://addonics.com/products/mst.php](http://addonics.com/products/mst.php) and use mdadm too - for all the reasons that you've stated.  I started with a Promise FastTrak RAID controller, but "linux support" meant a 2 yr old kernel was required.  That is more like anti-linux-support to me. The array has been working since 2007 non-stop with just a few loose-cable hiccups in the first year. It has been migrated between 2 machines once - without issue. I was shocked how easy it was.

Wider arrays (more disks in the stripe) become more hassle when there are issues than any home user wants.  Everything seems fine, until it isn't. Then it just sucks.  I try to organize storage / partitions by what can be easily backed up to a single external HDD.  Sometimes that is a hassle, but knowing that backup storage is not tied to disk array issues lets me sleep better at night. It is easy enough using soft-links to make storage "appear" to be larger than it is.  I've been using softlinks for almost 20 yrs in that way across almost every type of UNIX system.

I've never run MythTV, but I do use XBMC and it has fairly rigid storage directory structure requirements too.

**USB** -- even USB3 -- **is not your friend for day-to-day storage.**  Bus  throughput numbers do not make spinning disks any faster. USB3 has  queuing issues under Linux too, in my experience.  I've seen mention about fixing it, but my systems still see it today. There are times when the disks appear to do nothing for 30 seconds because there are too many items in the USB queue.  USB is great for backup  media and short term, emergency, extra storage for a month or two.  Basically, 2 or 3 tasks at a time, not for general purpose needs.

**For external storage, MP eSATA is your friend.**  Relatively cheap external arrays use this. It reduces the power needed inside a storage server, so the server doesn't become unstable.

At home, I own a 4 HDD Addonics external array [http://addonics.com/products/mst.php](http://addonics.com/products/mst.php) . I'm in the process of designing the upgrade for it as the current disks are 5+ yrs old (RAID5-mdadm).  There is nothing wrong with it. I simply need more storage, more flexibility and really need to retire those HDDs before failure. This same JBOD array purchased in 2007 is still sold today, so I'm not concerned about it going away.  Swapping out adapter modules is part of the reason I like Addonics.  When new HDDs are purchased for this array, I'll backup to external eSATA/USB3 partitions, swap out the HDDs inside the array, partition it with 1.5TB partitions and create multiple software RAID5 sets.  Each disk will probable be either 1.5TB or 2TB, so there will be at least 3 RAID sets. Those sizes are a conscious decision.  Until I have backup storage available, I will not expand into the newer 2nd or 3 arrays. If I can't backup the storage, then I don't want it available.  Inside the array, don't use "green" or "blue" cheap HDDs, only "black" or the equiv from other makers. There is a reason those cost more.

I use cheap external USB2, USB3 and eSATA storage for backups.  If I ever fill a larger external disk array, I'll probably switch to  having 2 - one with RAID5 or RAIDz storage and the other with JBOD just for backups.

Avoiding future hassles is my day job.

---

### Post by danBhentschel on 2012-08-24
> **TheFu said:**
> **Answer: **Remove the non-essential array from the machine.  Be certain you backup the configuration for that array so when you need to put it back, you can.

If you remove all arrays, does the machine boot?

I need to reread your posts to see if there is something more I can offer.

Yeah. I think you're missing the point a bit. O:) I have a **very temporary** setup that is causing one of my non-essential RAID arrays to fail on a regular basis. It's easy to recover from, though, since I am mounting the array read-only, so I'm not concerned about data corruption. The solution is to reboot the machine (so the USB ports come back) and then when the debug console comes up (because I have a failed mdadm array) i just execute:

mdadm --stop /dev/md0
mdadm --assemble --force /dev/md0
reboot

Then, Ubuntu boots back up with my RAID array online again, and none-the-worse-for-wear. Unfortunately, in order to perform this band-aid, I need to be physically in front of my machine, since it requires going into the debug console. I would like a way to be able to recover from a failure remotely (i.e. while I'm at work). However, if I reboot the machine from work, I know that it will boot up into the debug console, and then I'm stuck until I can get home and take care of it.

Does that make the situation clearer? Of course, if I don't get an answer within the next few days, it will become a moot point. The data copy from old RAID to new RAID is coming closer to completion, and then the USB drives will go away and I will be back down to "only" 7 drives in the box.

---

### Post by TheFu on 2012-08-24
Nice recap.

Shot in the dark:
Is it possible to not reboot the machine after the USB drives drop?  Perhaps unloading the USB storage module, then reloading it and reassembling the array?  I know sometimes the USB drivers need a hardware reset.

The other option is to move the array startup code to happen later in the boot, after the network has started?   On my 10.04 box, mdadm starts in the S25* startup.  Push that out to be S99* instead.  Or even disable it at boot and manually run /etc/init.d/mdadm start after a reboot.  **update-rc.d** is the easy way to change the levels, I'd guess. Personally, I'd just mv the softlinks in the rc3.d/ and similar dirs.

After all that, I'd probably add those mdadm --reassemble .... commands to the end of /etc/rc.local for your temporary fix.

---

### Post by danBhentschel on 2012-08-29
Thanks for the reply. I haven't responded because I haven't had much opportunity to try out your suggestions. My system has been pretty stable for the past several days, and now the copy process is just about complete. However, I have been able to try some things. I will respond below.

> **TheFu said:**
> Is it possible to not reboot the machine after the USB drives drop?  Perhaps unloading the USB storage module, then reloading it and reassembling the array?  I know sometimes the USB drivers need a hardware reset.

I tried this out. I tried resetting using a procedure found here:

[http://hack2live.blogspot.com/2008/06/ubuntu-linux-restart-usb-to-reset-stuck.html]("http://hack2live.blogspot.com/2008/06/ubuntu-linux-restart-usb-to-reset-stuck.html")

This doesn't seem to work on modern installations:

```
root@raidman:~# modprobe -vr ehci_hcd
FATAL: Module ehci_hcd is builtin
```

I tried to do the same with the usb_storage module. This worked to the extent that I was able to remove and re-add the module, but it did not make any drives re-appear. I also tried the advice here:

[http://www.roman10.net/how-to-reset-usb-device-in-linux/]("http://www.roman10.net/how-to-reset-usb-device-in-linux/")

This caused all of my usb devices to disappear, including mouse and keyboard. Nothing came back.

I also tried:

```
echo 1 > /sys/bus/pci/devices/0000\:00\:1a.0/reset
```

This did cause the USB to reset, and I was able to see some other USB devices disappear and re-appear, but the drives I was looking for still did not come back.

> **TheFu said:**
> The other option is to move the array startup code to happen later in the boot, after the network has started?   On my 10.04 box, mdadm starts in the S25* startup.  Push that out to be S99* instead.  Or even disable it at boot and manually run /etc/init.d/mdadm start after a reboot.  **update-rc.d** is the easy way to change the levels, I'd guess. Personally, I'd just mv the softlinks in the rc3.d/ and similar dirs.

Tried this as well. Unfortunately, I think that there is something that loads mdadm from GRUB, even before the root filesystem is mounted. Remember, the root filesystem can be on an madam volume itself. Disabling mdadm in the rc*.d directories didn't have any effect. My box still booted up in the debug console.

I also found some reference to adding the kernel flags "rd_NO_DM rd_NO_MD" to GRUB:

[https://fedoraproject.org/wiki/Dracut/Options]("https://fedoraproject.org/wiki/Dracut/Options")

Unfortunately, this also did nothing for me. I suspect that these flags are RedHat-specific.

Thanks again for your help, and advice. It really was appreciated. At this point, I don't think I'm going to experiment any more. I no longer need this.

 - dan

---

