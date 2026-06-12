---
title: "512Meg Enough Memory for 9.04?"
date: 2009-10-02
forum: General Help
---

### Post by SleeperMan2000 on 2009-10-02
I have installed Ubuntu 8.10 from a CD and did the online upgrade.  I have all the most recent updates.

I have a Dell Optiplex g150 with 512Meg of RAM.   

With only Firefox 3.5 (I upgraded that as well) and a terminal window, I seem to have very little headroom left in free memory.

[FONT=Courier New]                           total       used       free     shared    buffers     cached
Mem:        508476     500560       7916          0      21524     123468
-/+ buffers/cache:     355568     152908
Swap:      1502036     232396    1269640[/FONT]

System isn't very snappy.  System monitor says firefox is using 212MB.  I guess the rest is the for gnome?   

Youtube videos don't play hardly at all.   I tried to disable IPv6, upgrade Firefox, upgrading to flash 10, but still slow on the video.  Due to the memory?

I can put 1gig of memory in this computer if necessary, but I was hoping Ubuntu didn't need that much.   Another machine has XP on 512 meg, and it seems faster when browsing the web and it plays Youtube videos ok.  This makes me think there must be something I can do to get better performance out of Ubuntu with 512 meg.

Thanks in advance for any suggestions.

---

### Post by jward3010 on 2009-10-02
Ignore the lack of memory from "free" command. Linux kernel's buffer unused memory for quick access, so not unusual. 512MB is fine for Ubuntu, obviously the more the better and maybe 1GB is now preferred (minimum is 256MB anyway). 

Slowness can be related to your hardware.

Go to a terminal and paste the output of:
```
sudo lspci
```
Paste it into code tags (looks like {code}information{/code} - except they're square brackets. That will show us what hardware you have.

---

### Post by mike555 on 2009-10-02
getting more memory is always good ...... find out how much your mother board supports ..... 2 gb is probably good .........

---

### Post by credobyte on 2009-10-02
Haven't had any problems so far ( 512Mb RAM ) - even KDE with Compiz runs just fine :)

---

### Post by scouser73 on 2009-10-02
Here is the fact sheet for [[COLOR="Red"]**Ubuntu's Minimum Requirements**[/COLOR]]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by snowpine on 2009-10-02
512mb is plenty for Ubuntu. The laggy video probably has nothing to do with ram, and everything to do with your old, slow processor (pentium 3 I believe?).

On my Pentium 3 computers, I download the Flash video to my hard drive first, and then watch it from there. This is much smoother than streaming from the web, give it a try!

---

### Post by SleeperMan2000 on 2009-10-02
Thanks for all the quick replies.

Yes, I think this is a Pentium 3.  

I'm trying to find a way to put a new lease on life for machines gathering dust in the closet.  There are so many!   I would say Ubuntu 9.04 is successful at making this circa Year 2000 hardware a nice internet appliance for browsing the web and emailing, but not for multimedia.  Overall, I am very impressed.

Here is the output:

```

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)
02:07.0 Communication controller: ESS Technology ES2898 Modem (rev 03)
02:09.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
02:0a.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)


```

---

### Post by wojox on 2009-10-02
I see you have a nvidia card. Have you activated the driver? System > Administration > Hardware Drivers. You probablly just need a little tweaking. Check this out for Firefox:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by snowpine on 2009-10-02
Ubuntu is kind of full-featured for older hardware. I personally am running Crunchbang (a lightweight Ubuntu "remix") and SliTaz (a really tiny distro, about 30mb!) on my old pentium 3's.

---

### Post by credobyte on 2009-10-02
> **snowpine said:**
> Ubuntu is kind of full-featured for older hardware. I personally am running Crunchbang (a lightweight Ubuntu "remix") and SliTaz (a really tiny distro, about 30mb!) on my old pentium 3's.

In that case, what is "Ubuntu" ? I mean, most of people associate it with Ubuntu ( Gnome ), not Ubuntu minimal + custom applications on various DE's. If we are talking about Crunchbang, Xubuntu, Lubuntu, etc., we should refer to Linux, not Ubuntu by itself ( which is, more or less, just a repository ).

---

### Post by ApEkV2 on 2009-10-02
512 is enough for 32-bit Ubuntu, but not for 64-bit.
And don't forget about Mint with the Fluxbox window manager. 
That only uses about 200mb and is based off of Ubuntu.

---

### Post by jward3010 on 2009-10-02
> **ApEkV2 said:**
> 512 is enough for 32-bit Ubuntu, but not for 64-bit.
And don't forget about Mint with the Fluxbox window manager. 
That only uses about 200mb and is based off of Ubuntu.
There's no real difference dude, except the size of the sums it can do!

---

### Post by cantab on 2009-10-02
512MB RAM works fine for me, running the Gnome Desktop.

I have dual PIII 866 MHz, and Youtube videos are a bit marginal - usually fine, but sometimes they stutter, and if I load another webpage in another tab the video stops playing. I've found some other flash video sites perform very badly.

---

### Post by snowpine on 2009-10-02
> **credobyte said:**
> In that case, what is "Ubuntu" ? I mean, most of people associate it with Ubuntu ( Gnome ), not Ubuntu minimal + custom applications on various DE's. If we are talking about Crunchbang, Xubuntu, Lubuntu, etc., we should refer to Linux, not Ubuntu by itself ( which is, more or less, just a repository ).

The original post mentioned that the OP installed using the Ubuntu 8.10 CD. Presumably that means the default Gnome install (but Sleeperman, please correct me if I'm wrong). 

Kubuntu=Ubuntu+KDE, Xubuntu=Ubuntu+Xfce, etc. Doesn't matter which desktop environment you use, it is still Ubuntu, just like Debian+KDE is still Debian. It is the same distribution at its core (same repository, same command line, etc).

I refer to Crunchbang as a "remix" because it is not an official Canonical product. Hope that clears up my terminology. :)

---

### Post by blur xc on 2009-10-02
> **snowpine said:**
>  I refer to Crunchbang as a "remix" because it is not an official Canonical product. Hope that clears up my terminology. :)

I've been using #! in vbox on my xp machine just to try it out, and I have to say it's an impressive product.  It runs wonderfully fast, though it's a bit rough around the edges out of the box.  I definitely need to learn a bit more about how to configure the GUI...

Anyway- why not just get more ram?  Ram for those older machines is wicked cheap...

FWIW, my heavy 9.04 install w/ AWN and all my compiz whiz bang goodness uses about 300mb of ram on a fresh boot after logging in (one user logged in).  With it running, with both my wife and I logged in w/ a few apps open (FF being the one of the worst) we use about 1 - 1.5 gigs of ram.  Firing up Vista in VBox sets us up to almost the 3gb limit.

I think I should have gone w/ more ram an 64bit ubuntu...  I probably will sometime in the future...

BM

---

### Post by SouthOfHell on 2009-10-02
Its' 2009..... get some more ram christ sake...

---

### Post by jward3010 on 2009-10-02
Yep, it's as cheap as air almost. Even decent DDR2. Although if it is older DDR or even SD-RAM you're looking for, interestingly enough I don't think it will be cheaper - because nowadays it's demand is lower than DDR2, they charge a bit more for it than you'd expect, although it's still fairly cheap and depends where yar livin'.

---

### Post by credobyte on 2009-10-02
> **SouthOfHell said:**
> Its' 2009..... get some more ram christ sake...

Yeah, right .. 1GB DIMM costs around $50 #-o

---

### Post by Bush_Roo on 2009-10-02
Ha ha! I have a GX150. A P3 with 1gig CPU running with 384 megs of RAM. (I'm not using it, but I like to run those old machines with a late OS--only works well with Ubuntu/Linux systems I have noticed...) More RAM won't help the SPEED issues. Yes, those flash movies are going to be a bit BAD, but I have had reasonable performance when I make sure that no FREE flash players are installed (removed them all together) and then installed the proprietary flash player. I got quite good performance with 256 megs of RAM on a P3. More RAM won't improve speed, in fact, I'm note sure that you could stick more RAM in a GX150... they are a little old...

You can use a P3 to play those movies though!

It might be a setup problem with regards to flash. It could be using the free flash player instead of the proprietary one. (These are just thoughts.)

By the way, setting up an old 3D video card won't allow faster movie playback............ it's a good idea for 3D games though...... old ones....

---

