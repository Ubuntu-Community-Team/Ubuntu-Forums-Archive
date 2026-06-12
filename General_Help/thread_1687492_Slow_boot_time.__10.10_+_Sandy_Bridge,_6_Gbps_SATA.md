---
title: "Slow boot time.  10.10 + Sandy Bridge, 6 Gbps SATA"
date: 2011-02-14
forum: General Help
---

### Post by oaul on 2011-02-14
I just built a really fast computer, and it takes quite a long time for Ubuntu 10.10 to boot.  It wouldn't be so bad if the boot process didn't involve 20 seconds of doing pretty much nothing:

[See my Bootchart HERE]("http://img405.imageshack.us/f/paulboxmaverick20110213.png/")

I dual-boot into Windows 7, but I don't have an entry for the win7 partition in fstab.  Could that somehow be why it's so slow?

I don't know what async is... so can someone take a look at that and tell me what's slowing me down and how to fix it?

---

### Post by oaul on 2011-02-14
bump.

---

### Post by searchfgold6789 on 2011-02-14
Well, I will keep thinking about this, but I can tell you right off the bat it has nothing to do with not having win7 in your fstab :)
Sandy Bridge. Nice.
I'm stuck with a p3 750 mhz :lolflag:

---

### Post by oldfred on 2011-02-14
Hard drives do not run any faster on a 6G/s port.  Unless you are  using a SSD? Up until your post I have not seen anyone boot with a drive in the 6G/s port. They all have had to change to the 3G/s ports.

They said it was really fast once they got it going:
[http://www.phoronix.com/scan.php?page=article&item=intel_sandy_speed&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_sandy_speed&num=1)

SATA 6GB/sec ports wait for 11.04
[http://ubuntuforums.org/showthread.php?t=1614764](http://ubuntuforums.org/showthread.php?t=1614764)
[http://furiouspurpose.me/2010/12/27/the-new-sata-6-gbs-hardware-on-ubuntu-linux/](http://furiouspurpose.me/2010/12/27/the-new-sata-6-gbs-hardware-on-ubuntu-linux/)

See also this thread.
[http://ubuntuforums.org/showthread.php?t=1666626](http://ubuntuforums.org/showthread.php?t=1666626)

---

### Post by cascade9 on 2011-02-14
> **oldfred said:**
> Hard drives do not run any faster on a 6G/s port.  Unless you are  using a SSD? Up until your post I have not seen anyone boot with a drive in the 6G/s port. They all have had to change to the 3G/s ports.

Thats mainly because the older intel chipsets didnt do SATAIII, just SATAII. So motherboards manufacturers put nasty SATAIII controllers onto motherboards. When you have a decent controller with support (intel, AMD) then SATAIII should be no problem at all. 

I know there has been some problems with the SATAII controller on cougar point. Though AFAIK its only the SATAII ports that have a problem. 

BTW, your right, currently HDDs just arent fast enough for SATAIII to make any real difference. ;)

*edit- its async thats causing the big delay. IIRC async is used for controlling block devices, so it probably is drive related. If you arent doing something strange like using IDE mode (does cougar point even do IDE mode?) I'd try disconnecting the DVD/CD drive for a start.

---

### Post by searchfgold6789 on 2011-02-14
I don't know if this will help, but as I mentioned before I have a very old computer that probably was out before SATAIII.
And it doesn't take that long to start.
So I guess you should heed oldfred's post??

---

### Post by oaul on 2011-02-14
Once I'm booted, the computer is darn fast.  I get 1M super pi scores of 10.1s ... under wine.

I also use a discrete graphics card, which suggests I will not see any of the problems with H67 chipset a la Phoronix.  Indeed, I have not seen any glitching or instability.

But did you guys look at the bootchart?  20 seconds of NOTHING!  What's up with that?  I didn't think it had to do with Sata III, but I figured I'd offer that as a possible explanation.

Would it help if I posted dmesg?  What logs, if any, would shed any light?

---

### Post by oaul on 2011-02-14
Didn't see the drive suggestion from cascade.  I'll give that a go soon and update this thread...

---

### Post by oaul on 2011-02-14
Nice, cascade9.  Removing the blu ray drive cut my boot time in half!

Now, who wants to diff my boot logs and tell me how I might be able to fix this without having to unplug my drive? :D

The attached dmesg-noBluRay is just that.  It's about twice as fast as the boot corresponding to dmesg-withBluRay.

Also, check out the bootchart for the faster boot (sans Blu Ray) [HERE]("http://img87.imageshack.us/i/paulboxmaverick20110214.png/").

---

### Post by cascade9 on 2011-02-15
What motherboard and BluRay drive are you using?

*edit- I was semiguessing. I'm just glad it was the optical drive, not the HDD.

---

### Post by oaul on 2011-02-15
Turns out /dev/sr0 wasn't there!  10.10 didn't even recognize my drive the entire time.

I sissy'ed my way out and downgraded to 10.04 since I have a separate /home partition.  Now the drive works fine and my boot time is <20 seconds.  Hurray!

I suppose I could have downgraded the kernel but I figured downgrading the distro would have saved me more time in the long run.  

I have a Gigabyte ga-p67a-ud3 and a LG WH10LS30 10x burner.  As an aside, the mobo sucks - not only because of the infamous Sandy Bridge/Cougar Point bug, but the BIOS is glitchy as hell during POST.  Tell your friends, tell your neighbors.

---

### Post by cascade9 on 2011-02-15
Tried updating the BIOS? 

BTW, thanks for the info. ;)

---

### Post by oaul on 2011-02-15
Yup - I'm using the v5 of the gigabyte BIOS, which was downgraded from v6 (buggy as hell), which was upgraded from v4 (buggy as hell).

v5 is still pretty buggy!

All I need is awesome window manager, emacs, latex, terminal, and chrome.  So 10.04 is a fine solution for me.

---

### Post by cascade9 on 2011-02-15
Geez, thats not good. It might be a chipset issue though, generally I've found gigabyte BIOSes are OK.

---

