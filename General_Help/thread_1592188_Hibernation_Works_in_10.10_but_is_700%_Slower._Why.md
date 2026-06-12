---
title: "Hibernation Works in 10.10 *but* is 700% Slower. Why, How??"
date: 2010-10-10
forum: General Help
---

### Post by vbgunz on 2010-10-10
Hibernation works. It does. Using the Lucid kernels, I hibernated in 15 seconds with plenty of applications running. The latest Maverick mainline kernel (2.6.36-rc7), I can hibernate in 15 seconds. The current Maverick kernel (2.6.35-22) is 1:45 seconds.

Wth happened?

From being told "hibernation works, be happy" and "report a bug" the help that I've gotten so far about this sucks. Hibernation is critically important to me and why should I report a bug with the only evidence being "it's slow for me, not for you". It's not empirical. I don't want to cry bug. I'll go a couple weeks uploading files, the status will go from low to duplicate and by the time the answer is here it's in the form of Natty Narwhal.

I already see this coming.

I don't mean to be shrewd or mean about it, nothing is owed to me, I love this distro *but* I am stuck between a rock and a hard place and I already been over this months before at #ubuntu+1. I was told to basically go away and shew or report a bug. Really? It's obviously only my problem and without some rock solid evidence and troubleshooting skills reporting a bug is almost like breaking out of prison using a plastic spoon.

At least that's how I feel about it.

**TL:DR**
Heres the kicker. I can't really fallback to the Lucid kernels as they do not support TRIM for my SSD. I can't really use the 2.6.36+ Maverick RCs because I always seem to deadlock and freeze up. I can in no way turn the verbosity up. The only verbosity I get when suspending is an extrememly informative blinking underscore. That's it :( It's like a horse doing the kicking. As long as it's kicking I know it's doing the math :/

How do I turn the verbosity up? Extremely high? As least get a bold blinking underscore? Red would be nice? All jokes aside, how do I figure out why in the world my hibernation is 2.6.35 is 700% slower than anything before or after? Resuming is the same across all kernels. I'm back up in 15 seconds flat.

---

### Post by vbgunz on 2010-10-11
bump!

Fun Fact: In just 2 hours after posting the original topic above, this help request ended up on page 5.

---

### Post by vek on 2010-10-11
I think I might be getting the same issue - when I tell it to hibernate, it goes to the usual flashing underscore, turns off the secondary monitor, etc... 

But I haven't actually considered waiting for 1:30 or longer to tell if its working or not.  I figured it was locked up.  Either way, something is broken, its clearly not intentional to take 100-200 times longer (I also have an SSD, so perhaps thats a commonality here?  Due to the SSD being used for the hibernate storage, it was usually just a second or two to hibernate).

**Edit: I just tried just waiting and it eventually successfully shut down to hibernate!  But it took like 4 minutes.** This is a very fast machine with a very fast HDD, it used to take a handful of seconds, now it takes minutes?  This is much more than 700% slower.

---

### Post by vbgunz on 2010-10-11
Hey Vek, if you didn't uninstall your older Lucid kernel (in case you did an upgrade), can you try hibernating with that kernel?

---

### Post by cyberkilla on 2010-10-14
My Sony Vaio VGN-AR41E does a similar thing...

Hibernating worked in Karmic. It stopped working after I upgraded to Maverick. I get a flashing cursor on black screen, with no HDD activity.

I've never waited long enough to see if it would finally hibernate. After a minute or two of doing nothing, I just force emergency unmount and power off.

:facepalm:

---

### Post by aspz on 2010-10-15
I have the same problem with the blinking underscore after upgrading from 10.04 to 10.10 only it isn't just slow, hibernation never completes at all. I wouldn't mind if it just took a few minutes as I could just leave the PC sitting there and go home.

I also have an SSD (OCZ Vertex 2 60GB). Could be a clue there.

---

### Post by vbgunz on 2010-10-15
I've narrowed my issue down to the current kernel. The Lucid kernels and the latest vanilla 2.6.36-rc kernels hibernate in 15 seconds for me. The current kernel is up pass 700% slower to hibernate.

No matter what kernel I use though, I always have the blinking underscore when going into hibernation. The current and all future rc kernels as of this posting are nicely verbose when resuming.

I would really rather not fall back to using an older kernel from Lucid without TRIM *but* at the same time, even if I did, the older kernels give me a problem with my virtual terminals. Something about the framebuffer is going crazy on me :(

---

### Post by vek on 2010-10-15
I just verified that its the kernel change, too... 2.6.32-25 hibernates in about 5 seconds, but the latest takes about 4 minutes.

Perhaps the commonality here is the SSD?  If you're affected by this (and I mean a VERY SLOW hibernate, not a non-working hibernate, thats more likely to be a different issue), do you have a SSD?  

The latest kernel stuff added support for discard/TRIM stuff, so its a bit of a clue.  IF you do have a SSD, is the swap on it?

---

### Post by vbgunz on 2010-10-16
I have an OCZ Vertex 2. Performance is excellent. I made the leap to SSD for one thing and that was hibernation. So when this went down I noticed right away. I dual boot for stuff that cannot be solved in Virtualbox so hibernating and resuming quicker than a normal shutdown/startup is always important to me.

Here's my hdparm -I /dev/disk

```

ATA device, with non-removable media
        Model Number:       OCZ-VERTEX2                             
        Firmware Revision:  1.11    
        Transport:          Serial
Standards:
        Used: unknown (minor revision code 0x0028) 
        Supported: 8 7 6 5 
        Likely used: 8
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  117231408
        LBA48  user addressable sectors:  117231408
        Logical  Sector size:                   512 bytes
        Physical Sector size:                   512 bytes
        Logical Sector-0 offset:                  0 bytes
        device size with M = 1024*1024:       57241 MBytes
        device size with M = 1000*1000:       60022 MBytes (60 GB)
        cache/buffer size  = unknown
        Nominal Media Rotation Rate: Solid State Device
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 1
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
                Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    WRITE_{DMA|MULTIPLE}_FUA_EXT
           *    64-bit World wide name
           *    IDLE_IMMEDIATE with UNLOAD
           *    WRITE_UNCORRECTABLE_EXT command
           *    Segmented DOWNLOAD_MICROCODE
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Host-initiated interface power management
           *    Phy event counters
                DMA Setup Auto-Activate optimization
                Device-initiated interface power management
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT LBA Segment Access (AC2)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
           *    Data Set Management TRIM supported (limit 1 block)
           *    Deterministic read data after TRIM
Security: 
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
Logical Unit WWN Device Identifier: 5e83a97f1ed3cc16
        NAA             : 5
        IEEE OUI        : e83a97
        Unique ID       : f1ed3cc16
Checksum: correct

```

---

### Post by vbgunz on 2010-10-16
My swap is the first partition on the SSD. It's at 12GB.

---

### Post by vek on 2010-10-17
I just moved my swap to a non-SSD secondary drive and it seems faster now (about 15 seconds instead of 3 minutes...)

(ignoring the ~4 hours it took to get hibernation to actually work after installing the new motherboard).

Could also be something to do with new motherboard, of course...

---

### Post by ehartmann on 2010-10-17
I experience the same troubles with UL30VT and a SSD drive.

The SSD seems to be the source of the trouble. I've tried with latest kernel from kernel ppa and hibernation take almost the same time (3-4 minutes).

---

### Post by cyberkilla on 2010-10-17
I suspect that my issue differs from the one you're all having.

My laptop has a normal HDD, and the damned thing doesn't hibernate at all. It used to, until Maverick. Funnily enough, suspend works now, so it's just hibernate that fails utterly for me.

---

### Post by Lynx Phoenix on 2010-10-17
um guys i think i might have a way for you to hibernate properly

i've been trying to find a way to hibernate from the console for the last couple of days so i can do a one-time scheduled hibernate

from what i've seen on other threads and personal experience trying different methods, i found that using hibernate.sh for example makes a lot of people (including me) end up with a failed hibernate - it starts but ends with a blinking cursor and no activity. didnt wait for minutes cause i thought it just stopped.

hibernating from the gui works properly for me though and hibernating by using ```
sudo pm-hibernate
``` also works just fine

if indeed you are trying to hibernate through the gui and having these long delays and failed hibernates, then maybe you should try what *didnt* work for me as it might change behaviour from system to system, which is this: 

```
sudo /etc/acpi/hibernate.sh
```here's a link to a thread that might relate to this solution (i found it to copy the exact command, but i didnt actually read it through): [http://ubuntuforums.org/showthread.php?t=203398](http://ubuntuforums.org/showthread.php?t=203398)

hope it helps

edit - here's another i had open in a tab [http://ubuntuforums.org/showthread.php?t=813387&highlight=halt+hibernate](http://ubuntuforums.org/showthread.php?t=813387&highlight=halt+hibernate)

edit 2 - fixed the second code block, just noticed it was ****ed up

---

### Post by SeanBlader on 2010-10-17
I don't understand hibernate anymore. It used to be that you'd hibernate when you were going away from power for a long period but didn't want to wait for the tedium of restarting. Well now starting up takes under 30 seconds from power to Google, faster if you have a decent bios. If I expect to be away from power for less than 2 hours, I'll just suspend to ram, and then my system is back up in about 10 seconds. Obviously this won't work if you have no battery at all on your laptop, but if that's the case you probably have bigger problems than your hibernate, and should probably be powering off anyway.

So instead of hibernating, why not set the session to remember what you were doing at logout and restart all those apps at boot? It would be faster than a 3 minute hibernate, and it would probably take something like 60 seconds to get all your apps back running from SSD.

Anyway, sorry you all are having problems, but my attempt at a helpful suggestion is to try suspending? And if that doesn't help, here's a friendly bump to the top of the forum.

---

### Post by ehartmann on 2010-10-17
Thanks for the suggestion.

I've tried with sudo /etc/acpi/hibernate.sh. But it did not work either.

The advantage of hibernate is to keep the status of running applications. It works well with Karmic but not with Merkaat for an unknown reason.

I've profiled the hibernate script, and it seems that the scripts run quickly, it's the serialization to swap file that seems to be really long.

I've tried uswsups, it quite fast but I cannot resume. With kernel mode, hibernate take more than 3 minutes but the resume take less than 15s.

---

### Post by vbgunz on 2010-10-17
> **SeanBlader said:**
> I don't understand hibernate anymore. It used to be that you'd hibernate when you were going away from power for a long period but didn't want to wait for the tedium of restarting. Well now starting up takes under 30 seconds from power to Google, faster if you have a decent bios. If I expect to be away from power for less than 2 hours, I'll just suspend to ram, and then my system is back up in about 10 seconds. Obviously this won't work if you have no battery at all on your laptop, but if that's the case you probably have bigger problems than your hibernate, and should probably be powering off anyway.

So instead of hibernating, why not set the session to remember what you were doing at logout and restart all those apps at boot? It would be faster than a 3 minute hibernate, and it would probably take something like 60 seconds to get all your apps back running from SSD.

Anyway, sorry you all are having problems, but my attempt at a helpful suggestion is to try suspending? And if that doesn't help, here's a friendly bump to the top of the forum.

I purchased the SSD disk for one purpose. To hibernate and resume at blazing speeds. To give you an example of how extreme the performance is with an SSD check this out. From a clean power on to Grub takes 20 seconds and from Grub to the login screen is another 20 seconds. Doing a clean shutdown takes about 15 seconds.

The Lucid and latest Maverick RC kernels take 15 seconds to hibernate beating a clean shutdown. After hibernating, resuming takes 15 seconds just outright killing a clean start up. The benefits of hibernation far outweigh rebooting. There is just no session setup that can get me back at the exact same state like hibernation.

Hibernation still works albeit it's greater than 700% in wait time for shutdown. Resuming is still quick as hell killing a clean startup. If you don't have an SSD that can do this you might not see hibernation as I do. Thanks for the bump :)

---

### Post by vbgunz on 2010-10-17
> **ehartmann said:**
> Thanks for the suggestion.

I've tried with sudo /etc/acpi/hibernate.sh. But it did not work either.

The advantage of hibernate is to keep the status of running applications. It works well with Karmic but not with Merkaat for an unknown reason.

I've profiled the hibernate script, and it seems that the scripts run quickly, it's the serialization to swap file that seems to be really long.

I've tried uswsups, it quite fast but I cannot resume. With kernel mode, hibernate take more than 3 minutes but the resume take less than 15s.

I too tried uswsusp and though hibernation takes about 40 seconds for me, it never resumes. To be honest, I don't want to bother with it as the latest Maverick and earlier Lucid kernels hibernate and resume at the 15 second mark. Something is just wrong with the current kernel :(

---

### Post by ehartmann on 2010-10-17
I've compiled the kernel from the git tree of Ubuntu maverick.
And everything works fine with vanilla options ! :D

I will try with the default Ubuntu options, perhaps it's only a configuration.

---

### Post by cyberkilla on 2010-10-17
> **SeanBlader said:**
> I don't understand hibernate anymore. It used to be that you'd hibernate when you were going away from power for a long period but didn't want to wait for the tedium of restarting. Well now starting up takes under 30 seconds from power to Google, faster if you have a decent bios. If I expect to be away from power for less than 2 hours, I'll just suspend to ram, and then my system is back up in about 10 seconds. Obviously this won't work if you have no battery at all on your laptop, but if that's the case you probably have bigger problems than your hibernate, and should probably be powering off anyway.

So instead of hibernating, why not set the session to remember what you were doing at logout and restart all those apps at boot? It would be faster than a 3 minute hibernate, and it would probably take something like 60 seconds to get all your apps back running from SSD.

Anyway, sorry you all are having problems, but my attempt at a helpful suggestion is to try suspending? And if that doesn't help, here's a friendly bump to the top of the forum.

I would have agreed with you, but my Vaio's battery is so dead, it isn't even recognised any more, and I can't justify blowing >£100 on a battery for a laptop I use as a desktop :P

It would just be nice to be able to save state without having the power on all night. I had that *luxury* feature in Karmic (and a most releases before it), but it's regressed :mad:

EDIT:

I have been trying to hibernate in Maverick for ages, and each time it would hang with a flashing cursor...

Then, I did this:
- Log out of GNOME Desktop (just log out, back to GDM login screen).
- Switch to TTY, run "sudo pm-hibernate".

The system then hibernated successfully, and what's more, it now works through GNOME too. I don't know why that would be the case, but there you have it.

Might be obvious to everyone else, or complete BS, but I thought I'd share.

---

### Post by vexorian on 2010-10-18
How do you install the 2.6.36-rc7 kernel ? It seems I have the exact issue as the OP.

---

### Post by vbgunz on 2010-10-18
You can go here and get the latest vanilla ubuntu kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/). Keep in mind these kernels do not have the ubuntu patches, RC releases may be unstable and all kernels from mainline (I believe) are officially unsupported.

Now that that's out the way, the latest RC is 8 here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/) There doesn't appear to be any i386 packages there but RC 7 has them if you're not on 64 here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc7-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc7-maverick/)

You need to download 2 debian packages particular to your architecture and the *all* package. That's 3 debian packages you need to download.  Download them to an empty directory. cd into that directory using the command line and when there in that directory, say

```
sudo dpkg -i *.deb
```

Just make sure, the only debs you want installed are in that directory. Else, that command installs every deb found in that directory. You might have luck with the latest kernels but for me personally, I always freeze and lock up after a day or two using them. I am still stuck on the current 2.6.35. Good luck!

---

### Post by vexorian on 2010-10-18
Thanks. It worked. I will keep this session open for days and we will see if the hang up issue happens to me.

Incidentally, I still get a blinking cursor before hibernation but only for a second. I actually think it was that way back when I used 9.04.

---

### Post by anixon on 2010-10-22
This hibernation issue was horrible. It's to do with the kernel i think. Wasn't like this in 10.04. I found a solution sorta like above. Instead of using a backdated kernel you can easily without any work install a slightly newer one. Add ppa:kernel-ppa/pre-proposed to your sources and refresh. Then select the 'linux' package which is 2.6.35-23-generic. The issue is solved for me with this kernel.

---

### Post by vbgunz on 2010-10-22
> **anixon said:**
> This hibernation issue was horrible. It's to do with the kernel i think. Wasn't like this in 10.04. I found a solution sorta like above. Instead of using a backdated kernel you can easily without any work install a slightly newer one. Add ppa:kernel-ppa/pre-proposed to your sources and refresh. Then select the 'linux' package which is 2.6.35-23-generic. The issue is solved for me with this kernel.

Did you ever experience the extreme slowdown of greater than 700% or did hibernation never work for you at all? Hibernation on an SSD with the kernels that are blazing hibernate in the 15 second range. Is it this quick for you or more along the 1 minute range? Do these pre-proposed packages have the ubuntu patches?

---

### Post by anixon on 2010-10-23
> **vbgunz said:**
> Did you ever experience the extreme slowdown of greater than 700% or did hibernation never work for you at all? Hibernation on an SSD with the kernels that are blazing hibernate in the 15 second range. Is it this quick for you or more along the 1 minute range? Do these pre-proposed packages have the ubuntu patches?

Yeah in 10.04 hibernation was 15-20 seconds on my ssd. Then as soon as I went to 10.10 (fresh install), it would take FOREVER 3-4min. It would go to blank screen with cursor for like a min and a half. And then it would flicker and i thought it might be done but just back to the cursor for 2-3 min then shut off. Resume seemed way slower too. But not as bad as the hibernate.

I tried to fix it with uswsusp package (alternate hibernate package) and it seemed to fix it. But I found that uswsusp was unreliable for me and would hang on sleep often.

Anyways, so I found in a bug list that someone tried the 2.6.35-23 and it worked. Installed from the PPA and it worked for me. Everything in ubuntu still worked. Updates still work. Only had to reinstall virtual box for the new kernal but no problems since changing kernel.

Yah hibernation is back to same speed as 10.04.

---

### Post by vbgunz on 2010-10-23
I went ahead and dived into it yesterday and hibernation is back at the 15 second mark. I had a problem with the RC kernels of 2.6.36 as they would always cause me to freeze and lock up. They were basically vanilla without any patches and I feel one of those patches was meant for me.

Anyhow, everything seems fine and I am gonna leave it until I experience a freeze or lockup. If none experienced, I won't report back. Thanks anixon, so far so good!

---

### Post by anixon on 2010-10-26
Problem just came back for me on the newer kernel. I guess it's not 100%. vbgunz have you had any issues since?

---

### Post by vbgunz on 2010-10-28
Hey anixon, I was up for 4 days and every day I was able to hibernate at least twice (three times) without a problem. Using 2.6.35-23-generic I have not yet run into a lockup or slow hibernation. It's running great. What do you mean, it happening again? It just happened out of nowhere or did you upgrade at some point?

---

### Post by 5oak on 2010-10-28
> **anixon said:**
> This hibernation issue was horrible. It's to do with the kernel i think. Wasn't like this in 10.04. I found a solution sorta like above. Instead of using a backdated kernel you can easily without any work install a slightly newer one. Add ppa:kernel-ppa/pre-proposed to your sources and refresh. Then select the 'linux' package which is 2.6.35-23-generic. The issue is solved for me with this kernel.

It seems this did the trick, thnx!:)

---

### Post by anixon on 2010-10-28
> **vbgunz said:**
> Hey anixon, I was up for 4 days and every day I was able to hibernate at least twice (three times) without a problem. Using 2.6.35-23-generic I have not yet run into a lockup or slow hibernation. It's running great. What do you mean, it happening again? It just happened out of nowhere or did you upgrade at some point?

Yeah, it's pretty much out of nowhere. It seems kinda hit or miss for me. When I try to test it by booting up and opening some windows and hibernating. It hibernates in 20-25 seconds. But I've had a few times over the last week where I've been working for a long time and had maybe 3-5 programs open and hibernated and it's been about 1.5-2.5 min which is SUUUPER lONG. The new 2.6.35-23-generic is definitely an improvement over the stock 10.10 kernel but it's still frustrating me a bit. I'm sooo close to just picking up one of the new macbook air's because Linux is so frustrating with their "almost" good enough hardware support. My docking station doesn't work fully either. :(

---

### Post by jrussell88 on 2010-11-12
I'm running 64-bit 10.10 and whilst hibernate appears to work, resume doesn't. /var/log/pm-suspend.log ends:
> /usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Sat Nov 13 11:13:08 ICT 2010: performing hibernate

When I restart, I'm back to a fresh login. I tried cyberkilla's suggestion, but it didn't work for me.

> I have been trying to hibernate in Maverick for ages, and each time it would hang with a flashing cursor...

Then, I did this:
- Log out of GNOME Desktop (just log out, back to GDM login screen).
- Switch to TTY, run "sudo pm-hibernate".

The system then hibernated successfully, and what's more, it now works through GNOME too. I don't know why that would be the case, but there you have it.

Might be obvious to everyone else, or complete BS, but I thought I'd share.

---

### Post by kennethadammiller on 2010-12-09
I think this issue should be escalated to the developers of the kernel. They should know about this; hibernate used to be fast, but now it sucks. I don't want a work around or a stupid solution, I want hibernate to actually work.

I would like to confirm to you guys that I don't think that this is just an SSD problem either, because I'm using a SATA II hard drive will really nice read/write speeds of up to 80mb/s, and it's just like what you are saying; the differences in time required to hibernate and resume are exorbitant. Like 700% is actually accurate, and this is not an exaggeration.

I'm using an Acer 5740 for the info by the way.

---

### Post by aperomsik on 2010-12-09
The 2.6.35-23 kernel recently pushed to -updates helped significantly -- but hibernate still hangs now and then on my Inspiron 1545, and resume is still too slow. Never had any trouble with hibernate in Lucid. Well, resume was too slow there too, but not as bad as it is now.

---

### Post by vbgunz on 2010-12-09
To be honest, I didn't start this thread in the hopes that it'll become the catch-all thread to all hibernation issues. I opened this thread with a very specific hibernation issue and that issue is "hibernation is 700% slower".

I didn't pull the 700% out of thin air or the brown hole. I got 700% from the fact that hibernation went from 15 seconds-everytime to 15x7 and greater everytime. This also isn't the issue of "well, it's always been 15x7 slow for me, shouldn't it be faster?".

I find the best kernel that works for me, putting me back at the 15 second mark is 2.6.35-23-generic. This kernel pretty much covers my trimming needs and is the latest stable that works for me best. There is a new kernel out 2.6.35-2**4**-generic which for me is disastrous but that's a whole other thread.

---

