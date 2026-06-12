---
title: "Is the i3, i5 or i7 intel processors supported by Ubunut"
date: 2010-01-31
forum: General Help
---

### Post by timZZ on 2010-01-31
Hi,

I am looking at getting a new laptop.

I am thinking Dell.  Either Latitude (Which is my main goto) or the inspirion.

The latitudes run off the Intel Core 2 Duo, where as the inspirions seem to run off i3s or i5s.

I am curious if ubuntu supports this new architecture.?

---

### Post by t4thfavor on 2010-01-31
If they will run windows, they will run ubuntu. They are just a small upgrade in architecture from the core 2 line, so be confident that they will work just fine. 

The same is not true in reverse though :)

---

### Post by ad_267 on 2010-01-31
Yep, I've got an i5 750 in my PC. Apparently Turbo-boost doesn't work with the current Linux kernel but this has been fixed in 2.6.33. See [http://phoronix.com/forums/showthread.php?t=19260&page=6](http://phoronix.com/forums/showthread.php?t=19260&page=6)

---

### Post by kaibob on 2010-01-31
Some of the new i3 chips have built-in video. The new Dell Inspiron 580 desktops are an example:

[http://www.dell.com/us/en/home/desktops/inspiron-580/pd.aspx?refid=inspiron-580&s=dhs&cs=19&~ck=mn](http://www.dell.com/us/en/home/desktops/inspiron-580/pd.aspx?refid=inspiron-580&s=dhs&cs=19&~ck=mn)

I don't know but I would wonder whether the new video is supported by Ubuntu.

---

### Post by 3rdalbum on 2010-01-31
> **kaibob said:**
> Some of the new i3 chips have built-in video. The new Dell Inspiron 580 desktops are an example:

[http://www.dell.com/us/en/home/desktops/inspiron-580/pd.aspx?refid=inspiron-580&s=dhs&cs=19&~ck=mn](http://www.dell.com/us/en/home/desktops/inspiron-580/pd.aspx?refid=inspiron-580&s=dhs&cs=19&~ck=mn)

I don't know but I would wonder whether the new video is supported by Ubuntu.

The built-in graphics in the i3 are not very stable on Ubuntu. They can be driven by the Intel driver in Ubuntu 9.10, but even the latest Intel driver has crashing issues.

Even without this problem, I'd recommend getting an i5. The i3 doesn't seem to be as fast-per-clock as the Core 2.

---

### Post by falconindy on 2010-01-31
> **t4thfavor said:**
> If they will run windows, they will run ubuntu. They are just a small upgrade in architecture from the core 2 line, so be confident that they will work just fine. 

The same is not true in reverse though :)
Whoa, easy there. The Nehalem architecture is vastly different from the previous C2D style, particularly when it comes to the i7. The FSB is replaced by the QPI, the north bridge is gone and many of its former components moved to the core. All the cores are now physically on the same die as well -- no more combining multiple dies and tying them together. Hyperthreading is back (on the i7).

Not even close to the same beast. That said, the kernel supports 95% of the new functionality already. Intel graphics have been a mess lately, and at the rate things are going, I suspect they won't be stable until 2.6.34.

---

### Post by t4thfavor on 2010-02-01
My point was that to the normal user, you will not notice anything except a modest performance bump over a similarily priced C2Quad. I know there are lots of changes and I notice quite alot of performance increase, most will not due to the general lack of apps to utilize 8 physical threads (as opposed to 2 or 4)

---

### Post by falconindy on 2010-02-01
The OP's question was about support, not performance. It's valid to consider the architectural changes being (un)supported by the kernel.

---

### Post by timZZ on 2010-02-02
Thank you ... 

Yes my question was about support not performance.

Although I look forward to the performance.

I needed to know that my i3/5/7 based processor would be stable enough to develop on.

(I would hate to be stuck on windows until then)

I am patient I will just wait.

---

### Post by Matheo84 on 2010-02-07
I'm having problems with my Inspiron 1464 with Intel Core i3-330M Processor built-in video. The installer shows nothing in the monitor but runs Ok because I've heard the init sound; so now I'm afraid that the 9.10 kernel has issues with it.

Seems that should wait for Lucid and hoping that this issue be addressed on that version? :-|

---

### Post by Abhisheietk on 2010-02-09
I am also facing the same problem. help someone!!

---

### Post by bdamon on 2010-02-21
> **Matheo84 said:**
> I'm having problems with my Inspiron 1464 with Intel Core i3-330M Processor built-in video. The installer shows nothing in the monitor but runs Ok because I've heard the init sound

I see the same thing with a Inspiron 1464 with a i5 Processor.

---

### Post by manishmahabir on 2010-02-24
same no video problem here too on dell 1464 with i5 processor.
the new graphics is officially supported by intel 2.6.33 onwards.
Turbo mode is back for Linux as of the 2.6.33-rc5 kernel.
Unfortunately the next Ubuntu version is going to be using 2.6.32.

---

### Post by lex25288 on 2010-02-26
[SIZE=2]Well let's just say that they are not on-install supported, but with a bit of work-around I managed to make my Core i3 540 (Clarkdale 3,06 Ghz) run smoothly. If anyone were interested I could post a step-by-step guide, just say the word!
Cheers:popcorn:
[/SIZE]

---

### Post by lex25288 on 2010-02-26
Well anyway here it goes.
I know this works on 9.10, 'cause this is the only release I have tested it on.
If you manage to get to end of the installation process do as follows:

[LIST=1]
[*]Log in Failsafe GNOME;
[*]Download [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb") (make sure you're running the 64 bit version of Ubuntu 9.10 before downloading this, if you are running the 32 bit version download this [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb")), as of writing this post kernel version 2.6.33-0206633 is the latest stable version available.
[*]Open terminal and redirect to the directory where the download was saved to.
[*]Upgrade your kernel:```
sudo dpkg -i --force-all linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb
```
[/LIST]
Cheers :popcorn:

---

### Post by ScottMartin on 2010-02-26
I have an I7 920 running Ubuntu 9.10/amd 64 (was 8.10) and it runs great.
It has been my daily workhorse for over a year now.

Regards,
Scott.

---

### Post by Barbalras on 2010-04-11
Hey! 

I'm having a similar issue but I can't even go through the installation process!

I've just bought a dell studio with an i3 processor. It had Windows 7 built in so the minute I turned it on I tried to install Ubuntu 9.10 64-bit version. I can get to the screen with the options "try ubuntu without install", "install ubuntu", etc. Clicking on any of these two gets me to a black screen and that's it. It seems like the installation process can continue but without any image on the screen. I tried to use the safe graphics mode but it didn't do any good.

Same thing happens with 32-bit version.

Any thoughts? Thanks in advance

---

### Post by mataug on 2010-04-15
Barbalas, do you get a screen with busybox written on it ?

---

### Post by Barbalras on 2010-04-15
hi!

No, it was just a black screen with nothing in it

Anyway, the solution I came up with was really pragmatic: I installed Lucid with no problem whatsoever

thanks!

---

### Post by linden940 on 2010-04-15
i have NOT used the i3 i5 i7 processors but A fix you could do if your video card is not working WELL or not at all.....just go out and GET a video card for your computer. *that's if its a desktop and not a laptop*

---

### Post by mataug on 2010-04-15
then what was your solution barbalras ?

I have an inspiron580 with corei5-650 & GT-220

was unable to get the gfx card to run on 8.04 & 9.10, so was left wondering if lucid had better support for it

---

### Post by Barbalras on 2010-04-15
ok, maybe I didn't make myself clear in the last post

Until yesterday, I was trying to install Ubuntu 9.10 but I could only get trought the first installation screen and then the it went black everytime. I do not know how to resolve this issue.

I just downloaded the 10.04 beta version and I had no problems with the installtion process. I am now a happy user of Lucid Lynx.

My video card is the generic one that comes with a Dell laptop when you don't pay for the nvidia or ati cards.

---

### Post by Orographic on 2010-05-09
How is Lucid now going with the Core i3 and Core i5? I was planning on getting one fairly soon. I will just run the onboard HD graphics as its all I need.

Someone told me recently that their Core i3's at work seem to run Lucid well.

---

### Post by kaibob on 2010-05-09
> **Orographic said:**
> How is Lucid now going with the Core i3 and Core i5? I was planning on getting one fairly soon. I will just run the onboard HD graphics as its all I need.

Someone told me recently that their Core i3's at work seem to run Lucid well.

There have been a few threads on this topic, and the new processors and the Intel HD Graphics seem to work well with Lucid. See, for example,

[http://ubuntuforums.org/showthread.php?t=1465764](http://ubuntuforums.org/showthread.php?t=1465764)

---

### Post by Barbalras on 2010-05-09
Lucid is working great with my i3 processor

---

### Post by Orographic on 2010-05-10
Thanks guys, looks like the Core i3 will be my next new machine then. :)

---

### Post by nuovodna on 2010-05-14
Hi, is it a good combination intel i3 330m + nvidia geforce 310M 512MB ??

Regards

---

### Post by damien-tt on 2010-07-28
> **nuovodna said:**
> Hi, is it a good combination intel i3 330m + nvidia geforce 310M 512MB ??

Regards

It should work with Lucid, let us know how it goes. :)

---

### Post by MockY on 2010-08-17
The built in graphic seems to still be unsupported. It's a shame because I would love to use Ubuntu as XBMC base instead of XP for this build. I have an Intel Core i3-540 Clarkdale 3.06GHz matched up with a ASRock H55M Pro and the Live disk simply wont boot and if I use the alternative installer, it fails to boot once the install completes. For the live CD, all I get is a black screen, and for the alternative install, it hangs on the following screen:

---

### Post by TBABill on 2010-08-17
It is still unsupported (Core i3 using on-chip graphics). Until kernel 2.6.33 onward we are out of luck with Ubuntu. My machine booted but had constant freezes and crashes. I tried Mint 9 (same Ubuntu base, but wanted to see if they had any tricks integrate), same result.
 
I am running PCLinuxOS on the i3 machine and it runs great because of the 2.6.33 kernel. I'll give 10.10 a shot once it's out, but for now my one laptop has to run another distro with a newer kernel. My other machine is on Mint 9 and runs great with older Intel graphics.

---

### Post by MockY on 2010-08-17
I updated the system to 2.6.33-02063305 but that still did not work. I then upgraded all the way to 2.6.35-020635rc1 and that did not work either. So I guess it is a lost cause. I figured since it's Intel that they would be on top of things and actually have Linux support for their products before they even release them....

---

### Post by elmero68 on 2010-08-30
I too have an Intel i3 530 and have not been able to install Ubuntu 9.10 or 10.4, not even with the alternative install. With the normal install I get a black screen, with the alternative I get a full install but then a bunch of disk errors and it freezes. The funny thing is that Fedora 13 works fine, just not Ubuntu. Anyone else have any ideas/fixes?

---

### Post by lpanebr on 2010-09-10
I am very interested in this: does ubuntu fail to install on i3 processors?

I need to decide between a Dell machine with:

1) Intel® Core™ i3-540 (3.06GHz, 4MB cache) or
2) Intel® Core™2 Quad QE8200S (2.33 GHz, 4M Cache, 1333 MHz FSB

Any comments will be greatly appreciated!

---

### Post by mirchichamu on 2010-09-10
> **lpanebr said:**
> I am very interested in this: does ubuntu fail to install on i3 processors?

I need to decide between a Dell machine with:

1) Intel® Core™ i3-540 (3.06GHz, 4MB cache) or
2) Intel® Core™2 Quad QE8200S (2.33 GHz, 4M Cache, 1333 MHz FSB

Any comments will be greatly appreciated!
I am also planning to buy i3 or i5 laptop. I am afraid of having problem with lucid installation? It will be a shock for me to not have Lucid or Linux?

Any suggestion of what to do?

---

### Post by IAmWhatWasDavidBowman on 2010-09-10
mirchichamu,

Yep. Buy one from System76. They're customized to work with Ubuntu. I bought a Pangolin Performance with an i7 (though they also offer laptops with an i3 or i5).

---

### Post by mirchichamu on 2010-09-11
> **IAmWhatWasDavidBowman said:**
> mirchichamu,

Yep. Buy one from System76. They're customized to work with Ubuntu. I bought a Pangolin Performance with an i7 (though they also offer laptops with an i3 or i5).

Thanks for your reply.
What is system 76?

---

### Post by cascade9 on 2010-09-11
> **lpanebr said:**
> I need to decide between a Dell machine with:

1) Intel® Core™ i3-540 (3.06GHz, 4MB cache) or
2) Intel® Core™2 Quad QE8200S (2.33 GHz, 4M Cache, 1333 MHz FSB

Any comments will be greatly appreciated!

i5-540M should be faster on single-threaded programs, but the Q8200S has more CPU power (thanks to more cache and 4 cores, the 540 is a dual-core CPU).

---

