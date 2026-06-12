---
title: "64-bit computer"
date: 2010-06-01
forum: General Help
---

### Post by AmpersUK on 2010-06-01
Hi all,

I am a little uncertain about this message in the Ubuntu page:
[INDENT]           [COLOR=Blue]Click the big orange button to download the latest version  of Ubuntu. You will need to create a CD or USB stick to install Ubuntu.[/COLOR]
         
[COLOR=Blue]**32-bit** -  Recommended for most users[/COLOR]
[COLOR=Blue]**64-bit** - Not  recommended for daily desktop usage[/COLOR]
[/INDENT]                      I have a 64-bit computer with 8GB of memory. and am a little alarmed at the new message against "64-bit" which wasn't there when I originally downloaded the software and installed it. I have 10.04 64-bit Ubuntu installed.



There are many minor issues that I am not happy with but rather than complaining, I decided to wait until they all got fixed. But now it doesn't look as if they will be.


What should I do? 



Would it help to leave Ubuntu *(which I am reluctant to do)* and find a distro that has solved the problems for desktops working with 64-bit?


Or will 32-bit work on my machine?


I know a 32-bit machine with more than 3GB of memory is now supported with Ubuntu's Lucid 32-bit, but can I run a 32-bit version on my 64-bit computer and still access the 8GB of RAM?


I purchased 64-bit because my supplier (Power Computing of Bedofrd) has stopped making 32-bit machines.


Any help on this issue would be appreciated.



Ampers

---

### Post by HereInOz on 2010-06-01
The 32 bit version will work on a machine with 64 bit hardware.  

The only thing you will lose is the ability to take advantage of the uniquely 64 bit stuff, like the ability to access more than 3.2GB RAM, and things like that.

If you are unhappy with the 64 bit version, install the 32 bit version, it will work fine.

Also, check out this post on the same matter.

[http://ubuntuforums.org/showthread.php?t=1498697](http://ubuntuforums.org/showthread.php?t=1498697)

Cheers.

---

### Post by philinux on 2010-06-01
@AmperUk,

That message only sprung up with lucid. Not sure why at the moment. I've been using 64 bit for 18 months on my desktop with no problems at all. 

The only issue is installing flash. The 64 bit alpha from adobe is way better than 32 bit with the wrapper to install it.

If you got 8gig ram then 64 bit is the way to go.

It's bugged too.
[https://bugs.launchpad.net/ubuntu-website/+bug/585940](https://bugs.launchpad.net/ubuntu-website/+bug/585940)

I've also emailed the webmaster at ubuntu.com

---

### Post by dcstar on 2010-06-01
> **philinux said:**
> 
........
It's bugged too.
[https://bugs.launchpad.net/ubuntu-website/+bug/585940](https://bugs.launchpad.net/ubuntu-website/+bug/585940)

I've also emailed the webmaster at ubuntu.com

Somebody must have a large bullet hole in the foot by now over this......  :(

---

### Post by popey on 2010-06-01
Just to clear up some misinformation. It _is_ possible to address more than 3.2GB on a 32-bit install of Ubuntu.

If you perform a clean install of 9.10 or 10.04 it should detect that you have more than 3.2GB of RAM and install a kernel (PAE) which supports it.

If you upgraded your RAM after installing, or you installed an older version of Ubuntu and then upgraded, you might not have the PAE kernel installed. In that situation just install the package 'linux-image-generic-pae' to address all the available RAM in your computer.

[http://packages.ubuntu.com/linux-image-generic-pae](http://packages.ubuntu.com/linux-image-generic-pae)

This is a meta package which will pull in the latest PAE kernel for your release. Note this is the current one for Ubuntu 10.04 (Lucid):-

[http://packages.ubuntu.com/lucid/linux-image-2.6.32-21-generic-pae](http://packages.ubuntu.com/lucid/linux-image-2.6.32-21-generic-pae)

Note from the description: "Geared toward 32 bit desktop systems with more then 4GB RAM."

Note: On some computers this doesn't work, so 64-bit might be better for those people, but for many this does work.

---

### Post by Merk42 on 2010-06-01
> **popey said:**
> Just to clear up some misinformation. It _is_ possible to address more than 3.2GB on a 32-bit install of Ubuntu.

If you perform a clean install of 9.10 or 10.04 it should detect that you have more than 3.2GB of RAM and install a kernel (PAE) which supports it.

If you upgraded your RAM after installing, or you installed an older version of Ubuntu and then upgraded, you might not have the PAE kernel installed. In that situation just install the package 'linux-image-generic-pae' to address all the available RAM in your computer.

[http://packages.ubuntu.com/linux-image-generic-pae](http://packages.ubuntu.com/linux-image-generic-pae)

This is a meta package which will pull in the latest PAE kernel for your release. Note this is the current one for Ubuntu 10.04 (Lucid):-

[http://packages.ubuntu.com/lucid/linux-image-2.6.32-21-generic-pae](http://packages.ubuntu.com/lucid/linux-image-2.6.32-21-generic-pae)

Note from the description: "Geared toward 32 bit desktop systems with more then 4GB RAM."

Note: On some computers this doesn't work, so 64-bit might be better for those people, but for many this does work.
Though [64bit Ubuntu has other advantages](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1) than just easily using more RAM.

---

### Post by popey on 2010-06-01
> **Merk42 said:**
> Though [64bit Ubuntu has other advantages](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1) than just easily using more RAM.

Sure, and those performance graphs speak for themselves. I was merely addressing one of the main misconceptions about 32bit-vs-64-bit. Thanks for the link!

---

### Post by philinux on 2010-06-01
While were at it.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by MooPi on 2010-06-01
> **philinux said:**
> While were at it.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)
Nice article, Thanks. I use 64 bit but only have issues with Hulu. Not a game changer but an annoyance to say the least.

---

### Post by AmpersUK on 2010-06-01
Thanks to all of your for your replies.

In reading them all I have decided to reload the 64-bit version of 10.04 and considering Flash, am pretty certain I will stick with the 32-bit version in the wrapper until Flash 11 is released.

Ampers

---

### Post by cascade9 on 2010-06-01
> **dcstar said:**
> Somebody must have a large bullet hole in the foot by now over this......  :(

I'd like to hope so, but I doubt it.... 

> **AmpersUK said:**
> Thanks to all of your for your replies.

In reading them all I have decided to reload the 64-bit version of 10.04 and considering Flash, am pretty certain I will stick with the 32-bit version in the wrapper until Flash 11 is released.

Ampers

Your choice, but I've found that the 64bit (non-wrappered) version is more stable and works a lot better in general.

---

### Post by pricetech on 2010-06-01
Flash is the only thing that I even might use that I don't have with my 64 bit Lucid.  I haven't had a need for it yet, but who knows, maybe some day I will.

---

### Post by AmpersUK on 2010-06-01
Thanks, I had read that else where. But also read that if I use it it won't update. But then, if I keep it until version 11 comes out, I can always delete it and reload 11.

So perhaps I might do that.

Thanks

---

### Post by cascade9 on 2010-06-01
> **AmpersUK said:**
> Thanks, I had read that else where. But also read that if I use it it won't update. But then, if I keep it until version 11 comes out, I can always delete it and reload 11.

So perhaps I might do that.

Thanks

That is what I would do ;)

---

### Post by AmpersUK on 2010-06-01
> **cascade9 said:**
> That is what I would do ;)

Done, and working. I Googled something like "How do I install Adobe alpha flash for Ubuntu?" and found a website with full instructions (I am lost usually with tar files) and all is running well.

Ampers

---

### Post by Irony on 2010-06-01
> **AmpersUK said:**
> In reading them all I have decided to reload the 64-bit version of 10.04 and considering Flash, am pretty certain I will stick with the 32-bit version in the wrapper until Flash 11 is released
I'm using 64 bit Lucid on my desktop and it is working fine.

Testing 64 bit flash in the live CD/usb is very simple. Boot up your live CD/usb fire up firefox and go to;

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Download the tar.gz file (its an alpha release) then right click on it and extract it. Then go to your ~/.mozilla/plugins folder (make a plugins folder because one won't exist in the live CD/usb).

Drag the extracted flash (which is called libflashplayer.so) into the ~/.mozilla/plugins folder and restart firefox.

Go to youtube and see if flash is working - make sure you turn up your sound as by default Lucid has it muted in the live CD/usb.

Assuming it works then install Lucid and use the same method to install flash.

---

### Post by VastOne on 2010-06-01
> **cascade9 said:**
> I'd like to hope so, but I doubt it.... 



Your choice, but I've found that the 64bit (non-wrappered) version is more stable and works a lot better in general.

+1 and I totally agree....All I have ever used is 64 bit and once the Alpha Flash came out, all issues have died.

---

### Post by lavinog on 2010-06-01
> **AmpersUK said:**
> Thanks, I had read that else where. But also read that if I use it it won't update. But then, if I keep it until version 11 comes out, I can always delete it and reload 11.

So perhaps I might do that.

Thanks

I recall reading that 64bit flash will come out of alpha testing after 10.1 is released.

---

