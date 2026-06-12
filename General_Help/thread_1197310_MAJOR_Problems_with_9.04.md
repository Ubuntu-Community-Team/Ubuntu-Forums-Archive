---
title: "MAJOR Problems with 9.04"
date: 2009-06-26
forum: General Help
---

### Post by A-bot on 2009-06-26
I've been using Ubuntu 9.04 for about 1 and a half months now, and have noticed some HUGE, MAJOR problems. Here is a list of them:

1) Sound: When I play music, with the volume turned up to 80-100%, the speakers make a terrible crackly noise along with the music. The only way to rid of it is to turn the volume down, and sometimes THAT doesn't work.

2) Booting up: When the computer starts into the Splash Screen, I have to hold down a key for the bar to advance any

3) Flash: Flash is SUPER slow when trying to play a game online

4) When I turn off or boot up, the screen goes CRAZY with lines and different colors before loading the splash screen

5) Compatibility: Many programs don't work with Ubuntu, or even WINE on that note.

6) I can't hibernate/sleep/etc with out Ubuntu locking up and not letting me restore the state (meaning that it's shut down, or nothing)

Am I the only one experiencing these issues? 

~Adam

---

### Post by earthpigg on 2009-06-26
which of these problems also occur when running ubuntu from a live cd?

(you can sudo-apt get install ubuntu-restricted-extras from the live CD to test flash and whatnot.)

---

### Post by merlinus on 2009-06-26
Some of these seem related to your video card.  Are you using the latest drivers?

As to programs, which ones?  This ain't windows, thank goodness!!!

---

### Post by A-bot on 2009-06-26
@Earthpig: I haven't tried the LiveCD yet - will do that soon
@merlinus: Drivers are all up-to-date. Programs:

Sound: All
Flash: Firefox, e.g games, etc

---

### Post by loomsen on 2009-06-26
Quite a while ago, I left right when the official version was released after the most horrible "testing" phase I've ever been through.

Horrible release, horrible choice to backport the (milestone) 2.6.29 kernel to 2.6.28 (which really wasn't much of a gain, if no loss)

Discussed this ever since the whole lot of "features" | sed s/features/failures/g were published.

For me it was:
1) Reintroduced HighLoadCycleCount/LoadRetryCount bug
2) Ext4 is the worst FS I've tried so far, causing lock ups and high CPU temperature --> Lockups during some more CPU demanding compiles - lockups meaning my Laptop just switched off after like 1-2 hrs compiling. 
You can imagine how a system looks like if such stuff happens during the installation process...
3) CONFIG_IPv6=Y ... brainless
4) no KMS implementation (not even trying, they even announced it won't get into Karmic neither)
5) thus no plymouth (I'm _NOT_ a usplash freak... but I love working in the shell. Being able to see like 15 lines compared to a whole manual IS a difference. 
6) BTRFS is running as stable as Ext3 for me, Ext4 never got even into the same direction. I didn't lose _ANY_ data so far with btrfs, converted ext4 to btrfs, fscked my active root partition, defraged/reallocated some of my stuff which was like stuck somewhere in between my drive, created a snapshot of a running live system with one click, changed one line in the snapshots fstab and used it without any problems.
Btrfs is some massive improvement, even if it's still considered unstable (3 kerneloops so far for me, but no lockup. Just a trace message, still could start and close apps)

Guess these are the MAIN issues why I left, and I don't regret anything. GNOME is GNOME after all, differences only get obvious when it comes down to CLI package management. But half a day (or an alias file definition later) and everything was almost like before.

Only good thing, well, I gotta admit that, are the improvements regarding the font rendering / hinting in JJ. Kinda miss that, but well... Successfully built the notify-osd pkg for fedora yesterday, so the fonts specs should work too if I find some time and boredom.

As much as I love debian, JJ made me switch from Ubuntu to Fedora as my primary OS. Got another SuSe and a debian sid/sidux installed, and a debian squeeze I used to test some btrfs features. Bummer canonical refuses development, and rather works on undoing the development and destroying the work done by the kernel devels.

So, yep, you're right, JJ sux :D Fortunately there are enough dists around, if you know what you're looking for only one bootstrap away :)

---

### Post by A-bot on 2009-06-26
> **loomsen said:**
> Quite a while ago, I left right when the official version was released after the most horrible "testing" phase I've ever been through.

Horrible release, horrible choice to backport the (milestone) 2.6.29 kernel to 2.6.28 (which really wasn't much of a gain, if no loss)

Discussed this ever since the whole lot of "features" | sed s/features/failures/g were published.

For me it was:
1) Reintroduced HighLoadCycleCount/LoadRetryCount bug
2) Ext4 is the worst FS I've tried so far, causing lock ups and high CPU temperature --> Lockups during some more CPU demanding compiles - lockups meaning my Laptop just switched off after like 1-2 hrs compiling. 
You can imagine how a system looks like if such stuff happens during the installation process...
3) CONFIG_IPv6=Y ... brainless
4) no KMS implementation (not even trying, they even announced it won't get into Karmic neither)
5) thus no plymouth (I'm _NOT_ a usplash freak... but I love working in the shell. Being able to see like 15 lines compared to a whole manual IS a difference. 
6) BTRFS is running as stable as Ext3 for me, Ext4 never got even into the same direction. I didn't lose _ANY_ data so far with btrfs, converted ext4 to btrfs, fscked my active root partition, defraged/reallocated some of my stuff which was like stuck somewhere in between my drive, created a snapshot of a running live system with one click, changed one line in the snapshots fstab and used it without any problems.
Btrfs is some massive improvement, even if it's still considered unstable (3 kerneloops so far for me, but no lockup. Just a trace message, still could start and close apps)

Guess these are the MAIN issues why I left, and I don't regret anything. GNOME is GNOME after all, differences only get obvious when it comes down to CLI package management. But half a day (or an alias file definition later) and everything was almost like before.

Only good thing, well, I gotta admit that, are the improvements regarding the font rendering / hinting in JJ. Kinda miss that, but well... Successfully built the notify-osd pkg for fedora yesterday, so the fonts specs should work too if I find some time and boredom.

As much as I love debian, JJ made me switch from Ubuntu to Fedora as my primary OS. Got another SuSe and a debian sid/sidux installed, and a debian squeeze I used to test some btrfs features. Bummer canonical refuses development, and rather works on undoing the development and destroying the work done by the kernel devels.

So, yep, you're right, JJ sux :D Fortunately there are enough dists around, if you know what you're looking for only one bootstrap away :)

Thanks for the...help?

---

### Post by QIII on 2009-06-26
My first comment is:  No you are not the only one experiencing problems, but the vast majority of people are experiencing very few problems.  I've had very few, and they were all solved by work-arounds for my ATI video driver on one machine.  I've had no problems at all on two other machines.  (Until I started testing Karmic on one of them, but it's not a release yet, so you expect bugs . . . which is the whole point of testing.)

My first questions are:  When you burned your .iso image to disk, how fast did your burner go?  Did you do an integrity check (which you can do from the LiveCD?  Did you do an md5sum?  Did you encounter similar problems if you previously had another OS on the machine?

Would you please post your system specs?

So, to your items.

1) Sound: When I play music, with the volume turned up to 80-100%, the speakers make a terrible crackly noise along with the music. The only way to rid of it is to turn the volume down, and sometimes THAT doesn't work.

Are you overdriving the speakers?  If, instead of turning them down, you turn them off and then back on, does the problem persist?

2) Booting up: When the computer starts into the Splash Screen, I have to hold down a key for the bar to advance any

Hmmmm.  Don't know.  Strange.

3) Flash: Flash is SUPER slow when trying to play a game online

Run top from the terminal when you encounter this behavior.  Post the results.

4) When I turn off or boot up, the screen goes CRAZY with lines and different colors before loading the splash screen

If you are talking about the silly oval of splashy colors that appears around the status bar just before you get to the login screen, that's just the way it is.  Some developer may have thought it was cool. 

If you are talking about the period between when you select boot in GRUB and when the splash screen opens, I would suspect hardware.

5) Compatibility: Many programs don't work with Ubuntu, or even WINE on that note.

Which programs?  How are you installing them?  From Synaptic or the terminal?

6) I can't hibernate/sleep/etc with out Ubuntu locking up and not letting me restore the state (meaning that it's shut down, or nothing)

Is your swap at least the same size or larger than the amount of RAM you have on board?  RAM state is stored in your swap on hibernate.  Windows does the same thing -- it stores state on the drive to cut down on power to the RAM.  If your swap is smaller than the amount of RAM, you get a mangled, incomplete and corrupt "image" of the RAM state.

---

### Post by loomsen on 2009-06-26
Check your authentication settings...
System->Administration->authentications

I have interfaces for HAL and Devicekit, and for each have to grant permissions if I want to use suspend/hibernate.

---

### Post by skathmandoo on 2009-06-26
I'm having a lot of problems with 9.04 as well. i just upgrade from 8.04. everything was workin fine before the upgrade tho. the problems i'm having after the upgrade are :

1. Vuze doesnt work.
2. Flash players like megavideo doesnt work. Youtube and veoh works fine and
3. It freezes quite often nowdays.
 
thats all i have noticed till now.m starting to regret upgrading. can i downgrade? how do i do it? thanks

i forgot to mention , when streaming videos from youtube and stuffs , if its in fullscreen it keeps ..lagging or slowing (i dont know wat its called) but u get the idea..its like gettin stuck every few seconds. but this is only when its in fullscreen. any ideas?

---

### Post by muteXe on 2009-06-26
8.04 for the win. Really.

---

### Post by wpshooter on 2009-06-26
> **loomsen said:**
> Quite a while ago, I left right when the official version was released after the most horrible "testing" phase I've ever been through.

Horrible release, horrible choice to backport the (milestone) 2.6.29 kernel to 2.6.28 (which really wasn't much of a gain, if no loss)

Discussed this ever since the whole lot of "features" | sed s/features/failures/g were published.

For me it was:
1) Reintroduced HighLoadCycleCount/LoadRetryCount bug
2) Ext4 is the worst FS I've tried so far, causing lock ups and high CPU temperature --> Lockups during some more CPU demanding compiles - lockups meaning my Laptop just switched off after like 1-2 hrs compiling. 
You can imagine how a system looks like if such stuff happens during the installation process...
3) CONFIG_IPv6=Y ... brainless
4) no KMS implementation (not even trying, they even announced it won't get into Karmic neither)
5) thus no plymouth (I'm _NOT_ a usplash freak... but I love working in the shell. Being able to see like 15 lines compared to a whole manual IS a difference. 
6) BTRFS is running as stable as Ext3 for me, Ext4 never got even into the same direction. I didn't lose _ANY_ data so far with btrfs, converted ext4 to btrfs, fscked my active root partition, defraged/reallocated some of my stuff which was like stuck somewhere in between my drive, created a snapshot of a running live system with one click, changed one line in the snapshots fstab and used it without any problems.
Btrfs is some massive improvement, even if it's still considered unstable (3 kerneloops so far for me, but no lockup. Just a trace message, still could start and close apps)

Guess these are the MAIN issues why I left, and I don't regret anything. GNOME is GNOME after all, differences only get obvious when it comes down to CLI package management. But half a day (or an alias file definition later) and everything was almost like before.

Only good thing, well, I gotta admit that, are the improvements regarding the font rendering / hinting in JJ. Kinda miss that, but well... Successfully built the notify-osd pkg for fedora yesterday, so the fonts specs should work too if I find some time and boredom.

As much as I love debian, JJ made me switch from Ubuntu to Fedora as my primary OS. Got another SuSe and a debian sid/sidux installed, and a debian squeeze I used to test some btrfs features. Bummer canonical refuses development, and rather works on undoing the development and destroying the work done by the kernel devels.

So, yep, you're right, JJ sux :D Fortunately there are enough dists around, if you know what you're looking for only one bootstrap away :)

And what was it that you do in your spare time ???

---

### Post by decoherence on 2009-06-26
For those reporting problems... you have not included enough information for anyone to do more than guess at what the causes might be. If you want help on these issues, I suggest starting a new thread for each one so that people familiar with that part of the system can get the appropriate information from you.

Trying to do it all in one thread, with multiple posters posting multiple problems, will get very messy and will be inconvenient for anyone else looking for help on one of these subjects.

Unless this actually belongs in "testimonials" ... some of the replies do, anyway.

---

### Post by loomsen on 2009-06-26
[quote="wpshooter"]And what was it that you do in your spare time ?[/quote]

Why, wanna ask me out?

[quote="decoherence"]what the causes might be[/quote]

Most of them, if not all, have been discussed a lot during the testing time. Archive ftw.

---

### Post by VastOne on 2009-06-26
> **loomsen said:**
> Why, wanna ask me out?



Most of them, if not all, have been discussed a lot during the testing time. Archive ftw.

:twisted:

Seriously...Loomsmen, what do you point at the most as the culprit of these issues in JJ? I say it is the kernel and the cpu and not living in the same house or county or country.

---

### Post by loomsen on 2009-06-26
> **VastOne said:**
> :twisted:

Seriously...Loomsmen, what do you point at the most as the culprit of these issues in JJ? I say it is the kernel and the cpu and not living in the same house or county or country.

<<SERIOUSLY
Jaunty is a farce. 
_IMHO_ canonical obviously intends to focus on their purpose.

ubuntu.COM it is. Commercial. With all its annoying disadvantages which occur due to mass compatibility (or better, mass shut-the-foo-up-ity)

No other explanation for such behavior. 
2.6.28 was a not 2 important release, neither did it implement a lot of new features. 
2.6.29 however did. And these are elementary features which completely reset the users possibilities. DKMS and btr alone are reason enough to work on implementing it. 

DKMS provides a DRI for i915 cards, a card which is part of many many notebooks, especially single core ones. So, this is a point I will never ever understand. Why putting effort in destroying other peoples work? Many n00bs just switching from PropOS are likely to install ubuntu on their notebook first, like my roommate for instance did as well. Vista64 on his Desktop and a rock solid (yet old) Hardy on his notebook. 
Now, most users aren't able to trace bugs/errors/whatever themselves. Considering that Y instead of M regarding ipv6 is hillarious. 
Why not putting a little more effort on stabilizing the experimental modules? 
Just typical, profit-oriented, hypocritic freeloading, again, _IMHO_
And by denying to at least ship DKMS with GG they basically took their year off, waiting for the more critical modules to be stabilized by others.
Lame 1. But more important is still what I wrote above. Mass compatibility and individiual needs seldom go hand in hand.

Guess they are afraid that this forum would just explode due to 
HELP I INSTALLED BTRFS (--ignoring manuals, tips, howtos and warnings-- editors note) AND NOW I CANT BOOT ANYMORE !!11!!!!oneoneoneeleventwelve
posts. This is a reasonable and probable scenario, you have to be able to trace bugs yourself if you decide to try experimentals, but _I_ want to choose.
Somehow ubuntu just got 2 bloated for me, I don't need most of the stuff it ships with anyway, so for my very own package selection (which is pretty much the same no matter which dist) I don't feel any difference between debian, sidux, ubuntu or any other debian based dist. 
As I said, I love debian, but I'm also glad to be on fedora now.
I'll see how debian handles btrfs the next couple of days...
YLSUOIRES

---

### Post by A-bot on 2009-06-28
Is anyone actually able to **help** me instead of posting their own problems?

---

### Post by Laysan_A on 2009-06-28
@A-bot

I'll tell you one thing that would help (maybe two?). Put your system specs in your sig. so people will at least have a small idea what you're using. Including some info about your install - have you modified it in any substantial way (or not) - might be important, too. Also, have you noticed anything that looks suspicious in your sys.log, kernel.log, xorg.log or dmsg.log? If so, you should post it (or maybe mention that if anyone wants to see them to let you know).

I'm very new at this whole debugging thing, so I'm afraid I won't be of any real help. I've seen a number of folks with problems similar to yours (minus the boot-colors thing). I experienced system sluggishness and high cpu use when I compiled a .29-5 kernel, and after I had had to rebuild my xserver stuff. I don't know what it was, exactly, but assume it was unmet dependencies, modules that should have been installed but weren't, that kind of thing. The problems surrounding x were solved by *sudo apt-get -f* to fix unmet dependencies. You might give that a shot, if you haven't already.

Good luck.

---

### Post by A-bot on 2009-06-29
> **Laysan_A said:**
> @A-bot

I'll tell you one thing that would help (maybe two?). Put your system specs in your sig. so people will at least have a small idea what you're using. Including some info about your install - have you modified it in any substantial way (or not) - might be important, too. Also, have you noticed anything that looks suspicious in your sys.log, kernel.log, xorg.log or dmsg.log? If so, you should post it (or maybe mention that if anyone wants to see them to let you know).

I'm very new at this whole debugging thing, so I'm afraid I won't be of any real help. I've seen a number of folks with problems similar to yours (minus the boot-colors thing). I experienced system sluggishness and high cpu use when I compiled a .29-5 kernel, and after I had had to rebuild my xserver stuff. I don't know what it was, exactly, but assume it was unmet dependencies, modules that should have been installed but weren't, that kind of thing. The problems surrounding x were solved by *sudo apt-get -f* to fix unmet dependencies. You might give that a shot, if you haven't already.

Good luck.

I will post my system information here, and then in my signature later

HP Pavilion DV9720us
Running Ubuntu 9.04, Jaunty Jackalope
17" Screen, 1440x900
Nvidia Graphics
Altec Lansing Sound
2 GB of a Ram, AMD turion dual core processor
250GB Hard Drive

Need any more? Tell me and I'll get it up.

---

### Post by Laysan_A on 2009-06-29
Hi A-bot,

There's a thread entitled something like "Known Bugs in Jaunty". Check there for your issues. I think I recall seeing something about crackling audio...

Are you using the 64bit flash straight from Adobe - not the flash from the restricted repo? If not check this thread out. It may help. 
[http://ubuntuforums.org/showthread.php?t=985479](http://ubuntuforums.org/showthread.php?t=985479)

I've noticed a number of folks having probs. with hibernation. Someone said that if your swap is not larger than your available ram your hibernation will corrupt and fail. Beyond that, I don't know (I haven't used it myself yet).

To the issue of program compatibility, well, that's rather a large statement, isn't it? It's like saying "Life isn't perfect". What's anyone supposed to do with that. If you're having problems with a specific program(s) post a separate thread describing what's going on. 

Oh, and don't forget to search - the forum and the web. Someone may have solved your issue already.

---

### Post by A-bot on 2009-06-29
@ Laysan_A:

Can you link me to the "Known Bugs" thread?

I'm not sure if I'm using the 64 bit - how can I check?

It's not only hibernation - it's suspending it, too

---

### Post by Laysan_A on 2009-06-29
Okay, just go to Main Support Categories > General Help (top of the page). It's the first sticky.

If you don't know that you have the 64bit flash then you don't. You have to install it yourself. It isn't in the repositories (at least it wasn't). Check the thread I already gave you. It has all the info you'll need. It works great on my machine (you still can't use the Move Player though).

> It's not only hibernation - it's suspending it, too

Sorry, can't help you...search the forums and the web (this isn't the only place hosting (k)ubuntu issues).

---

### Post by A-bot on 2009-06-30
I've checked the topic and did not see anything about any of the problems I'm experiencing in there.

---

### Post by raafaell on 2009-06-30
Ubuntu Jaunty works perfect to me!

---

### Post by Laysan_A on 2009-07-01
Well, what you need to do is take each of your problems, one by one. First do a search, both here and on the web. Try to be specific, for instance include the name of your sound device and a short description of your symptoms, but don't be afraid to get more general, or to just try different combinations of terms, if your searches don't return much. Error messages can be very fruitful search terms, if you get one.

Sometimes it can be helpful to check for open bugs in launchpad. It might already be a known bug with someone working on it. There may already even be a fix that just hasn't hit the repos yet. 

If you don't find the answers you need in previous posts, then post your own question/difficulty and hopefully you'll get it worked out. But take each issue separately (one post for each - in the proper forum). 

Good luck A-bot!

---

### Post by UranUtan on 2009-07-01
Did you upgraded to 9.04 or installed it from scratch? I had graphic and sound troubles after upgrading, time consiming fixes and updates, etc. and finally the best fix was to re-install 9.04 instead of upgrading.

Good lucks.

---

### Post by A-bot on 2009-07-01
9.04 was my first time using Ubuntu, so no, I didn't upgrade from previous versions of Ubuntu.

---

### Post by Laysan_A on 2009-07-02
@A-bot

Did you find this thread for your sound issues?

[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

---

### Post by A-bot on 2009-07-07
My sound issues seem to have gone away, which is great. Only a few problems left.

---

### Post by moster on 2009-07-07
6) I can't hibernate/sleep/etc with out Ubuntu locking up and not letting me restore the state (meaning that it's shut down, or nothing)

I read kernel hackers deal with that in next kernel 2.6.30. Many people have problems with that and that is one of reasons why I install Ubuntu 9.10 alpha on my laptop. It work perfect now.

edit:
This will not resolve your problem now, but at least you will know what is going on.

---

### Post by A-bot on 2009-07-14
I'm not going to install an unstable version of Ubuntu on my laptop just to fix a sound issue. There's gotta be a way. I'm still having many of these problems...

---

