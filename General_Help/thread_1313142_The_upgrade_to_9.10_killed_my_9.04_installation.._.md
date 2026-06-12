---
title: "The upgrade to 9.10 killed my 9.04 installation..  Thanks alot"
date: 2009-11-03
forum: General Help
---

### Post by duckdown on 2009-11-03
Well isn't this just lovely, I had a perfectly lovely working 9.04 installation on my HTPC and because the god damn "Upgrade Notice" kept popping up telling me to upgrade to 9.10, I listened.

Well, it did its whole routine and now upon reboot when my system boots up, the welcome CONSOLE login screen is flickering 100 miles a minute as if someone is holding down a button on the keyboard.

I ssh'ed into the machine and noticed the load was through the roof, and it was because of "dbus-daemon"

so I do a killall -9 dbus-daemon and the rapid flickering stops, however the USB bluetooth keyboard (Logitech DiNovo Edge) doesn't work, and neither does my X windows.

So I re-download the newest NVIDIA driver package from nvidia.com and remake the kernel module by running the installer and it complains about missing vdpau.h in my /usr/lib and a few other things, which its' never done before.  Overall, it installs though, and I reboot and now I at least see my desktop, but the bluetooth keyboard still wont work so I can't control the PC.

What the hell is going on?  Why would you be telling people to upgrade to something so unstable?
I am a novice user and don't know what the hell to do, but I can assure you I CHANGED NOTHING

Can somebody please help?  I can't even control my PC anymore now with my Logitech USB bluetooth keyboard...  This is an absolute disaster..  I'm never upgrading Ubuntu again because seriously they have done a terrible job of not breaking stuff

Thanks in advance for any help , I need responses ASAP because my computer is unusable!!

---

### Post by Zoot7 on 2009-11-03
Honestly you're a lot better off you do a clean install, and if I were you that's the route I'd take now. :( 
The upgrades seem to be rife with problems at the moment. There's always problems around directly after the release date, you're better off waiting off for 3-5 weeks after the release, and doing a clean install. I too found out the Hard way when Hardy -> Intrepid was a disaster on Intrepid's release day this time last year.

Just so you know you can tell it to ignore upgrades by going to
System -> Administration -> Software Sources and selecting "Never" for Release Upgrades under the updates tab.
Also a nifty thing to do is to put your /home on a separate partition so you keep all your Documents and Settings if you want to re-install the OS.
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by snowpine on 2009-11-03
Hi Duckdown, this happens every six months... spend some time on these forums and you'll see! :)

I recommend reinstalling 9.04 (since that was working well for you) and wait a month or two for the dust to settle on 9.10, then do a clean install. Canonical will support 9.04 through October 2010, so there is no rush to upgrade.

---

### Post by Tahakki on 2009-11-03
I thought Intrepid was bad, but the Koala seems to be the worst distro yet.

Wait the usual month.

---

### Post by abickerton on 2009-11-03
> **Zoot7 said:**
> Honestly you're a lot better off you do a clean install, and if I were you that's the route I'd take now. :( 

Are you seriously suggesting endusers WIPE and re-install everytime a new release is out ? :-?

1995 called... they want their crappy installs back, One wonders just how this got through the test cycle.

I too had a disaster updating from Jaunty... 

A larger number of packages just failed to install and my lovely gdm theme gone...  Now I have a user selection that looks hideous and have an extremely unstable environment. GTK seems to be most badly affected so far.

---

### Post by snowpine on 2009-11-03
> **abickerton said:**
> Are you seriously suggesting endusers WIPE and re-install everytime a new release is out ? :-?


Yes; that is the official recommendation (as well as mine personally) for a smooth and pleasant upgrade experience. 

Putting your /home folder on a separate partition allows you to easily perform a fresh install every 6 months, while still keeping your documents and user settings.

If you are concerned 9.10 might not be ready for your hardware, you can set up a "dual boot" between 9.04 and 9.10, use both for a while until you're confident to make the transition.

---

### Post by whoop on 2009-11-03
> **snowpine said:**
> Yes; that is the official recommendation (as well as mine personally) for a smooth and pleasant upgrade experience...

Official? Proof or it ain't true :lolflag:
If you are serious about this, than this is the one of the most stupid things I have ever heard...
A fresh install every six months (if you want the latest ubuntu stuff), it's ridiculous. Imagine: "Say what boss we need the new LTS 10.04? Sure thing boss, just let me reinstall it on the 150 machines in the office and we will be good to go..." Even some automated installation process would not be the way to go in this scenario, if you ask me. I'm glad I'm not responsible for more than 12 machines then :D

I have never done a fresh install, excluding the incident when my hard-disk failed. Sure, I ran into problems while upgrading (as people also experience with fresh installs) but nothing was unfixable (all well under the time it takes to reinstall).

Linux machines used to have an uptime of 6 months, now they get removed and reinstalled every 6 months ? ;)

I thought allot of people where reinstalling because of a wave of new ubuntu users (who are used to this because of Windows).

"Official"? This just can't be true...

---

### Post by snowpine on 2009-11-03
> **whoop said:**
> Official? Proof or it ain't true :lolflag:
If you are serious about this, than this is the one of the most stupid things I have ever heard...
A fresh install every six months (if you want the latest ubuntu stuff), it's ridiculous. Imagine: "Say what boss we need the new LTS 10.04? Sure thing boss, just let me reinstall it on the 150 machines in the office and we will be good to go..." I'm glad I'm not responsible for more than 12 machines then :D

I have never done a fresh install, excluding the incident when my hard-disk failed. Sure, I ran into problems while upgrading (as people also experience with fresh installs) but nothing was unfixable (all well under the time it takes to reinstall).

Linux machines used to have an uptime of 6 months, now they get removed and reinstalled every 6 months ? ;)

I thought allot of people where reinstalling because of a wave of new ubuntu users (who are used to this because of Windows).

"Official"? This just can't be true...

I felt the same way as you once:

[http://ubuntuforums.org/showthread.php?p=7393205](http://ubuntuforums.org/showthread.php?p=7393205)

Personally, I prefer a "rolling release" model such as Arch, or a truly "stable" distro such as Debian Stable or Red Hat. But Ubuntu is a good compromise between those two extremes, for many users.

I would not use Ubuntu's "normal" releases in an office with 150 workstations. I would stick to the LTS (long term support) releases that come out every 2 years (if I used Ubuntu at all). That's what they're designed for. :)

---

### Post by 3rdalbum on 2009-11-03
What do you mean, 'one wonders how this got through the test cycle'? The people who beta tested, like moi, never saw these sorts of problems. If we had, we would have raised a bug report well before release.

Help us test next time!

---

### Post by duckdown on 2009-11-03
This is a complete nightmare...  This is a perfect example of why the rest of the Windows world doesn't want anything to do with Linux..   Because it's always riddled with problems that shouldn't be there.  Why would they rush out a half assed 9.10 release that severely breaks most things -- and on top of it, reccomend all 9.04 users do a distribution upgrade!  

I guess I'm just gonna wipe out and reinstall 9.04 but this is experience has made me seriously bitter and frankly I can see why people insult Linux after things like this..  Totally unneccessary and would have been avoidable if you weren't in such a rush to put out "something new"..  Windows haters, take your best shot.  But my machine has never been left in shambles after one of their updates.  This thing is bloody unusable now..

Terrible...

Thanks anyways for the responses guys..  This is way above a novice users head as far as being able to fix it goes..

---

### Post by whoop on 2009-11-03
> **snowpine said:**
> 
I would not use Ubuntu's "normal" releases in an office with 150 workstations. I would stick to the LTS (long term support) releases that come out every 2 years (if I used Ubuntu at all). That's what they're designed for. :)

Yep, I know that's why I stated LTS 10.04 in my fictional scenario :D

Was it because of what Sef said in the thread you posted, that you see a clean install as a recommendation?:
*"A clean install is recommended for installing. However, it wipes your your system settings."*
If yes, I can understand. But I, still, hope he didn't mean it as strictly as we are interpreting it now (I'll see if I can ask him in the thread :D).

I do agree that a fresh install is more likely to have zero flaws than an upgrade (as there is less that can go wrong). However this does not make it a "better" upgrade path, let alone a "recommended" upgrade path. In practice neither have zero flaws and upgrading is allot easier if nothing does go wrong...

---

### Post by wildweathel on 2009-11-03
The issue is that we need to do more testing of upgrades.  We test livecds, why not upgrades in at least a virtual environment.

*mea culpa*. *nostra culpa. mea et nostra maxima culpa.*

[https://wiki.ubuntu.com/QATeam/Specs/DistributionUpgradeTesting](https://wiki.ubuntu.com/QATeam/Specs/DistributionUpgradeTesting)

I've decided to make standardized testing--both from CD and upgrade--my personal first-priority goal during the Lucid cycle.  I've got the hardware and software for it (virtualization is da bomb) and it looks like an area that needs more love.  Let's not let a lack of automation get in the way of doing at least some testing, cuz the current situation causes way too much pain for novice users.

---

### Post by LoneWolfJack on 2009-11-03
> But my machine has never been left in shambles after one of their updates.

I NEVER had one of my Windows upgrades (Win98->WinMe, Win98->Win2k, etc.) work. They always wrecked my system. In fact, even the regular patches tend to break your install. For that reason, I never trusted that Ubuntu upgrade button.

I'd always do a complete reinstall... thanks to the great partition manager that's integrated into the installer you can put the new release into its own partition and move over the stuff you need as you need it (remember to pull a backup... you never know) from the old install.

I agree, though, that there shouldn't be an option to upgrade your system if it's not 99,99% safe. Get rid of it or make it a link to where people can download the latest release for a clean install. Just my opinion.

---

### Post by 3rdalbum on 2009-11-03
> **LoneWolfJack said:**
> I agree, though, that there shouldn't be an option to upgrade your system if it's not 99,99% safe. Get rid of it or make it a link to where people can download the latest release for a clean install. Just my opinion.

I've never had a dist-upgrade from release to release go belly-up - I've done it five times. I once had to remove a graphics card driver and then reinstall it, but that was due to a known problem with Envy at the time.

The only dist-upgrade that's caused me problems is when I tried to go from 9.04 to Karmic alpha 4; that was a shambles, but then I'm not surprised.

---

### Post by whoop on 2009-11-03
> **LoneWolfJack said:**
> I NEVER had one of my Windows upgrades (Win98->WinMe, Win98->Win2k, etc.) work. They always wrecked my system.

Exact same experience for me. However I never had this with linux. Technically there is more that can go wrong with an actual upgrade (also with linux), nothing was unfixable with linux for me though.
Furthermore, windows tended to slow down for me over time, I don't experience this with linux, even after countless upgrades, as I never fresh install...

---

### Post by LoneWolfJack on 2009-11-03
Well, I guess all upgrades are tested so they work fine with a standard install of the earlier release. Maybe this even could be considered 99,99% safe.

However, there's no way you can test the upgrade with every combination of installed software or custom system tweaks. So basically, one of the great things about linux, the ability to customize everything, is also a great hindrance for seamless upgrades.

Maybe there should at least be a warning to the user that upgrading isn't advised for a system that's heavily customized. Currently, the "upgrade" button is probably too tempting for newbies.

---

### Post by Zoot7 on 2009-11-04
> **abickerton said:**
> Are you seriously suggesting endusers WIPE and re-install everytime a new release is out ? :-?
Yes I am, and loads of others suggest the exact same thing. It's true of every OS. There's quite a few problems with the Windows 7 upgrades too, and the Vista to XP upgrades were a disaster too.
If you feel like that you'd probably be best skip every second release and only do a clean install about a month after the release. There's no real need to upgrade to Karmic if Jaunty is working fine for you, after all it's still maintained with updates for another year or so, is it not?

> **duckdown said:**
> This is a complete nightmare...  This is a perfect example of why the rest of the Windows world doesn't want anything to do with Linux..   Because it's always riddled with problems that shouldn't be there.  Why would they rush out a half assed 9.10 release that severely breaks most things -- and on top of it, reccomend all 9.04 users do a distribution upgrade!  
I really do like Ubuntu, but I won't deny that it's not ready until 3-5 weeks after the release date. I'm of the opinion that the 6 months is too aggressive a release cycle, if it was dialed back maybe to once per year things would be a lot more stable when the release gets out the gate. 
But you do pay a price for being on the bleeding edge of things. If you wanted a good rock solid OS that works good, you'd be best go for the LTS releases. Hardy is pretty solid right about now, granted it's getting a little long in the tooth, but it's still solid.

Sorry to hear your upgrade experience was a disaster, but don't give up on Ubuntu or Linux in general. It's worth it in the long run. ;)

---

### Post by abickerton on 2009-11-04
I should have qualified what I said, I was a bit harsh previously. The computer with the issues has been dist-upgrading since Dapper. I had done a fresh install of Karmic beta the previous week, so was fairly confident It would be alright. For a list of problems see the install experiences thread.

I've never had an upgrade go this badly before, so it has left a bitter taste. The problems experienced are also WAY over what an average Joe might be expected to handle.

I think there's one thing many of us forget. NORMAL PEOPLE ONLY HAVE ONE COMPUTER! Just because the people on here generally have many and can fall back to another when it goes belly up, does not make breaking the OS  acceptable. If I wanted that kind of thing, I'd run Gentoo ;).

---

### Post by ColdFFF on 2009-11-04
> **wildweathel said:**
> The issue is that we need to do more testing of upgrades.  We test livecds, why not upgrades in at least a virtual environment.


I tested karmic from livecd, clean install and upgrade. Infact, our company even decided to use the beta on our office machines because they felt it was that stable.

Unfortunately, although there are a lot of people who take part in testing, not all hardware will be tested. I personally think that ***more*** people should take part by installing a test release next to a stable, as it will help iron out things like this.

> **Zoot7 said:**
> Just so you know you can tell it to ignore upgrades by going to
System -> Administration -> Software Sources and selecting "Never" for Release Upgrades under the updates tab.
I thought this was the default behavior, but if not, maybe it should be?

---

### Post by Zoot7 on 2009-11-04
> **abickerton said:**
> I should have qualified what I said, I was a bit harsh previously. The computer with the issues has been dist-upgrading since Dapper. I had done a fresh install of Karmic beta the previous week, so was fairly confident It would be alright. For a list of problems see the install experiences thread.

I've never had an upgrade go this badly before, so it has left a bitter taste. The problems experienced are also WAY over what an average Joe might be expected to handle.

I think there's one thing many of us forget. NORMAL PEOPLE ONLY HAVE ONE COMPUTER! Just because the people on here generally have many and can fall back to another when it goes belly up, does not make breaking the OS  acceptable. If I wanted that kind of thing, I'd run Gentoo ;).
Can't disagree with you there. Even for me (and I put up with a bit of breakage, it's the price I pay for being on the latest release all the time) there comes a time when I just want my machine to *just* work whenever I want to use it.

> **ColdFFF said:**
> I thought this was the default behavior, but if not, maybe it should be?
Yes. Agreed it should be, there also should be a good big warning dialogue pop up when the update option is selected recommending a clean install.

---

### Post by moonport on 2009-11-04
I agree with whoop. A fresh install every six months is a ridiculous solution.
Imagine that a worker must renew his tools every time that appears a new one. I'm a developer. A computer and it's OS are my tools, not a hobby.
Koala is a nightmare.

---

### Post by leonhook on 2009-11-04
its seems funny because i upgraded from jaunty to karmic on release day and my installation was fine, no problems what so ever.

i then done a fresh install so i could have ext 4 and grub2 and still no problems with it at all. i think some problems must be peoples machines or tweaks.

---

### Post by alienclone on 2009-11-04
> **leonhook said:**
> its seems funny because i upgraded from jaunty to karmic on release day and my installation was fine, no problems what so ever.

i then done a fresh install so i could have ext 4 and grub2 and still no problems with it at all. i think some problems must be peoples machines or tweaks.

exactly, these ppl "tweak" their machines for 6 months but dont realize that most of these changes they make are NOT supported by Canonical, therefore the upgrade breaks it and they dont remember how to make those changes again.

> **duckdown said:**
> This is a complete nightmare...  This is a perfect example of why the rest of the Windows world doesn't want anything to do with** [COLOR=Red]Linux[/COLOR]**..   Because it's always riddled with problems that shouldn't be there.  [COLOR=Red]**Why would they rush out a half assed 9.10 release that severely breaks most things -- and on top of it, reccomend all 9.04 users do a distribution upgrade!  **[/COLOR]

I guess I'm just gonna wipe out and reinstall 9.04 but this is experience has made me seriously bitter and frankly I can see why people insult [COLOR=Red]**Linux**[/COLOR] after things like this..  Totally unneccessary and would have been avoidable [COLOR=Red]**if you weren't in such a rush to put out "something new"**[/COLOR]..  Windows haters, take your best shot.  But my machine has never been left in shambles after one of their [COLOR=Red]**updates.  This thing is bloody unusable now..**[/COLOR]

Terrible...

Thanks anyways for the responses guys..  This is way above a novice users head as far as being able to fix it goes..

dont confuse Ubuntu with Linux, dont confuse UPDATES with UPGRADES, nothing on my machine broke because of my UPGRADE from 9.04 to 9.10 on my TEST PARTITION THAT IS SEPERATE FROM MY MAIN USE PARTITION, and nothing forced me to UPGRADE, stick with a version that works if it is still being supported like an LTS or even 9.04 which is supported until like oct 2010 or something. they are in a "rush" to put out something new so that it can be tested, if you want to wait 10 yrs between upgrades pay for Windows,
Ubuntu is FREE to use, you ppl need to stop bitching, ingratefull bastards.
i hardly consider a temperarily non working bluetooth keyboard "(machine)is bloody unusable now", plug in a regular keyboard and try to find the problem.

> **moonport said:**
> I agree with whoop. A fresh install every six months is a ridiculous solution.
Imagine that a worker must renew his tools every time that appears a new one. I'm a developer. A computer and it's OS are my tools, not a hobby.
Koala is a nightmare.

if a worker buys a set of tools, and then a "possibly better" set is for sale 6 months later, he has the CHOICE!!!!!! to buy the new set, he is NOT FORCED!!!!, or he can just STAY with the set he already has if they do the job.

you ppl rush out for the "latest and greatest" head first with blindfolds on and then cry to mommy when you hurt yourselves.



IF WHAT YOU HAVE NOW WORKS, THEN STAY WITH IT,
if you want Ubuntu to be better then participate in testing, which in my opinion, using a cost FREE os is considered testing, and the user/tester should feel PRIVILAGED, if not then they should pay for Windows since they "never had a problem" with it, even tho all they do in their previous threads is bash it. 

sorry for the rant.

---

### Post by duckdown on 2009-11-04
I hardly call the destruction of my system "linux bashing" or "bitching"..  Nice troll post though.  And the bluetooth keyboard was the tip of the iceberg.  How about the dbus-daemon issue?  How about my Xserver problems now?

Way to ignore the key points and just spew a bunch of insulting useless garbage nobody cares about..

---

