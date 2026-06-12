---
title: "Kubuntu 10.04 crashes completely when watching you tube - only firefox, Konqueror ok"
date: 2011-03-03
forum: General Help
---

### Post by FunkyFrank on 2011-03-03
Hi all,

since last night I'm experiencing a weird problem. 
(Kubuntu 10.04, ASUS F50Z with ATI Radeon card)
Every time I go to Youtube and watch a video on firefox, the whole machine crashes, black screen, red lines, have to manually switch it off. 
Interestingly, this does NOT happen when I watch the videos using Konqueror, and also on firefox it does not happen when the video is embedded in another website, only on the Youtube site!.

I tried various things and waded through tons of forums and posts, disabled apci etc etc. When I disabled compositing, it worked again on Firefox, tried a few times, all ok. This morning it was back to the same problem, regardless of compositing on or off...

I went into the system logs and found this radeon message every time the system crashes

```

kernel	[  414.164077] [drm:radeon_fence_wait] *ERROR* fence(cc036640:0x00004E62) 508ms timeout going to reset GPU
kernel	[  414.164089] radeon 0000:01:05.0: GPU softreset 
kernel	[  414.164095] radeon 0000:01:05.0:   R_008010_GRBM_STATUS=0xA0003030
kernel	[  414.164100] radeon 0000:01:05.0:   R_008014_GRBM_STATUS2=0x00000003
kernel	[  414.164109] radeon 0000:01:05.0:   R_000E50_SRBM_STATUS=0x20001040
kernel	[  414.164123] radeon 0000:01:05.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
kernel	[  414.164179] radeon 0000:01:05.0: R_008020_GRBM_SOFT_RESET=0x00000001
kernel	[  414.164239] radeon 0000:01:05.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
kernel	[  414.164397] radeon 0000:01:05.0:   R_008010_GRBM_STATUS=0x00003030
kernel	[  414.164402] radeon 0000:01:05.0:   R_008014_GRBM_STATUS2=0x00000003
kernel	[  414.164407] radeon 0000:01:05.0:   R_000E50_SRBM_STATUS=0x20000040
kernel	[  414.165845] [drm:radeon_fence_wait] *ERROR* fence(cc036640:0x00004E62) 516ms timeout
kernel	[  414.165851] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x00004E62)
kernel	[  416.681049] [drm:radeon_fence_wait] *ERROR* fence(ca45f580:0x00004E64) 508ms timeout going to reset GPU
kernel	[  416.681060] radeon 0000:01:05.0: GPU softreset 
kernel	[  416.681066] radeon 0000:01:05.0:   R_008010_GRBM_STATUS=0xA0003030
kernel	[  416.681072] radeon 0000:01:05.0:   R_008014_GRBM_STATUS2=0x00000003
kernel	[  416.681078] radeon 0000:01:05.0:   R_000E50_SRBM_STATUS=0x20000040
kernel	[  416.681090] radeon 0000:01:05.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
kernel	[  416.681146] radeon 0000:01:05.0: R_008020_GRBM_SOFT_RESET=0x00000001
kernel	[  416.681206] radeon 0000:01:05.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
kernel	[  416.681363] radeon 0000:01:05.0:   R_008010_GRBM_STATUS=0x00003030
kernel	[  416.681368] radeon 0000:01:05.0:   R_008014_GRBM_STATUS2=0x00000003
kernel	[  416.681373] radeon 0000:01:05.0:   R_000E50_SRBM_STATUS=0x20000040
kernel	[  416.682806] [drm:radeon_fence_wait] *ERROR* fence(ca45f580:0x00004E64) 516ms timeout
kernel	[  416.682811] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x00004E64)
kernel	[  419.196085] [drm:radeon_fence_wait] *ERROR* fence(cc036b80:0x00004E65) 508ms timeout going to reset GPU
kernel	[  419.196097] radeon 0000:01:05.0: GPU softreset 
kernel	[  419.196104] radeon 0000:01:05.0:   R_008010_GRBM_STATUS=0xA0003030
kernel	[  419.196110] radeon 0000:01:05.0:   R_008014_GRBM_STATUS2=0x00000003
kernel	[  419.196115] radeon 0000:01:05.0:   R_000E50_SRBM_STATUS=0x20001040
kernel	[  419.196129] radeon 0000:01:05.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
kernel	[  419.196185] radeon 0000:01:05.0: R_008020_GRBM_SOFT_RESET=0x00000001
kernel	[  419.196245] radeon 0000:01:05.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
kernel	[  419.196402] radeon 0000:01:05.0:   R_008010_GRBM_STATUS=0x00003030
kernel	[  419.196407] radeon 0000:01:05.0:   R_008014_GRBM_STATUS2=0x00000003
kernel	[  419.196412] radeon 0000:01:05.0:   R_000E50_SRBM_STATUS=0x20000040
kernel	[  419.197848] [drm:radeon_fence_wait] *ERROR* fence(cc036b80:0x00004E65) 516ms timeout
kernel	[  419.197854] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x00004E65)
kernel	[  421.729096] [drm:radeon_fence_wait] *ERROR* fence(cc036ec0:0x00004E6D) 508ms timeout going to reset GPU
kernel	imklog 4.2.0, log source = /proc/kmsg started.
rsyslogd	[origin software="rsyslogd" swVersion="4.2.0" x-pid="854" x-info="http://www.rsyslog.com"] (re)start
rsyslogd	rsyslogd's groupid changed to 103
rsyslogd-2039	Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
rsyslogd	rsyslogd's userid changed to 101
avahi-daemon[877]	Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
avahi-daemon[877]	Successfully dropped root privileges.


```

I found this error message described in forums, but not sure how to fix it...

Does anyone have any idea what is going on here, why only on firefox, not Konqueror?
This described crash is 100% reproducible
I have had this issue a few times using Google Earth, black screen and red lines, but this was random and only happened about 3-4 times in 6 months

Please let me know if you need more info, very happy to give you more printouts/system logs etc...

I've been using Kubuntu for a few years now, I'm not a geek, but also not a complete novice. This issues though is totally over my head... :confused:

Thanks a lot
Cheers
Frank

---

### Post by fsando on 2011-03-03
I don't think anyone really knows right now. From other reports it seems to affect Chrome as well. I use Opera right now so as to not accidentally crash my machine.

EDIT: Just saw the same crash with Opera - so this is purely flash+yuotube

It worked with Opera yesterday but now it crashes like the firefox.

I saw somewhere that deleting cookies (not sure which but probably youtube ones) would solve the problem for some time but it would eventually come back.

---

### Post by Mercuryseven on 2011-03-04
I have the same problem too, and I'm using Ubuntu 10.04.  I have been searching the internet for the past few days, and you're the only other guy (besides) I know to have this problem.  I get a similar error message
```
[drm:radeon_fence_wait] *ERROR* fence(ed58ceco:0x000241cs) 504 ms timeout going to reset GPU
```Is this problem specific to our display system?  Here's an excerpt of my lspci command
```
VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
```

---

### Post by mrsfixit on 2011-03-04
I'm running Ubuntu 10.04 64 bit, this is happening to me as well. It started about 2 weeks ago. The video signal goes completely dead and the monitor shuts off, yet the sound keeps playing. Nothing I do on the mouse or keyboard has any effect. I have to power cycle the machine off.

I have an ATI Radeon 3650, which has been working fine using the open source driver for the past 6 months, including on youtube until now.

I'm seeing the same thing in the logs that you guys are. It's happening on Opera, Chrome and Firefox.

If anybody has a solution to this I'd love to hear about it. This is bad enough to make me think of (ugh) going back to Windoze... :-(

> **Mercuryseven said:**
> I have the same problem too, and I'm using Ubuntu 10.04.  I have been searching the internet for the past few days, and you're the only other guy (besides) I know to have this problem.  I get a similar error message
```
[drm:radeon_fence_wait] *ERROR* fence(ed58ceco:0x000241cs) 504 ms timeout going to reset GPU
```Is this problem specific to our display system?  Here's an excerpt of my lspci command
```
VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
```

---

### Post by Voluntocracy on 2011-03-04
Same here -- YouTube on Chromium and FireFox bombs; Konqueror OK.
Mobility Radeon HD 4500
x86_64
Began bombing Mar  2 19:17:37
Details at <http://voluntocracy.blogspot.com>.
YouTube in Konqueror just caused segfault in npviewer.bin

---

### Post by mrsfixit on 2011-03-04
So the common link is that this just started happening to most of us, we're all using ATI Radeon video cards, and it's only on youtube, right?

I tried it on 3 different browsers, with the same result, so it's NOT a Firefox problem per se.

---

### Post by FunkyFrank on 2011-03-05
Very interesting, thanks for all the replies. Makes me feel not quite so alone anymore :KS
THought I was the only one, but now it looks many ppl are scratching their heads over this one...
So has this been reported as a bug? Sorry for my ignorance, but I've never reported a bug, quite happy to if I know how and where...

Thanks
Frank

BTW, my ATI is this one (using the open source driver as well):
```

lspci
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

```

---

### Post by FunkyFrank on 2011-03-05
PPS:
I have read about a memory leak in the X.org server, could this be related to our problem?

[https://wiki.ubuntu.com/X/Testing/GEMLeak]("https://wiki.ubuntu.com/X/Testing/GEMLeak")

The command they are stating gives me:
```

grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
152203264 object bytes

```
The number is not as high as they stated for this issue, but 
I still tried the patch. The youtube issue is still there...:confused:

---

### Post by sumu-j on 2011-03-05
I'm having this issue also. I have Ubuntu 10.04 and Gigabyte MA785GM-US2H motherboard with Radeon 4200 graphics core.

Looks like this issue is caused by a software update received via Ubuntu Update manager. Is it possible to revert a particular installed update? Can the installed updates be seen in some log?

thanks,

J

---

### Post by sumu-j on 2011-03-05
Seems that xserver-xorg-video-geode display driver is to be blamed for this.

I got my issue fixed by reverting xserver-xorg-video-geode from 2.11.11-1~lucid1 to 2.11.8-4

-J

---

### Post by mrsfixit on 2011-03-05
> **sumu-j said:**
> Seems that xserver-xorg-video-geode display driver is to be blamed for this.

I got my issue fixed by reverting xserver-xorg-video-geode from 2.11.11-1~lucid1 to 2.11.8-4

-J

Ok, I'm *pretty* good with Ubuntu, but I'm not exactly a guru.

How do you "revert" a driver? Could you please post the steps that you took? It would be much appreciated. Thanks.

---

### Post by sumu-j on 2011-03-05
Here are the reverting instructions as I remember, use at your own risk:

1. Start Synaptic package manager.

2. Select to view Installed packages.

3. Mark xserver-xorg-video-geode for removal.

(xserver-xorg-video-all metapackage shall be removed also)

4. Click Apply. 

5. After you have removed the driver, it should be visible in 'All' or/and 'Not installed' view.

6. Mark  xserver-xorg-video-geode for installation.

7. From the menu, select Package -> Force version and select the older version of the driver.

8. Click Apply.

I did not bother to re-install the removed metapackage, not sure about the consequences, none observed so far.

9. Reboot and test.


regards,

J

---

### Post by Voluntocracy on 2011-03-05
There is no package named  xserver-xorg-video-geode on my Ubuntu 10.04.1 system.
There is xserver-xorg-video-radeon, but the only updates between YouTube working and YouTube crashing here was a kernel update -- and booting with previous kernels doesn't fix it.

Start-Date: 2011-03-02  10:42:14
Install: linux-headers-2.6.32-29-generic (2.6.32-29.58), linux-headers-2.6.32-29 (2.6.32-29.58), linux-image-2.6.32-29-generic (2.6.32-29.58)
Upgrade: linux-generic (2.6.32.28.32, 2.6.32.29.35), linux-headers-generic (2.6.32.28.32, 2.6.32.29.35), linux-image-generic (2.6.32.28.32, 2.6.32.29.35), linux-libc-dev (2.6.32-28.55, 2.6.32-29.58)
End-Date: 2011-03-02  10:43:29

---

### Post by Voluntocracy on 2011-03-05
/var/log/apt/history.log
/var/log/dpkg.log

---

### Post by sumu-j on 2011-03-05
Well, after all, my Youtube playback is still crashing. So much for reverting the display driver. Damn.

---

### Post by mrsfixit on 2011-03-05
> **sumu-j said:**
> Well, after all, my Youtube playback is still crashing. So much for reverting the display driver. Damn.

I appreciate the instructions anyway. Since your machine is still crashing, I won't bother to try it.

How do we submit this bug to the developers? I think this issue is critical as it is bringing everyone's computer to it's knees. :(

FWIW- this is the worst problem I have *ever* had with Ubuntu. It's been really great up to now.

---

### Post by illopos on 2011-03-05
Why is only youtube affected? I have been able to see flash videos on other sites without crashing. Also, I was able to view youtube embedded video from google reader. Even more intriguing is that on youtube, if I click on any video with an ad, the ad is played completely and the system crashes only after the actual video starts.

---

### Post by mastablasta on 2011-03-05
today i noticed that only some videos on You tube crash Kubuntu sound and video. well not completelly. but they do. in my case video i watch turns red, sound is gone ( can be restored by using alsa reload command). i can see some of the videos quite fine, running default opensource drivers. It seems one of the updates f..ed up this. nice work.

i think i will turn off all updates form now on. this is getting ridiculous. before i had sound issues, i upgraded and moved from U to Kubuntu 10.10. suddenly sound works fine as it should (so does the hibernation/suspend) but now this flash gaves in.   and it worked before when i tested live as well as after the install.

---

### Post by 4partee on 2011-03-05
Had the freeze problem in U10.4.

Installed the proprietary driver in 'Hardware Drivers'.  

Youtube Works now.

John

---

### Post by mrsfixit on 2011-03-05
> **4partee said:**
> Had the freeze problem in U10.4.

Installed the proprietary driver in 'Hardware Drivers'.  

Youtube Works now.

John

I'm going to wait for confirmation from others before I try this. I've read of too many issues with the proprietary ATI drivers. What works with your ATI card may not work with all of them...

---

### Post by sumu-j on 2011-03-06
My efforts in trying try to revert to an older version of xserver lead to an unfortunate situation where I had to re-install the whole OS. Be careful out there! :-)

Now that I have the system up and running again with latest kernel and xserver updates, my Youtube video playback has been working flawlessly so far. Now that I said that, it is to be expected that I'll face the issue again soon... ;-)

Just wondering whether the issue could have been somehow caused by the Video DownloadHelper plug-in that was installed to Firefox in my previous setup. Currently I don't have that plug-in installed.

-J

---

### Post by pieroxy on 2011-03-06
Same issue here. It's been a couple of weeks, I don't really remember exactly.

For you guys out there, you don't need to do a hard reboot (with the power/reset button), you can shut down Ubuntu from two different ways:

1. SSH from another box on your network. Then type "sudo shutdown -r now" to reboot. Replace -r with -h to shut down.

2. Hit Ctrl-Alt-F1. There, you still can't see a thing. You should log in blindly (type user name / Enter / Password / Enter) and then type the command above, followed by your password. Beware that my numeric keypad doesn't work, so if you have numbers use the keys above your keyboard, not on the side.

#1 is better of course. You see what you are typing.

For reference, killing X and restarting it isn't enough. You need to restart ubuntu.

---

### Post by pieroxy on 2011-03-06
btw I'm using Ubuntu, not Kubuntu. I had this issue with Firefox so I switched to Chrome and everything worked allright for a few month. Since the last update, every browser on youtube crashes the ATI driver.

Very, very, very painfull. I watch my Youtube videos on a windows VM, which is a shame in and of itself.

Anyone knows video cards that are well supported?

---

### Post by mrsfixit on 2011-03-06
> **sumu-j said:**
> My efforts in trying try to revert to an older version of xserver lead to an unfortunate situation where I had to re-install the whole OS. Be careful out there! :-)

Now that I have the system up and running again with latest kernel and xserver updates, my Youtube video playback has been working flawlessly so far. Now that I said that, it is to be expected that I'll face the issue again soon... ;-)

Just wondering whether the issue could have been somehow caused by the Video DownloadHelper plug-in that was installed to Firefox in my previous setup. Currently I don't have that plug-in installed.

-J

An OS reinstall is *exactly* what I'm afraid of... good grief, I don't want to have to go through that. My system is set up exactly how I like it right now... :(

I also have Video DownloadHelper installed in Firefox, but I'm getting the same crash in Opera and Chrome which don't have any plugins, so I don't think that's the problem.

---

### Post by mrsfixit on 2011-03-06
I have 2 desktops on my network, His & Hers Dell's. Mine runs Ubuntu, my husband's runs XP. Hubby has taken a liking to MY system, and according to him- this problem started Saturday, Feb. 26th.

I don't know if this info helps anyone, but I thought I'd put it out there anyway.

This is getting very frustrating, and I'm on the verge of swapping out the video card that something more compatible. I'd like to hear from others who might be considering this as well... :(

---

### Post by pieroxy on 2011-03-07
> **mrsfixit said:**
> This is getting very frustrating, and I'm on the verge of swapping out the video card that something more compatible. I'd like to hear from others who might be considering this as well... :(

Frustrating to no end! I am also considering changing my video card. There are basically three chips manufacturers: ATI, NVidia and Intel. By far the best supported chips are Intel's. However, there are no third party video cards with Intel chips. It's just integrated chips on mother boards. The second lesser evil is NVidia, but then I had one and it burned in 6 month.

So... I don't know. I can't imagine this problem not getting fixed. But when?

---

### Post by pieroxy on 2011-03-07
Did you try to install the proprietary drivers? Go to System > Administration > Hardware Drivers. In there you should see the "ATI/AMD proprietary FGLRX graphics driver". It almost worked for me. I have a dual screen setup with two monitors that don't have the same resolution and I couldn't get it working. Youtube worked though (even if you can't put it in full screen).

Well, different set of bugs. It might work for you.

---

### Post by mastablasta on 2011-03-07
> **pieroxy said:**
>  The second lesser evil is NVidia, but then I had one and it burned in 6 month.

 
ok this was really bad luck. I use ATI/AMD, but i know nvidia are very good cards. and they can usually work well for quite some time.
 
unfortunatelly i can't use proprietary drivers as i use RAdeon 9600XT. so only opensoruce for me. i could install Edgers PPA, but i dont' think it's the card drivers. i suspect flash. as some videos work OK. and because sound also crashes.

---

### Post by sumu-j on 2011-03-07
2.6.32.29 kernel changes can be seen here:

[http://lwn.net/Articles/428682/](http://lwn.net/Articles/428682/)

There are some modifications done to Radeon driver.

I have contacted the Radeon driver author about this issue.

-J

---

### Post by mastablasta on 2011-03-07
thank you. let's hope they fix it with next patch and make it like before when it was all working well.

---

### Post by =JeffH on 2011-03-07
I ran an upgrade last night on a Dell C610 from 10.04 to 10.04.1. it had been running 10.04 nominally fine (tho there was a subtle display issue i could workaround). 

upon reboot after the "upgrade", the system seems to boot but the screen is a total mess of colored lines and such. I managed to get it to a console prompt (ctl-alt-f1 ?) and logged in and things looked fine, but didn't have time to properly look around. that machine has an AtI Radeon chip in it.

I have another system, a Dell D820 with a NVidia Quadro display chip, and it developed weird display issues upon upgrade to 10.04.1, but I discovered a workaround where I can drop to console prompt, let it sit, and eventually, it restarts the GUI and all is fine. :-/   I use this system daily for /work/ and /cannot/ have it suddenly go south on me. 

I'm *VERY* disappointed and disturbed by this drop in quality in Ubunutu releases -- this is REALLY serious and unacceptable. I've been using ubuntu as my mainline system for work and personal applications for about five years now, and this is the most serious problem I've had. Plus I've been evangelizing Ubuntu to colleagues and friends over the years. 

If this is a sign of where quality is going, I'll have to consider migrating. I simply don't have time for such shenanigans.

=JeffH

---

### Post by mrsfixit on 2011-03-07
> **=JeffH said:**
> I ran an upgrade last night on a Dell C610 from 10.04 to 10.04.1. it had been running 10.04 nominally fine (tho there was a subtle display issue i could workaround). 

upon reboot after the "upgrade", the system seems to boot but the screen is a total mess of colored lines and such. I managed to get it to a console prompt (ctl-alt-f1 ?) and logged in and things looked fine, but didn't have time to properly look around. that machine has an AtI Radeon chip in it.

I have another system, a Dell D820 with a NVidia Quadro display chip, and it developed weird display issues upon upgrade to 10.04.1, but I discovered a workaround where I can drop to console prompt, let it sit, and eventually, it restarts the GUI and all is fine. :-/   I use this system daily for /work/ and /cannot/ have it suddenly go south on me. 

I'm *VERY* disappointed and disturbed by this drop in quality in Ubunutu releases -- this is REALLY serious and unacceptable. I've been using ubuntu as my mainline system for work and personal applications for about five years now, and this is the most serious problem I've had. Plus I've been evangelizing Ubuntu to colleagues and friends over the years. 

If this is a sign of where quality is going, I'll have to consider migrating. I simply don't have time for such shenanigans.

=JeffH

Yes, I completely agree.

I've been experiencing verrrrrry slow usb transfer speeds when copying files to thumb drives, this is a *known* problem, and has never been fixed.

I also have a problem with "jack sensing"- when I plug a pair of headphones into my computer, the sound to my external speakers remains on. Nothing I do fixes the problem. 

Previous versions of Ubuntu had a "jack sense" option for this- 10.04 does not. I opened up alsamixer and the option is no longer there. Another *known* problem that hasn't been fixed.

Now this...

I have been an Ubuntu convert and advocate since 9.04, but with the mounting problems I am starting to question the wisdom of sticking with this OS.

Is the problem just with Ubuntu, or with ALL Debian based distro's as well?

I am very disappointed, and the thought of having to go back to Windows makes me cringe. But I need the bloody machines to work, I don't have time for this kind of nonsense either.

---

### Post by hun.gergov on 2011-03-07
Hi!

I have the same problem here. Last week firefox started to crash when i tried watching youtube videos. I noticed that every other flash based sites work without problems, even youtube in chrome.
Since I have an Nvidia 8600MGT I don't think it's a problem with the radeon driver.
I didn't update my system before the problem came out so I think it's caused by youtube changing something on their sites.

---

### Post by dnguyen1963 on 2011-03-07
Here is something to scratch your head with...download Mint or ArtistX (both are based on Ubuntu but with all the media codecs installed) then run the live CD/DVD to watch YouTube videos.  I bet you will not have any problem.  If you like either version of OSes, perform the install but DO NOT perform any update.  For some reasons, update via update manager screws up Flash big time.

---

### Post by sumu-j on 2011-03-07
> **hun.gergov said:**
> Hi!

I have the same problem here. Last week firefox started to crash when i tried watching youtube videos. I noticed that every other flash based sites work without problems, even youtube in chrome.
Since I have an Nvidia 8600MGT I don't think it's a problem with the radeon driver.
I didn't update my system before the problem came out so I think it's caused by youtube changing something on their sites.

Well, the original issue in this thread is about system level crash that paralyzes the whole OS, not just the browser. And AFAIK, the original problem concerns only Radeon chips. Correct me if I'm wrong.

J

---

### Post by mrsfixit on 2011-03-07
> **sumu-j said:**
> Well, the original issue in this thread is about system level crash that paralyzes the whole OS, not just the browser. And AFAIK, the original problem concerns only Radeon chips. Correct me if I'm wrong.

J

No, you're not wrong. All of us Radeon users are the ones with the problem. 

The system crash occurs on Firefox, Chrome, and Opera.

I think I am going to turn off automatic updates before something else goes fubar...

---

### Post by mrsfixit on 2011-03-07
> **dnguyen1963 said:**
> Here is something to scratch your head with...download Mint or ArtistX (both are based on Ubuntu but with all the media codecs installed) then run the live CD/DVD to watch YouTube videos.  I bet you will not have any problem.  If you like either version of OSes, perform the install but DO NOT perform any update.  For some reasons, update via update manager screws up Flash big time.

I downloaded Mint 10 64 bit DVD, I am running it right now from the DVD and posting this message.

I went to Youtube, played some videos, and didn't have any crashing problems.

So I can confirm that as of right now on Mint I am having no issues, at least on Youtube, using the open source drivers.

If the problems with Ubuntu are not solved I may have to switch. I hope the Mint Gnome is as customisable as the Ubuntu Gnome, because this interface is way too minimal for my taste... :)

Anyway, I thought I'd let you fine folks know that this is working- so far...  :P

---

### Post by Mercuryseven on 2011-03-07
> **pieroxy said:**
> Did you try to install the proprietary drivers? Go to System > Administration > Hardware Drivers. In there you should see the "ATI/AMD proprietary FGLRX graphics driver". It almost worked for me. I have a dual screen setup with two monitors that don't have the same resolution and I couldn't get it working. Youtube worked though (even if you can't put it in full screen).

Well, different set of bugs. It might work for you.

I tried this and it's working now!  I can now watch Youtube, and can get full screen too...

---

### Post by Br1987 on 2011-03-07
I ahve he same problem! but I don't have a ATI Radeon video card.. I'm using a SiS (Silicone Integrated Systems) 300/305/630/540/730 32 Mb so I'm starting to think that the problem has to do with the update manager... can't get you tube to work though =X

---

### Post by Altusanew on 2011-03-07
I am also having these same issues with Kubuntu 10.04 and Flash on an ATI 4850 card after an update with no previous issues to speak of running the OSS default drivers. 

However, as of sometime this evening I am also seeing what looks like compositing issues with what seems to be anything Plasma related. Everything that is not related to the application that I am running is totally screwy. I have attached a screen shot for anyone interested. 

If there is a bug open on this or if there is some dev out there who thinks this should be reported as a bug let me know and I will gladly help with that effort. I am kind of a noob at times so please be gentle. :) For now I am going to install the drivers from the amd.com site and see what happens. I will try to report my findings back here.

I have run Kubuntu since it was last shipping KDE 3.5 and it has always run great for me. I also run AMD graphics because next to Intel they do their best with their open source driver support efforts, including all the documentation for driver developers and what not. This is why I try to stick to their hardware to show my support for those efforts.

---

### Post by Altusanew on 2011-03-07
So I updated to the 11.2 AMD pro driver and I seem to be able to watch Youtube vids with out crashing the system but I am still having the compositing issues. So still working on it. About to hit up IRC next.

---

### Post by Altusanew on 2011-03-08
Wow that was an ordeal. Never was able to get the drivers from AMD's site to actually install. Kept getting some error while trying to install the kernel modules. Finally installed using the built in driver installer and it is now reporting as an ATI driver vendor. Fixed compositing issues and Flash/ Youtube crashing issues in Chromium and FF.

I was really hoping to keep running the FOSS drivers from the LTS repos through the life of this install and on to the next install in April of 2012. I guess it was not to be. Maybe some day when the switch to Wayland/ gallium3d radeon drivers happens we will see some more stability, speed, and features.

Post here if these steps did or did not fix your issue. I still think we should get a bug submitted on this problem.

---

### Post by mastablasta on 2011-03-08
i think new FOSS drivers can be installed using the Edgers PPA. I haven't tried it yet if it solves the problem. What i can't understand is why no one tested this on other systems before cretaing an "update".

---

### Post by Voluntocracy on 2011-03-08
[http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)
"fix 3" solved my radeon linux crashes on YouTube videos.

---

### Post by PeteJCF on 2011-03-08
Hello there everyone. I've also had this problem in my system, although not as bad as some have described. I noticed that this past weekend when I went on the youtube site and the videos wouldn't play. There was sound for brief moments only and then the browser would freeze up and some (long) moments later it would go back to normal after I hit the close button on the youtube tab. This happened with Firefox, chrome and opera. I read all of the posts in this thread. Did some procedures and got nothing. Moments ago I decided to uninstall the Ati/AMD proprietary FGLRX graphics driver. Before restarting the system youtube videos on youtube site were playing flawlessly with firefox and chrome. After restarting the system, when playing a video on the youtube site, the screen goes black, showing some colour lines and then restarts on its own. If I reinstall the Ati/amd driver I go back where I started from: video playing on the youtube site and the browser freezes up. I’m using Ubuntu 10.04 and a Radeon HD 4650. Sorry for the long post. Hope that someone can help out a noob here.

---

### Post by PeteJCF on 2011-03-08
Two enthusiastic thumbs up for you Voluntocracy. "fix 3" also worked for me! youtube videos are now playing flawlessly on youtube site with both firefox and chrome and with the ATI/AMD proprietary driver installed. Thanks again for the tip!

---

### Post by PeteJCF on 2011-03-08
> **Voluntocracy said:**
> [http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)
"fix 3" solved my radeon linux crashes on YouTube videos.

Two enthusiastic thumbs up for you Voluntocracy. "fix 3" also worked for me! youtube videos are now playing flawlessly on youtube site with both firefox and chrome and with the ATI/AMD proprietary driver installed. Thanks again for the tip! Sorry for the double post. I wanted to quote the user.

---

### Post by FunkyFrank on 2011-03-08
Hi all,

yes, big thanks also from me, fix 3 worked miracles, everything is fine again, youtube's playing on Firefox again...
Still using the open source drivers btw

Phew

Cheers
Frank

---

### Post by pieroxy on 2011-03-09
> **PeteJCF said:**
> Two enthusiastic thumbs up for you Voluntocracy. "fix 3" also worked for me! youtube videos are now playing flawlessly on youtube site with both firefox and chrome and with the ATI/AMD proprietary driver installed. Thanks again for the tip! Sorry for the double post. I wanted to quote the user.

I don't think anyone was having issues with the proprietary drivers. It works for me out of the box with the proprietary drivers. Only the open source drivers do crash the system... At least, that's what this thread is all about.

---

### Post by Voluntocracy on 2011-03-09
> **pieroxy said:**
> I don't think anyone was having issues with the proprietary drivers. It works for me out of the box with the proprietary drivers. Only the open source drivers do crash the system... At least, that's what this thread is all about.

Installing "linux-firmware-nonfree" drivers made no difference on my Ubuntu 10.04.1 system.
[http://voluntocracy.blogspot.com/2011/03/youtube-hangs-my-ubuntu-1004-hp-dv7.html](http://voluntocracy.blogspot.com/2011/03/youtube-hangs-my-ubuntu-1004-hp-dv7.html)

---

### Post by samcoinc on 2011-03-09
I also disabled acceleration - problem went away.  (ubuntu 10.04 lts)  It started about a week ago.  Updated firefox and flash to no avail.   The computer would black screen.  Could not get to console or nothing.  hard reboot required. 

(I am also using open source drivers)  dell xps 1645 with ati 4670

THANK YOU!
sam

---

### Post by mrsfixit on 2011-03-09
Ok, here is my experience since yesterday...

I also tried disabling hardware acceleration, and now I can play Youtube videos again without crashing.

However... and this is *only* in Firefox- I can no longer play Hulu videos, when they worked fine a couple of days ago. The problem is only in Firefox, Chrome and Opera will play Hulu with no problem. 

Even if I re-enable hardware acceleration, it doesn't crash, it just won't load. I just get a black box in Hulu that says "Sorry, we are unable to load the player. Please check your internet connection, clear your browser cache, and try again". I did all that, and Hulu still doesn't work.

Can someone else check Hulu using Firefox?

So I did take 2 steps forward, but also took a step back... :confused:

---

### Post by samcoinc on 2011-03-09
hulu seems to be working fine here.  

sam

---

### Post by mrsfixit on 2011-03-09
> **samcoinc said:**
> hulu seems to be working fine here.  

sam

Thanks for checking, it was helpful.

I just tried loading a different profile of Firefox, one with no plugins, and Hulu works. So one of my plugins is causing the problem.

I do have NoScript, which is becoming more of a PITA than it's worth, and also AdBlock, and Flashblock, but Hulu is whitelisted and all popups, flash and everything is allowed on that site.

I guess I'll have to start disabling the plugins one by one until I track it down.

Thanks for checking. :)

---

### Post by mrsfixit on 2011-03-09
Update:

I updated NoScript to the latest version. NoScript plays nicely with Hulu again.

I guess I should have checked the version of NoScript I had first... duh....I never said I was the sharpest tool in the shed... LOL :-)

YouTube still working for me, so fix #3 was a solution. :-)

**************************************************************

It was NoScript...

I disabled it and Hulu started working.

NoScript was good at one time, now it's turned into a huge PITA. No matter if I enable *everything* on sites like Hulu, it still screws up sites with multimedia and prevents them from working.

Time for it to go....

---

### Post by PeteJCF on 2011-03-09
Correct pieroxy. Maybe I didn't explained myself clearly enough. And, yes, the full system crash (black screen with colour stripes + reboot) only happened when I was using the open source drivers. After running "fix 3" gently posted by Voluntocracy, youtube videos now play flawlessly either way (with the proprietary drivers or with the open source ones). However, I still find it curious that the system was able play the youtube videos correctly on the youtube site after uninstalling the proprietary drivers and before restarting (this before "fix3" was posted).

---

### Post by pieroxy on 2011-03-09
I can confirm that the fix 3 works as well. Problem "solved" for me.

---

### Post by elfiii2008 on 2011-03-12
Many many many thanks to Voluntocracy! :D
Worked for me too. I was becoming desparate.

> **Voluntocracy said:**
> [http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)
"fix 3" solved my radeon linux crashes on YouTube videos.

---

### Post by peterVG on 2011-03-12
We were experiencing same problem on Ubuntu 10.04 & ATI RV770 [Radeon HD 4850] (black screen when viewing YouTube)

Disabling YouTube cookies as per fix 1 here solved it for us:
[http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)

---

### Post by albywolf on 2011-03-12
I have the same problem, Kubuntu 10.04 64bit, onboard Radeon HD3300, open source drivers, it crashes watching Youtube videos. I'll try the fix, thanx in advance.

---

### Post by Howie Spitz on 2011-03-13
ATI Radeon HD 3870, ";system level crash that paralyzes the whole OS, not just the browser".  Possible fix 3 (disable Adobe Flash hardware acceleration): Did not work for me.  > **4partee said:**
> Had the freeze problem in U10.4.

Installed the proprietary driver in 'Hardware Drivers'.  

Youtube Works now.

John

 Worked for me too! Thanks!

---

### Post by albywolf on 2011-03-18
> **albywolf said:**
> I have the same problem, Kubuntu 10.04 64bit, onboard Radeon HD3300, open source drivers, it crashes watching Youtube videos. I'll try the fix, thanx in advance.

Tried fix #3: Adding the file with acceleration disabling only in [FONT="Lucida Console"]/etc/adobe[/FONT] didn't work, to make it work I had to add the same file also in [FONT="Lucida Console"]~/.adobe[/FONT].
Curiously, sometimes it doesn't work anyway. I'll try to clean Youtube's cookies too. I'm also curious whether the latest kernel update solves the problem, if I find the time to risk another crash, I could try enabling again the acceleration...

---

