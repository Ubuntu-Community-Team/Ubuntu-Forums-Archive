---
title: "Computer consistently randomly freezes"
date: 2010-04-16
forum: General Help
---

### Post by compu73rg33k on 2010-04-16
After 6 months or so I noticed my 9.10 install getting sluggish and it started to freeze habitually. I let it go until one day it consistently froze at the startup login screen.

I installed 10.04 and the problem continued - After first installing it worked for about 6 hours without a crash, and then once again the problem developed into consistently freezing at the login screen.

I tested with some USB Live sessions and my live sessions never froze, even when active for a whole day. Remembering some I/O BAD SECTOR error messages from my 9.10 crash, I determined the error may be with the hard drive so I bought a new [Hitachi SATA hdd]("http://www.amazon.com/Hitachi-Travelstar-Internal-HD20500IDK-7K/dp/B002FYJQB8") (needed more GBs anyway).

I installed 10.04 on the new hdd (H and after 6 hours again it crashed. When it crashes the screen freezes for about 3 seconds and then the graphics wildly split and it's just a jagged gray screen. However, as time has gone on over the past 2 days, the freezing situation has been better in that it hasn't come to the point where the computer consistently freezes on the login screen. The time before it freezes has varied from 10 minutes to 6 hours.

I think it's maybe a software issue with the nvidia drivers. I'm having trouble diagnosing this bug or providing information. I've included the output of lspci -vvv

I have the nVidia GeForce Go 6100 graphics card

---

### Post by switch10 on 2010-04-16
Have you run a memory check on it?  Sounds to me like your RAM may be failing..

---

### Post by compu73rg33k on 2010-04-16
> **switch10 said:**
> Have you run a memory check on it?  Sounds to me like your RAM may be failing..
Interesting. I haven't run a memcheck from startup, that is what you're talking about right? I'll try it and report the results back. Initially I feel like it wouldn't be the RAM since I bought it new 18 months ago, but it's def a possibility so I'll try it and report back. Thanks for the tip.

Is there any other log files I should post that would help the community diagnose this with me?

---

### Post by warfacegod on 2010-04-16
I agree with switch10. This sounds more like a hardware issue than soft. The first culprit is likely RAM. Then I'd say HDD but you've already replaced that so I figure video card is next.

I have the nVidia GO5200. It uses the 173 driver which is fairly old now and should be quite stable. Your card should use the same driver or at least one that's very close sequentially so you *should* be fine in that area. Even still, have you tried a different driver?

---

### Post by compu73rg33k on 2010-04-17
I ran a memtest and it passed 100%. I'm running it again and am planning on letting it just run memtests all day to see if it would freeze after a long period of time even doing memtests.

I tried all 3 provided nvidia drivers and it froze in all 3 cases. the 93 has seemed to give me the longest time without freezing, though I think this may just be coincidence.

I guess my next plan is to try re-installing 9.10 and see if it freezes. I'm planning on keeping my /home and not reformatting that partition, just my / and /usr partitions - should that be OK?

Any other ideas? Thanks for the help so far.

---

### Post by warfacegod on 2010-04-17
Your /home partition is where most of your user preferences are kept. They're hidden folders. It is conceivable that one of your settings is the cause of your freezing problem. I would create a new user account and use it for a day or so to see if it freezes without your user settings. But to answer your question, no it doesn't look like there are any flaws in your plan.

---

### Post by mhgsys on 2010-04-17
Have you checked the machine on overheating?

f.e you can monitor this with with computertemp
open a terminal and type:

```
sudo apt-get install computertemp
```

after that right click a panel, click add to panel and select computer temperature monitor.

That way you can monitor the temperature set an alarm etc.

*If it's not there, reboot, It will be there after
**(Don't know if maybe it also appears by restarting gdm)

**If you don't get any output on the computertemp-sensor, install libsensors4 & lm-sensors as well.**
after that run
```
sudo sensors-detect
```

and try again.

(I monitor my temp with screenlets on my amd-athlon, since it seems to have a problem with computertemp, which works fine with 10.04 on my belinea c1541 laptop)

---

### Post by compu73rg33k on 2010-04-17
> **mhgsys said:**
> Have you checked the machine on overheating?
Thanks for the tip. I installed the monitor and added the widget to my panel. I'm skeptical that this is the issue though because when it freezes, I am able to reboot and there's no coorelation to how long the next session will survive before freezing again. A few years back I had a heatsink issue and when my CPU got too warm, usually within 10 minutes, the computer would shut off but when I turned it back on, since it was still really warm, it would instantly turn off again. In this case, I can reboot and the session could last hours again.

Anyway, for the preferences, I"m monitoring "ACPI" It just froze again and the temperature read 45 degrees celsius. The default alarm was 80 so I don't think this is the issue.

Also I'm beginning to doubt that it's a hardware issue since I just ran the memtest for 10 hours straight. Passed every test 100% and never froze. But after rebooting and logging in it froze within 10 minutes. I'm beginning to think maybe it's a bug with xserver. Can anyone help me locate a log that would help debug further and determine if its an xserver issue?

---

### Post by warfacegod on 2010-04-17
Is there a common program running for every freeze. For instance, my laptop freezes on me every two weeks or so and I'm fairly sure that ktorrent has been running each time.

---

### Post by john newbuntu on 2010-04-18
Looks like you have done some fairly intensive checks.  However, Lucid is on the bleeding edge and would be a harder candidate to solve your problem.  I wished you used karmic with all updates/upgrades.  You might also want to run fsck from a liveCD on all your linux partitions to check for consistency.

You should have all your logs in /var/log directory.  Check files like Xorg.0.log.old, syslog, kern.log, dmesg etc for anything odd.

You might want to keep the top command running in the background to check a culprit process and examine it at the time when the freeze happens. Example: top -b -n 500 -d 5 > topout
Keep increasing -n parameter if the freeze does not happen.

One other option would be to change the kernel.

---

### Post by kyalpani on 2010-04-18
I had this problem ever since after kernel 2.6.31-17-generic. No sooner I upgraded to a new kernel my desktop stated freezing completely and I had to reboot. Most of the time it happened while I am in firefox.

So now I revert back to kernel 2.6.31-17-generic and everything is fine. I do not know who to report the problem to. It must be somewhere in the kernel

---

### Post by compu73rg33k on 2010-04-19
> **kyalpani said:**
> I had this problem ever since after kernel 2.6.31-17-generic. No sooner I upgraded to a new kernel my desktop stated freezing completely and I had to reboot. Most of the time it happened while I am in firefox.

So now I revert back to kernel 2.6.31-17-generic and everything is fine. I do not know who to report the problem to. It must be somewhere in the kernelThanks for the tip. If this doesn't work, I think I'm going to install WIndows XP and see if that ends up freezing. If it's a hardware issue, it should make its presence known in XP too, right? Is it possible there would be some hardware error that only surfaced in Ubuntu?

I booted into 2.6.31-14 and it froze again after about an hour. I guess it's time to test Windows XP. Any other suggestions?

---

### Post by Karmic Alice on 2010-04-19
same problem here. fresh lucid install. on desktop P4 2.40 2 giga ram, video on board (asrock pi65gv) Ubuntu 9.10 worked fine.

Now firefox crashes me absolutely ANYTHING. since yesterday install of Lucid i get an error at each reboot. and now the worse just happened. Ill attach a picture as I really need help with this.
[URL="http://img697.imageshack.us/img697/8140/19042010005.jpg"]
[SIZE=3]http://img697.imageshack.us/img697/8140/19042010005.jpg[/SIZE][/URL] 

If is not the appropriate section, please feel free to move my reply. Because I really need an answer to my concerns:)

By the way, this happened all of a sudden while in gnome. No reboot or whatsoever. The keyboard's "caps lock" and "scroll lock" turned on and blinking. No option to choose from, just force reboot manually.

Each time I try to see a video on youtube sh*t happens. firefox is 3.6.3 (and I HATE IT!). I wanted to downgrade to 3.5.9 but when I installed lucid I decided nothing unofficial or NOT out of the box will be on it until it's official release. The only extra pack is "restricted extras"

Thanks!

---

### Post by klemes on 2010-04-19
Does deactivating compiz prevents the freezes?
I am saying this because there is a bug in launchpad affecting computers with certain video cards  running Ubuntu 9.10 with Compiz turned on resulting in complete system freezes(kernel panic).
Maybe it's this issue affecting you,so try with compiz turned off.

---

### Post by compu73rg33k on 2010-04-19
> **Karmic Alice said:**
> 
By the way, this happened all of a sudden while in gnome. No reboot or whatsoever. The keyboard's "caps lock" and "scroll lock" turned on and blinking. No option to choose from, just force reboot manually.
This happened to me when my problems originally started about 2 weeks ago. But since installing 10.04 the screen just freezes momentarily and then there's a segment of the window border that tiles across the entire screen.

Turning off compiz has no affect. The computer has even frozen on a default install with no extra programs running.

Installing Windows XP right now. If Windows doesn't ever freeze, then I'm going to maybe try 9.04 and see if a default install of that works.

---

### Post by compu73rg33k on 2010-04-20
I've been successfully running Windows XP all day. It hasn't frozen at all yet.

My next plan was to try and install 9.10 on another partition that doesn't recycle my /home/ dir with those settings. 9.10 was running successfully for 6 months before this started happening, which is why I would think it was a hardware issue .. but it's been stable with Windows on it all day. If it still freezes, I'll try 9.04.

Any other ideas? I have an old RAM stick I could at least try swapping in if more people think it could still somehow be a RAM issue even though memtest passed 3 times and WindowsXP is stable.

---

### Post by klemes on 2010-04-20
What can I say ,freezes in 9.10 are not entirely unheard of you know ;)
Better go directly to the new Lucid beta2 10.4 or is it Release Candidate nowadays?
I have tried it for the better part of a month and it has been proven super stable
so far.I suggest you give it a shot instead going back to 9.04.

---

### Post by compu73rg33k on 2010-04-20
I've already experimented with 10.04 and that causes the same issue. If it's a linux software bug then going back a few versions should make it stable because I've been running ubuntu on this laptop for the past 3 years with no problems until a couple weeks ago when this freezing error started. I'll post a SS soon of the screen when it freezes.

---

### Post by klemes on 2010-04-20
Well I do not know what to say.If it was about 9.10 I have experienced myself freezes too so it's no surprise to me.But with 10.04 everything just worked for me out of the box.
I do not have the slightest idea why 10.4 does not work for you as it should.I mean sure it is a kernel freeze but why ?
Have a look at this it might help pinpoint the reason behind that if you take the time to do a little debugging stuff:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by compu73rg33k on 2010-04-20
I've attached the photo. Does it seem like it would be an xserver issue? I've got 9.10 reinstalled on a single partition. After mounting my former /home dir (has all my files) it did the freezing thing again. I'm wondering if 10.04 creates some setting that is stored in my /home/ that is causing it to freeze...

Will let this fresh ubuntu install run for a while and if it is OK I'll reinstall 9.10 using my whole harddisk again and see if the lack of 10.04 settings in my /home makes the difference.

---

### Post by klemes on 2010-04-20
Well it seems one such to me!!!!
Are you able to switch into terminal mode using Ctrl+Alt+F1?Does then Ctrl+Alt+Backspace reboots the computer or does the caps lock led flashes and you need to hardware reset the machine.
If yo are able to switch to a terminal it is merely an X server related problem if not might be a complete system freeze.

---

### Post by Karmic Alice on 2010-04-20
> **klemes said:**
> Does deactivating compiz prevents the freezes?
I am saying this because there is a bug in launchpad affecting computers with certain video cards  running Ubuntu 9.10 with Compiz turned on resulting in complete system freezes(kernel panic).
Maybe it's this issue affecting you,so try with compiz turned off.


Is off. Compiz never started. The only way to get it started is:
```
$ compiz --replace
``` 
 And I'm running 10.04 beta2. 
But after manually starting compiz, I get "resume: libgcrypt version: 1.4.4" at reboot.


> **compu73rg33k said:**
> This happened to me when my problems  originally started about 2 weeks ago. But since installing 10.04 the  screen just freezes momentarily and then there's a segment of the window  border that tiles across the entire screen.

Turning off compiz has no affect. The computer has even frozen on a  default install with no extra programs running.

Installing Windows XP right now. If Windows doesn't ever freeze, then  I'm going to maybe try 9.04 and see if a default install of that  works.

This didn't happened to me on Karmic.

Ill try (another) clean install and report back.

---

### Post by P4man on 2010-04-20
If you still have XP installed, try playing some (3d) games. Or do the same on ubuntu and see if that causes faster freezing. Just a gut feeling there is a hardware problem with your videocard, having seen similar artifacts and problems with nvidia 6200 card that gave up on me.

---

### Post by Karmic Alice on 2010-04-20
> **klemes said:**
> Well it seems one such to me!!!!
Are you able to switch into terminal mode using Ctrl+Alt+F1?Does then Ctrl+Alt+Backspace reboots the computer or does the caps lock led flashes and you need to hardware reset the machine.
If yo are able to switch to a terminal it is merely an X server related problem if not might be a complete system freeze.

Hey! Thanks for your answers. Do you mind take a look at what's on my terminal when using  Ctrl+Alt+F1? (picture attached)

I don't have a xorg.conf in etc/X11. If this make sense. (newbie here :-$ )

---

### Post by klemes on 2010-04-20
> **Karmic Alice said:**
> Hey! Thanks for your answers. Do you mind take a look at what's on my terminal when using  Ctrl+Alt+F1? (picture attached)

I don't have a xorg.conf in etc/X11. If this make sense. (newbie here :-$ )

Your computer does not seem to freeze.It's just it cannot startup an X server(meaning  that it does not boot into graphical environment at this moment)
from what can be read at the top of the screen it it has something to do with i915_drm meaning that you have an issue with your Intel video card.Could you tell us which one exactly?ie 945 ,965 and so on...
If you can boot from a LiveCD and click on the icon of your hard drive on the desktop (if there is one ,if not you must manually mount your hard drive)and navigate to the file /var/log/Xorg.0.log,open it with gedit and cut & paste the results here.
That is assuming that running Ubuntu LiveCD gets you into full graphical environment.

---

### Post by Karmic Alice on 2010-04-20
> **klemes said:**
> Your computer does not seem to freeze.It's just it cannot startup an X server(meaning  that it does not boot into graphical environment at this moment)
from what can be read at the top of the screen it it has something to do with i915_drm meaning that you have an issue with your Intel video card.Could you tell us which one exactly?ie 945 ,965 and so on...
If you can boot from a LiveCD and click on the icon of your hard drive on the desktop (if there is one ,if not you must manually mount your hard drive)and navigate to the file /var/log/Xorg.0.log,open it with gedit and cut & paste the results here.
That is assuming that running Ubuntu LiveCD gets you into full graphical environment.

It does boot in the graphical environment. That's the problem. I don't know what is wrong with all the errors I get.  

Here is the Xorg.0.log and lspci. Thanks again!

---

### Post by Karmic Alice on 2010-04-20
I can't attach the xorg.0.log. 53 kb seems too big. ?
 I uploaded here: [http://www.wikiupload.com/kfJ8wlAN](http://www.wikiupload.com/kfJ8wlAN)

---

### Post by klemes on 2010-04-20
I am sorry I put you in all this trouble.I read back your first post where you clearly describe a kernel panic(caps lock and scroll lock LED's blinking).Your Xorg.log reveals no errors whatsoever and you are running an Intel 865 onboard video card which should be well supported in Linux.
It's a kernel panic from what I can gather but keeping in mind that firefox and other apps keep crashing it would be wise to do a full memtest before proceeding.
Also have a look at the link I provided in a previous post in this thread about complete system freezes in Ubuntu.
Also whenever a system crash occurs use Alt+SysRq+R+E+I+S+U+B instead of hardware reset because the first way provides for a much smoother shutdown preserving your hard disk contents(syncing disks then unmounting before reboot).

---

### Post by Karmic Alice on 2010-04-20
Oh! Don't worry! Not a trouble at all! I am grateful for your help. 
Right after i post the last message i ran a mem test that gave me NO ERRORS. 
 Regarding the hard reboot, trust me, when it freezes keyboard freezes too. I have another keyboard here (not multimedia) and another (NOT microsoft hehe) mouse.

Do you think is better to just take my HDD where win7 is installled and is a master, off? And leave just one hdd set to master then install fresh beta2? Or it worth the trouble of trying to fix all this mess? I don't have any information that I need in the system. All backed up on dvd's.

You tell me:)

---

### Post by klemes on 2010-04-20
I should have thought it was the darn Microsoft mouse!!!!!! hehe :lolflag:
Seriously though I am by no means a kernel expert and have truly no means to tell you what's wrong.If your computer does not freeze in Win7 and given it passed the Memtest,if I were you I would file a bug in Launchpad.I think it's the only thing left to do except maybe upgrading the kernel.;)
Pertaining your question I don't think it is necessary to unplug your master hdd in order to make a clean installation of LucidLynx,and since all your valuables are backed up you  could experiment all you want to,but I doubt it a clean installation will fix things because system freezes usually mean kernel bugs and that of course are reproducible as long as your kernel stays the same and no bugfixes have been applied.

If you are not fed up yet and you have no use for 3D Desktop Accelaration in your system I would try to make  a simple xorg.conf and put this lines in the section Device under the 'Driver "intel"' line:

Option "DRI" "Off" 
Option "AIGLX" "Off" 
Option "PM" "Off"  
Option "NoMTRR"

and let it run for a while.If no system crash occurs I would try to comment out one by one the above lines and see when the freeze reoccurs ,so I would comment again that line in the next reboot and possibly uncomment the others...


Good luck and keep us informed if you achieve anything with this.:)

---

### Post by Karmic Alice on 2010-04-20
Hello back. Clean install lucid (from usb - unetbootin) 
Only one HDD now. And I put a videocard ATI radeon HD 3650 512 mb 8x AGP. 

Same errors as the install from couple of days ago. First error was at first reboot. see 1st picture.

Second error was right after entering gnome desktop. 

Also ati asks to install the drivers (proprietary) which I won't do just yet. I had problems with this card in ubuntu 9.10. We all know ati HD 3650 and ubuntu 9.04 or 9.10 dont like eachother. 

Can somebody please tell me exactly what should I do next? I guess I need someone to blame:D:D:D:)))

Thank you all!

---

### Post by P4man on 2010-04-20
The IO errors seem to suggest you got a bad harddrive (or usb stick ?).

The crash detection thing, I wouldnt worry too much about that. I had plenty of those when I installed Lucid first (alpha 2 I think). Ran the updates, and they went away.

---

### Post by klemes on 2010-04-20
Well done!!!
And no freezes with the ATI video card?????
Who could tell even ATI has better support than Intel graphics cards in Linux.....
Oh my oh my....:)

---

### Post by Karmic Alice on 2010-04-20
[P4man]("http://ubuntuforums.org/member.php?u=412374") I guess is the usb and the darn unebootin. But this affects me now? I mean... is ok now? Or should I go for a iso dvd md5sum checked? And YES! First reboot after updates and NO ERROR!

[klemes]("http://ubuntuforums.org/member.php?u=508488") No freezes till now. But I didn't opened any youtube alike site yet. I still don't know if to install the proprietary drivers or not. :confused: Help please? Flash? What should I do next? I will start searching for " things to do after install ubuntu 10.04" but I am afraid are so many contradictory stuff out there.

For example compiz doesn't appear somewhere and in preferences>>appearance I see video effects set to normal. 

Now I am a bit lost and afraid to touch anything. 

 I will need codecs and I will need to choose something in software sources>>>other sources. I have the default 2 PPA's. But unchecked. I need them marked to get compiz work? I thought compiz will be up somehow...

Sorry for being a pain in the butt. Promise. And thanks all!

---

### Post by P4man on 2010-04-20
> **Karmic Alice said:**
> [P4man]("http://ubuntuforums.org/member.php?u=412374") I guess is the usb and the darn unebootin. But this affects me now? I mean... is ok now? Or should I go for a iso dvd md5sum checked? And YES! First reboot after updates and NO ERROR!

Good, then dont worry. Ive seen the IO errors on USB drives that worked perfectly fine, although ive never seen quite so many. 

> [klemes]("http://ubuntuforums.org/member.php?u=508488") No freezes till now. But I didn't opened any youtube alike site yet. I still don't know if to install the proprietary drivers or not. :confused: Help please? Flash? What should I do next? I will start searching for " things to do after install ubuntu 10.04" but I am afraid are so many contradictory stuff out there.

Install what you need :). Im not sure about the drivers for your card, the opensource one's you have automatically installed may be good enough. If you really need faster 3D, then you'll have to install the proprietary ones. You mentioned that card wasnt well supported, but frankly that would surprise me by this time. Id just install them, and if they bork your install, install again :)

> For example compiz doesn't appear somewhere and in preferences>>appearance I see video effects set to normal. 


Compiz is already running and enabled then. If you want more then those basic effects, and more than the "extra" (which adds wobbly windows), then install "advanced desktop effects settings" from the applications > software center. That installs a program to configure and tweak compiz. After installing, system > preferences will add a compiz menu where you can enable the 3d cube and a gazillion other things.

---

### Post by Karmic Alice on 2010-04-20
Yuhuuuu! (I was about to say "yahooo":P) Thank you so much! p4man, klemes, ubuntu:P:)

Working. And Catalyst is here and NONE of the problems in karmic are showing up! This is just great! 

I wanted to set up the display to a higher resolution that worked perfectly well time ago in XP. here the best I can get in wide is 1680 x 1050. (is even the one recommended by the manufacturer). Apart from that in System >>> Preferences >>> Display states "Unknown" and "monitor: Unknown". Even  if this is not affecting me till now, I can't avoid the feeling I am not taking all the best out of my lcd. Before installing the proprietary drivers for the videocard, in Monitor preferences I had the model and the manufacturer.

Anyway. That's just nothing and I thank you so much once more for the precious help.

P.S. Youtube (with adobe flash player) in full screen freezes the hell out of it all. Runs like a charm in normal size window. :( Which makes me think firefox 3.6.3 simply sux. There is no other way to put it.

---

### Post by P4man on 2010-04-20
> **Karmic Alice said:**
>  Apart from that in System >>> Preferences >>> Display states "Unknown" and "monitor: Unknown". 

Thats because ATI drivers now control your display, the gnome app you are using is now irrelevant. Im sure in catalyst control center the name and model of your monitor will show up somwehere.

> P.S. Youtube (with adobe flash player) in full screen freezes the hell out of it all. Runs like a charm in normal size window. :( Which makes me think firefox 3.6.3 simply sux. There is no other way to put it.

Dont blame firefox. Blame flash. But still that shouldnt happen. If you disable desktop effects, does it still happen? Im guessing it will work fine then, and if so, check this thread for possible solutions:
[http://ubuntuforums.org/showthread.php?p=7487421](http://ubuntuforums.org/showthread.php?p=7487421)

---

### Post by klemes on 2010-04-20
Hi! Glad it all (well almost...:)except fullscreen flash movies) works fine for you!!!!

The thing about the monitor analysis 1680 x 1050 (It's a Samsung monitor,isn't it????)
remind me of the story with my freshly bought monitor (about a year ago) that supported roughly only that particular analysis and guess what in Windows XP that came preinstalled (bootleg I am ashamed to say but gone a long time ago...) with my (secondhand) IBM desktop with it's ancient RivaTNT2 videocard (gulp...!!!!)you were not given the option of 1680 x 1050 even with the monitor drivers installed,resulting in a very blurred image for a brand new monitor....
When I switched to Linux every single distribution or LiveCD (with the exception of Zenwalk-LiveCD) I cared to throw at it recognized properly my monitor and they all defaulted to the correct analysis resulting in a crystal clear image bearing no resemblance to that produced by poor old XP.
This goes to show you somethings ,doesn' it?????
Anyway I was very impressed by Linux since that day!!!:guitar:

---

### Post by compu73rg33k on 2010-04-20
I installed 9.10 on a single partition and it's been running fine for the past 4 hours. It also ran fine for 6 hours over night. WHen I woke up I tried to mount my /home partition from my previous install and the screen immediately froze. I'm thinking it's either a multiple-partition issue, or some setting in 10.04 that was stored on my /home is causing it. I'm going to let this 9.10 install run for a couple more hours to verify that it's stable and then try installing 10.04 on a single partition and see if the freeze continues.

---

### Post by Karmic Alice on 2010-04-20
> **P4man said:**
> 
Dont blame firefox. Blame flash. But still that shouldnt happen. If you disable desktop effects, does it still happen? Im guessing it will work fine then, and if so, check this thread for possible solutions:
[http://ubuntuforums.org/showthread.php?p=7487421](http://ubuntuforums.org/showthread.php?p=7487421)
  Yeap:) Shows in Catalyst.

I've been there (link) before asking. When I ask and if I ask is when I finished all resources. And since I had a mess in the distro, last thing I care about was to fix youtube in firefox. Now I'm going there:)

Especially because YOU ARE RIGHT!!! No effects turns into AMAZING full screen flash tube (of course not even a delay in PAUSE, PLAY, Esc, Volume +-. I am "ubuntu" for a week now. And this is getting better and better. You guys are fantastic. And I mean it.

Did I thank you? hehe. Thanks!

---

### Post by Karmic Alice on 2010-04-20
> **klemes said:**
> Hi! Glad it all (well almost...:)except fullscreen flash movies) works fine for you!!!!

The thing about the monitor analysis 1680 x 1050 (It's a Samsung monitor,isn't it????)

Thanks! So kind of you... 
No, is philips 220sw 22''

> Anyway I was very impressed by Linux since that day!!!:guitar:

Karmic was my first real intent, after failing so bad several times when tried linux. And I am proud to say this time I stay. There is nothing in this world to get me back to the blue screen:). I really hope to find a good way to install the crap I need to watch soccer online (things like sopcast, veetle :P). But that I have it under control and **I am way too 'OFF TOPIC'**. :-\"

Cheers!

---

### Post by P4man on 2010-04-20
> **Karmic Alice said:**
> I am "ubuntu" for a week now. And this is getting better and better. 

You must not have had terribly high expectations from ubuntu, considering the problems you already encountered. Its getting "better and better", as in, "it appears to no longer crash every 15 minutes and i can even watch youtube after jumping through some hoops" makes windows 95 look good ;). Anyway good luck with the flash fix. Its definitely fixable.

@compu73rg33k
Good to hear you seem on the right track too. Is that /home partition on a different (physical) disk?

---

### Post by dxplosiv1 on 2010-04-20
I had a similar issue with my 9.10 setup. I thought mine was the graphics card so I replaced it but ran into the same problem. In the end, I think I de-activated and re-activated the third party hardware drivers from the admin menu and it solved my problem.

---

### Post by Karmic Alice on 2010-04-20
> **P4man said:**
> You must not have had terribly high expectations from ubuntu, considering the problems you already encountered. Its getting "better and better", as in, "it appears to no longer crash every 15 minutes and i can even watch youtube after jumping through some hoops" makes windows 95 look good ;). 
  No. Is my fault. I jumped to explain a thing assuming you know what I am talking about. I was trying to say that after installing like... 78615234125762354534589123 times in 2 weeks (9.10, 8.04, 10,04 upgrade and clean) I didnt expected much from MY HARDWARE. Not from ubuntu. Because I always wanted to be able to have the courage of trying at least. Nobody from whom I know ever had, used or plan to use linux. And that makes it harder for me. "it gets better and better" was about the comunity and about the WAY I START to see the magnitude of all this amazing place to be. Linux, ubuntu, forum, help, thrill :P:P. I missed this I guess:)

About MS? As I said. In the past few years I was fed up, but hey?! That's past. Here I am now. And no, never wine or alike... Is hard to understand my feeling. But trust me, 3 weeks ago I was a xp user. Hope you have an idea about LINUX being a new amazing, beautiful world to me. Is like.. like... waking up to go to work to the s***est job just to feed your family compared to having the job of your dreams and feel so sad when friday comes. hehe

Ok. I finished the chat and apologize for the offtopic.

---

### Post by compu73rg33k on 2010-04-20
Oh noes! After running smoothly for a while when I was upgrading the packages it crashed. It was already done downloading and in the midst of setting up the packages. How can I get a log to find out which packages it had already updated?

---

### Post by klemes on 2010-04-21
You are probably reinstalling by now (and quiet rightly so I may suggest) but for the history if you have not rebooted and still have a working system some things you could try to fix this mess are:

~#sudo dpkg --configure -a
~#sudo apt-get install -f
~#sudo apt-get install --fix-mising
and 
~#sudo apt-get update && sudo apt-get dist-upgrade

If none of the above works you have to reinstall from the LiveCD....
Sorry I was not able to see this earlier if it made any difference anyway....
Good luck and don't give up just yet!!!!!!
:)

---

### Post by compu73rg33k on 2010-04-22
> **klemes said:**
> You are probably reinstalling by now (and quiet rightly so I may suggest) but for the history if you have not rebooted and still have a working system some things you could try to fix this mess are:

~#sudo dpkg --configure -a
~#sudo apt-get install -f
~#sudo apt-get install --fix-mising
and 
~#sudo apt-get update && sudo apt-get dist-upgrade

If none of the above works you have to reinstall from the LiveCD....
Sorry I was not able to see this earlier if it made any difference anyway....
Good luck and don't give up just yet!!!!!!
:)
I tried all this and nothing helped. I checked my /var/log/syslog and there was nothing in there at the time of the freeze. Just "wpa_supplicant[1260] CTRL-EVENT-SCANT-RESULTS" lines that are all over the log. Any other logs I should check?

---

### Post by compu73rg33k on 2010-04-29
So I've tried several more options and nothing has worked. I installed 10.04 Ubuntu amd64, 10.04 Ubuntu x86, 9.10 Ubuntu, 9.04 Ubuntu, and 10.04 XUbuntu and they ALL give this same strange freezing error. Considering 9.04 and 9.10 ran fine throughout when they were current, I suspect it's some sort of hardware issues. I've already replaced the harddrive, and I ran 4 memtests which all passed with 100%. I even replaced the RAM with my original RAM chips that came with the laptop. Error still happened.

However, WindowsXP is stable and Windows 7 is too. But when I installed WIndows 7 for some reason when I try to install the graphics driver it says that the driver couldn't find the proper hardware for that driver. However the driver DOES work in XP. I'm wondering if there's an issue with my graphics card? But why would it be OK in WindowsXP?

Any ideas how I could further diagnose the issue?

---

### Post by klemes on 2010-04-29
> **P4man said:**
> If you still have XP installed, try playing some (3d) games. Or do the same on ubuntu and see if that causes faster freezing. Just a gut feeling there is a hardware problem with your videocard, having seen similar artifacts and problems with nvidia 6200 card that gave up on me.


 I think that P4man is right here and maybe replacing the video card
or testing with a borrowed or even an old one is the way to go from here.


EDIT:I just saw it was a laptop so things are more complicated.Maybe it must be repaired from a certified computer service shop if the video card is to be replaced then.Nothing else springs in mind right now after all these tests you performed...

---

### Post by P4man on 2010-04-29
If its the videocard dying (which would be my best guess looking at that screenshot), then it would almost certainly also occur under windows, at least under load (say, playing 3d games).

This is a long thread, I went through it again, but may have missed it. Have you posted your log files? Is there anything in there giving a clue around the moment the freezes happen? Also (another duplicate question I fear), does [REISUB]("http://kember.net/articles/231/reisub-the-gentle-linux-restart") still work when it freezes?

Anyway.. since you replaced ram, hdd and temps apparently arent the problem, so one more thing to try would be the bios. Maybe it got corrupted. I would reflash it (and while you are dong that, flash it to the latest).

---

### Post by compu73rg33k on 2010-04-29
> **P4man said:**
> Have you posted your log files? Is there anything in there giving a clue around the moment the freezes happen?I posted my /var/log/syslog and it didn't show anything leading up to the freeze. Is there another log i could post that could help diagnose the issue?

> **P4man said:**
> 
Also (another duplicate question I fear), does [REISUB]("http://kember.net/articles/231/reisub-the-gentle-linux-restart") still work when it freezes?I tried alt+sysreq+k and alt+sysreq+b but neither work. I also try to change to tty1 using ctrl+alt+1 but that doesn't work.

I'll try to get a game installed on my windows partition and test it under load. I noticed though in linux it was most likely to freeze when doing a 70GB transfer from external hdd to internal, or updating all the packages, or loading my music library into rhythmbox.

---

### Post by P4man on 2010-04-29
> **compu73rg33k said:**
> I posted my /var/log/syslog and it didn't show anything leading up to the freeze. Is there another log i could post that could help diagnose the issue?


well, perhaps the dmesg log would nice too.

> 
I'll try to get a game installed on my windows partition and test it under load. I noticed though in linux it was most likely to freeze when doing a 70GB transfer from external hdd to internal, or updating all the packages, or loading my music library into rhythmbox.

 that is interesting and could be a  good lead I think. The external drive is USB I assume? Does the problem also occur with the external drive disconnected? Can you try "stress testing" windows by copying large files back and forth on the internal drive ( I realize its a new drive, but it could be the cable or controller as well).

---

### Post by RJARRRPCGP on 2010-04-29
I would replace the CR2032 battery, reset the CMOS and try again. 

Because it's rare for onboard graphics to just fail. Unlikely, compared to add-in video cards.

A corrupted CMOS can cause strange behavior: 

Such as: The OS refusing to recognize you have USB 2.0 and runs in USB 1x mode. And possibly HDD corruption for no apparent reason.

---

### Post by compu73rg33k on 2010-04-29
> **P4man said:**
> well, perhaps the dmesg log would nice too.



 that is interesting and could be a  good lead I think. The external drive is USB I assume? Does the problem also occur with the external drive disconnected? Can you try "stress testing" windows by copying large files back and forth on the internal drive ( I realize its a new drive, but it could be the cable or controller as well).
Hmm yeah perhaps the harddrive controller is bad.

Also I just installed windows 7 32-bit and 64-bit and both versions failed to install the nvidia graphics driver. I got an error message that my hardware wasn't compatible with the setup even though I download the Geforce 6 series driver for my Geforce 6100.

I'm starting to think I just need a new computer. Had this one for 3 years now. Seems like **** just ain't workin anymore.

---

