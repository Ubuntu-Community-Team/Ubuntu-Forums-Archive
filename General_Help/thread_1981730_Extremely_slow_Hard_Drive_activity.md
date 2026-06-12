---
title: "Extremely slow Hard Drive activity"
date: 2012-05-17
forum: General Help
---

### Post by v0 HaVoK 0v on 2012-05-17
Ok, so first off, since I installed ubuntu it has been very slow when doing any activity on the hard drive (File Transfer, Uncompressing Files, Installing Files, especially updates).
It send within its own hard drive at around 500kb/s to 1mb/s. Horrible isn't it?
Even Worse, while doing these things, ubuntu becomes very unresponsive and freezing. I can't do anything else along side it.
One thing I noticed is that when on startup of ubuntu, it flashes this really quick : "Try (hd0,0): NTFS5: error:'prefix' is not set."
Then I went back into windows and checked Disk Management.
I added a image in the attachment to show what it looks like.
I done this because I thought it should be showing my ubuntu partition? Maybe I'm wrong?
So please does anyone know whats going on, because this is horribly, horribly slow.

---

### Post by v0 HaVoK 0v on 2012-05-18
Nobody has any ideas?

---

### Post by Fraoch on 2012-05-18
That's not your Ubuntu partition, it's your Windows partition.  What's the size of your drive?  That could be your entire drive if you have a 250 GB HDD.  It kind of looks like Ubuntu has no space to work in.  It could be trying to use swap but not getting enough and just slowing down to a crawl.

In regards to your issue...I'm no expert.  However what does Ubuntu see in regards to hard drives?  If your Ubuntu can manage it, go to System Monitor - File Systems and post the output.  Also post the Resources tab and see what's up - do you have any swap, is it being used, what's the load on the processor etc.

Ubuntu can work with NTFS-formatted partitions and has been able to for a long time, but it's not ideal.  Ideally your Ubuntu partitions should be ext3 or ext4.  That said, performance shouldn't be this slow on NTFS.

Are you sure you installed Ubuntu to your hard drive and it's not running off a USB stick or a CD?

---

### Post by v0 HaVoK 0v on 2012-05-18
> **Fraoch said:**
> That's not your Ubuntu partition, it's your Windows partition.  What's the size of your drive?  That could be your entire drive if you have a 250 GB HDD.  It kind of looks like Ubuntu has no space to work in.  It could be trying to use swap but not getting enough and just slowing down to a crawl.

In regards to your issue...I'm no expert.  However what does Ubuntu see in regards to hard drives?  If your Ubuntu can manage it, go to System Monitor - File Systems and post the output.  Also post the Resources tab and see what's up - do you have any swap, is it being used, what's the load on the processor etc.

Ubuntu can work with NTFS-formatted partitions and has been able to for a long time, but it's not ideal.  Ideally your Ubuntu partitions should be ext3 or ext4.  That said, performance shouldn't be this slow on NTFS.

Are you sure you installed Ubuntu to your hard drive and it's not running off a USB stick or a CD?
Yes I'm sure its on the hard drive, and I selected 30GB Installation size in wubi.
I added screenshots of Resources and File systems.
I'm not sure about swap, don't know how to check it, and never really understood what it was.

---

### Post by Fraoch on 2012-05-18
I'd like someone else to chime in here but I think despite reserving 30 GB for Ubuntu, it doesn't look installed - it's on /dev/loop0 which (I think) means it's mounted from your USB/CD onto your hard drive but not actually written to it.  Of course I've never installed Ubuntu alongside Windows, perhaps it's normal for that sort of installation but it just doesn't look right.

In regards to swap, that's not an issue here.  swap is a partition on your hard drive used when you run out of memory - it forms a section of very slow memory.  If you're using swap things will slow down dramatically.  You're not using swap, you have 8 GB of RAM and you're only using 850.9 MB of RAM.  You have swap space, 256 MB, but you're not using it.  No issues here.

Your processor looks lightly to moderately loaded.  It's not maxed out and shouldn't be slowing things down.

Again, something doesn't look right with respect to your root filesystem.  Can anyone else running Ubuntu alongside Windows confirm?

---

### Post by Fraoch on 2012-05-18
I looked a little online and it seems that a loop filesystem is normal with Wubi.

However I did find this:

[https://wiki.ubuntu.com/WubiGuide#Improving_disk_performance](https://wiki.ubuntu.com/WubiGuide#Improving_disk_performance)

Give that a try from inside Windows.

---

### Post by v0 HaVoK 0v on 2012-05-18
> **Fraoch said:**
> I looked a little online and it seems that a loop filesystem is normal with Wubi.

However I did find this:

[https://wiki.ubuntu.com/WubiGuide#Improving_disk_performance](https://wiki.ubuntu.com/WubiGuide#Improving_disk_performance)

Give that a try from inside Windows.

Ok, so I started that, but I have a problem, I here that red is unmovable files, and well look at the attachment I have a lot of red files.
Will report back here and let you know how it went when its done. Thanks for the help.

---

### Post by houseworkshy on 2012-05-18
Not fond of wubi installs.  I tried a couple years ago and for various reasons, which I don't remember in detail, abandoned the method.  Much better to install to a partition or another drive, have the full duel boot options and either system dead when the other runs ( though linux can still read and write to the windows drive if asked ).  This isn't actually helping your problem, other than recomending a clean install of a true duel boot instead,  so call it a bump.

---

### Post by v0 HaVoK 0v on 2012-05-18
> **houseworkshy said:**
> Not fond of wubi installs.  I tried a couple years ago and for various reasons, which I don't remember in detail, abandoned the method.  Much better to install to a partition or another drive, have the full duel boot options and either system dead when the other runs ( though linux can still read and write to the windows drive if asked ).  This isn't actually helping your problem, other than recomending a clean install of a true duel boot instead,  so call it a bump.

I might look into this and see how its done, I just don't want to lose lots of important files I have.
So wubi was the easiest and safest option for me, just never thought it would have this problem, my ubuntu's performance is horrible, I used to run 9 or 10. something (Can't remember now) and it wasn't dual boot and they were a lot faster than my windows.

---

### Post by houseworkshy on 2012-05-18
Yes the files are always the most important thing.  All the ones that matter in linux should be in /home/YourUserName, in windows under Documents and settings.  If, from linux, you take a look at the properties of each then you'll know how big any backup medium would need to be.  If one is mostly concearned with ones work and things that can't be replaced it's often not much after one subtracts anything one can reinstall or download again, videos are usually the biggest and mostly replaceable anyway.  Whatever you choose to do a backup of whats crucial is a must.  I've found that when the important stuff is safe one can relax about the machine, reinstall at the drop of a hat if the fixes don't work etc.  An external usb hd was one of the best purchases I've made, allows me to dump the lot, to be sorted through at leisure, and fix the machine right now.

---

### Post by v0 HaVoK 0v on 2012-05-18
> **Fraoch said:**
> I looked a little online and it seems that a loop filesystem is normal with Wubi.

However I did find this:

[https://wiki.ubuntu.com/WubiGuide#Improving_disk_performance](https://wiki.ubuntu.com/WubiGuide#Improving_disk_performance)

Give that a try from inside Windows.

Ok, This helped a little, Its still slow, but now it send around 2-3mb/s faster, it still becomes un-responsive, but a lot less.

---

