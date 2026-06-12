---
title: "Transfer rates to external USB Why is Windows 7 faster in comparison with Ubuntu?"
date: 2012-07-25
forum: General Help
---

### Post by siddartha on 2012-07-25
On Windows 7 64bit transfer rates from the internal hard drive to a USB3 drive connected through a USB2 connection is 18 to 22 Mo/s. Now, on Ubuntu 64bit and the same configuration I get 2 to 6Mo/s. What can I do to make Ubuntu a little bit faster?

---

### Post by vasa1 on 2012-07-25
Why don't you make the title more specific?

---

### Post by siddartha on 2012-07-25
> **vasa1 said:**
> Why don't you make the title more specific?

So there's no hope. I kept reading about how fast Linux can be.

---

### Post by cottfcfan on 2012-07-25
You've probably hit on one of the very few instances were windows is superior.
If that's your only issue, live with it.
I dual boot Windows 7 64 bit & Kubuntu 12.04 at present.
Kubuntu gets used around 99% of the time for it's speed, ease of use & stability.
Nothings perfect, but what do you want for free?

---

### Post by greenpeace on 2012-07-25
> **siddartha said:**
> So there's no hope.

Hi, I don't think that was what he was saying... 

On my box (ubuntu 64bit) I have a very fast throughput with my USB devices (25-30MB / s), and have never seen slow connections on any ubuntu machine I've used.

Perhaps you could give a few more details, and then when the guys who know more about these things comes online they can help you troubleshoot.

Also, have you searched the forum to see if other people have had similar problems?

You should probably post the output of (at least) the following terminal commands (with the USB drive plugged in) to help them:

```

lsusb 
uname -a

```

(don't forget to use the CODE tags to make the output readable)

Also, please include the version of the distro you're using... (Ubuntu 12.04?)

thanks!

---

### Post by siddartha on 2012-07-25
> **greenpeace said:**
> Hi, I don't think that was what he was saying... 

On my box (ubuntu 64bit) I have a very fast throughput with my USB devices (25-30MB / s), and have never seen slow connections on any ubuntu machine I've used.

Perhaps you could give a few more details, and then when the guys who know more about these things comes online they can help you troubleshoot.

Also, have you searched the forum to see if other people have had similar problems?

You should probably post the output of (at least) the following terminal commands (with the USB drive plugged in) to help them:

```

lsusb 
uname -a

```(don't forget to use the CODE tags to make the output readable)

Also, please include the version of the distro you're using... (Ubuntu 12.04?)

thanks!

Oh. Ok. It's a clean install of Ubuntu 12.04, no upgrades. I wanted to do a large backup and hoped for the better. Now I'm back in Windows doing that. So it would be a while till I get a lsusb. The drive is one WD passport blue hard drive. It was boxed with some silly software, but I got rid of all that was inside. Now it's a plain NTFS drive with one large partition.

---

### Post by siddartha on 2012-07-25
> **cottfcfan said:**
> Nothings perfect, but what do you want for free?

Well, windows is free too. I just bought a laptop. And, its category it was cheaper than laptops that come bundled with some other OS.

---

### Post by Grenage on 2012-07-25
> **siddartha said:**
> Well, windows is free too. I just bought a laptop. And, its category it was cheaper than laptops that come bundled with some other OS.

/pat

---

### Post by philinux on 2012-07-25
Title changed.

There is an outstanding bug on this if I can locate others I'll post the link.

---

### Post by techvish81 on 2012-07-25
just format it as fat32 and the speed will be doubled.  

there are several threads about usb transfer speed here and there are also a lot of threads in win7 related sevenforums about external usb being slow. so i think this problem has something to do with usb media being recognised differently by different OSs. and sometimes misinterpreted as usb 1.0 device or a slow speed device.

it does not happen everytime, my external hdd writes @55MB/SEC!, under ubuntu,  it is formatted as fat32.   i faced problems while writing on flash media but now i managed to get 7mbps, by doing some workarounds suggested here in some threads. 

you can also search for solution in threads here.  actually it is better to search before posting.

---

### Post by kurt18947 on 2012-07-25
> **techvish81 said:**
> just format it as fat32 and the speed will be doubled.  

there are several threads about usb transfer speed here and there are also a lot of threads in win7 related sevenforums about external usb being slow. so i think this problem has something to do with usb media being recognised differently by different OSs. and sometimes misinterpreted as usb 1.0 device or a slow speed device.

it does not happen everytime, my external hdd writes @55MB/SEC!, under ubuntu,  it is formatted as fat32.   i faced problems while writing on flash media but now i managed to get 7mbps, by doing some workarounds suggested here in some threads. 

you can also search for solution in threads here.  actually it is better to search before posting.

I've run into the NTFS problem using a SATA drive in a USB enclosure.  And yes, FAT32 was much faster.  On another SATA-USB enclosure, the connection was indeed recogized as USB 1.1 -- 1.2 MB./sec., presumably a combination of the chip set in the enclosure and Linux drivers. That one was cheap - $5 off Amazon so I wasn't surprised.

I also found another surprise.  Win 7 doesn't want to format to FAT32, only NTFS or exFAT.  There's a way to format FAT32 in Win 7 but it involves using the command line.  COMMAND LINE?? in WINDOWS 7?!?!  Oh no!!!!   :P

---

### Post by techvish81 on 2012-07-25
> **kurt18947 said:**
> 

I also found another surprise.  Win 7 doesn't want to format to FAT32, only NTFS or exFAT.  There's a way to format FAT32 in Win 7 but it involves using the command line.  COMMAND LINE?? in WINDOWS 7?!?!  Oh no!!!!   :P

it's really a surprise.  The OS, which for the sake of compatibility  has still got the ruins of old dos and win3.1,  doesn't think accordingly about it's old filesystem. (which linux still supports in every way :-) ) :confused:

---

### Post by philinux on 2012-07-25
Found bug report. click the "does this bug affect you" to increase the Heat.

Don't post a me too comment unless it adds something new.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069)

---

