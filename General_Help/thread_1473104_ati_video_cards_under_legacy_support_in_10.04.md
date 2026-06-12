---
title: "ati video cards under legacy support in 10.04"
date: 2010-05-04
forum: General Help
---

### Post by kid_eh on 2010-05-04
Hi, just wondering if it's at all possible to get hardware acceleration with the ati cards under legacy support. I have an x700 card and the default drivers in 10.04 don't support any visual effects, 3D applications and scrolling through web pages is a little jittery. 

I don't know a lot about open source drivers. Are there any that will let me enable visual effects? or are the default ones as good as it gets?

---

### Post by kid_eh on 2010-05-04
Sorry, I should have specified, web scrolling is alright, but windows are slow to redraw when min/maxed or moved, slow to refresh, it just feels over all sluggish in the video department.

---

### Post by Confused Computer User on 2010-05-06
Same here. I resorted to puling out the card and reverting to the inbuilt video card/chipset (on board memory).

Why?... Why this?

---

### Post by sandyd on 2010-05-06
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

thats all there is.

---

### Post by molar on 2010-05-10
this driver doesn't work on 10.04

---

### Post by geonel on 2010-05-11
With my ATI Radeon 2600, I would often have this problem if I upgraded the kernel. I would then go to amd.com and find a new driver package and load it and do an 'aticonfig --initial=daul-head ....' and everything would be okay. 

I have done that probably about eight times. This time, on 10.04 I haven't had a good outcome. Repaint is unacceptable. 

Sorry I don't have any answers. I just wanted share my experience with the issue you are having.

---

### Post by geonel on 2010-05-11
um, duh. I just removed/deactivated the fglrx driver and reinstalled the 10-4 ati support for good measure (from amd.com) and now everything is good with my graphics. Now to get my bluetooth keyboard working.

---

### Post by Confused Computer User on 2010-05-12
> **geonel said:**
> um, duh. I just removed/deactivated the fglrx driver and reinstalled the 10-4 ati support for good measure (from amd.com) and now everything is good with my graphics. Now to get my bluetooth keyboard working.

Sorry to ask this but could you be ever so kind to give an walk through for a newb on how you did this. My Video card is ATI Radeon X1600. I'd really like to be able to use 10.04 instead of 9.10.

Thanks.

---

### Post by Chrisco66 on 2010-05-14
Try this, it worked for me.  

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

### Post by Confused Computer User on 2010-05-16
> **Chrisco66 said:**
> Try this, it worked for me.  

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

wow...just wow... runs like a well tune engine... 
But two things...

**First** after executing:
sudo apt-get install fglrx fglrx-amdcccle fglrx-dev fglrx-modaliases 

I tried:
sudo aticonfig --initial 

this didn't work, even after a restart.

**Second**, trying out the ATI Catalyst Control Center doesn't work either as it claims I might not have an ATI Graphics Card driver installed. How Do I fix this?

My reason for this is that I wnt to get the efects up and runing... so far I'm stuck at None.

Thanks in advance.

---

### Post by Chrisco66 on 2010-05-16
ok, when I did it, this was the result, as I remember.

sudo apt-get update---ran with no faults

sudo apt-get install fglrx fglrx-amdcccle fglrx-dev fglrx-modaliases ---Also no faults

If you get this message when running the apt-get install command:

Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)---I didnt get the message, so I disregarded the next three lines--

I went right to ---sudo aticonfig --initial and it told me that an applicable card could not be found, or something worded similarly.

I went back and ran the 3 commands one at a time..

sudo apt-get remove fglrx---no faults, then

sudo apt-get install linux-headers-`uname -r`---no faults, then

sudo apt-get install fglrx---no faults

ran sudo aticonfig --initial again, still showed no applicable card installed.

I restarted, and when it came back up, the video was back to its normal speed.

It didnt go exactly like it was spelled out at the link, but pretty close..

Hope this helps..Chrisco

---

### Post by Confused Computer User on 2010-05-17
thank you for the reply Chrisco. But you missed my point. The speed has indeed improved but the visual effects don't work. Videos run smoothly for me and I can even drag a video window with the video running with no issue.

I'm trying to get the eye candy going as well. Have you manage to get it to work?

Also I have attempted the steps you listed as well with no success in terms of effects. Usability has gone up but nothing otherwise.

---

### Post by 3rdalbum on 2010-05-17
@ConfusedComputerUser: The X1600 is not supported by the ATI proprietary driver. I'm surprised that any of the steps listed have actually changed anything on your system for the better, because by rights they should have stopped your card from working at all.

---

### Post by Confused Computer User on 2010-05-17
> **3rdalbum said:**
> @ConfusedComputerUser: The X1600 is not supported by the ATI proprietary driver. I'm surprised that any of the steps listed have actually changed anything on your system for the better, because by rights they should have stopped your card from working at all.


Well they haven't. I can run videos and pretty much move/drag the windows which is much better than what happened when I did the clean install with what I'm guessing were the open drivers. 

So how do I salvage this? Is there a solution? I've posted in other threads and i'm not the only one having issues with older ATI cards. Any suggestions?

---

### Post by Mark Phelps on 2010-05-17
> **Confused Computer User said:**
> So how do I salvage this? Is there a solution? I've posted in other threads and i'm not the only one having issues with older ATI cards. Any suggestions?

Suggestion is to go over to the Phoronix forums and see what they have regarding tips in using the ATI drivers.  They do a LOT of tweaking using both the fglrx drivers and the open source drivers.

---

### Post by Chrisco66 on 2010-05-18
Confused Computer User, I have not played around with effects like compiz, if that's what you are talking about.  Maybe the other post from Mark Phelps is the way to go for now.  Good luck, and keep us informed..

---

### Post by parn on 2010-05-18
I am using ATI X700, compiz effect, cairo-docky (opengl) all running. Ok it is not lightning fast or silk smooth but... it is acceptable.

3D Cube + movie + Magic Lamp effect + bunch of other effects I am running.

What sort of effects are we talk here?

---

### Post by Confused Computer User on 2010-05-18
> **Chrisco66 said:**
> Confused Computer User, I have not played around with effects like compiz, if that's what you are talking about.  Maybe the other post from Mark Phelps is the way to go for now.  Good luck, and keep us informed..

I have followed up on Mark Phelps' suggestion. The problem with that is that half the stuff on the forum went over my head. The other half went way, way over my head.
I'm not a power user nor an experienced programmer (basic java knowledge but not nearly enough). So altering some of the basic files for me is out of the question. I might resort to becoming a member and asking for help but for now I'll wait.

on that note, thanks Mark Phelps for the post.


> **parn said:**
> I am using ATI X700, compiz effect, cairo-docky (opengl) all running. Ok it is not lightning fast or silk smooth but... it is acceptable.

3D Cube + movie + Magic Lamp effect + bunch of other effects I am running.

What sort of effects are we talk here?
Well that's what I was hoping to get as well. the problem in my case is the "acceptable" part.

When I would scroll a web page it felt like it was jammed. It took like 10 seconds to scroll down to the bottom. And mind you that was without seeing the middle of the page. I would see the top and then the bottom.

Another thing, dragging an open window was near impossible. I mean it never worked.

You might think I'm peaky but this is not acceptable for me.:(

Also, thank you for the feed back as well.

---

### Post by kid_eh on 2010-05-19
> **parn said:**
> I am using ATI X700, compiz effect, cairo-docky (opengl) all running. Ok it is not lightning fast or silk smooth but... it is acceptable.

3D Cube + movie + Magic Lamp effect + bunch of other effects I am running.

What sort of effects are we talk here?

That's exactly what I'm looking for! Are you running 10.04? If so, how did you get the effects to work?

---

### Post by Confused Computer User on 2010-05-22
> **kid_eh said:**
> That's exactly what I'm looking for! Are you running 10.04? If so, how did you get the effects to work?

I can tell you that with a fresh install of Ubuntu 10.04, the effects were working for me but they were SLOW (not meant as a scream but as an emphasis)

I found a link that suggests:

> If you find that after upgrading to X.Org 7.3 your display becomes very slow, and you own ATI Radeon, all you need to do is to put this line in the Device section of your xorg.conf:

Option "MigrationHeuristic" "greedy"

After that, your display should return to the normal speed, and X server will stop burning CPU cycles during such simple tasks like moving windows or switching workspaces.

See:
[http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html](http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html)

Now I haven't tried this, and after 10 re-installs I am not willing to try this yet.

---

### Post by ollobollo on 2010-05-31
My ATI Radeon X1950 Pro (RV570) didn't have hardware acceleration in Ubuntu 10.04, but after some searching, I found [this guide](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) on the wiki. I followed **Problem: Need to fully remove -fglrx and reinstall -ati from scratch**, and I had hardware acceleration. It's still not listed in **Hardware Drivers**, but it works fine with Compiz and Diablo II.

---

### Post by Confused Computer User on 2010-06-02
> **ollobollo said:**
> My ATI Radeon X1950 Pro (RV570) didn't have hardware acceleration in Ubuntu 10.04, but after some searching, I found [this guide](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) on the wiki. I followed **Problem: Need to fully remove -fglrx and reinstall -ati from scratch**, and I had hardware acceleration. It's still not listed in **Hardware Drivers**, but it works fine with Compiz and Diablo II.

No go for me. Fresh install of 10.04 with all the updates and this did nothing to help. Thanks though for the post ( I think this was your first)

---

### Post by TBABill on 2010-06-02
Not sure which card this applies to for ATI but I just fixed my driver issues following the SECOND set of steps in this wiki:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by waynefoutz on 2010-06-02
> **Confused Computer User said:**
> No go for me. Fresh install of 10.04 with all the updates and this did nothing to help. Thanks though for the post ( I think this was your first)

This isn't the best solution, but if you are going to run an older ATI GPU, you're going to need an older version of Ubuntu. Try installing Hardy Heron [http://releases.ubuntu.com/hardy/]("http://releases.ubuntu.com/hardy/") and install the proprietary driver it asks you to install, and you'll get it going at peak performance. Another option is Debian Lenny (stable.) [http://www.debian.org/CD/]("http://www.debian.org/CD/") These run an older version of xorg-server. The newer xorg-server doesn't work with ATI's older legacy drivers. Hardy has another year of life in it, Debian will be around for a while as well. The only other option is to replace the hardware.

---

### Post by Confused Computer User on 2010-06-03
> **waynefoutz said:**
> This isn't the best solution, but if you are going to run an older ATI GPU, you're going to need an older version of Ubuntu. Try installing Hardy Heron [http://releases.ubuntu.com/hardy/]("http://releases.ubuntu.com/hardy/") and install the proprietary driver it asks you to install, and you'll get it going at peak performance. Another option is Debian Lenny (stable.) [http://www.debian.org/CD/]("http://www.debian.org/CD/") These run an older version of xorg-server. The newer xorg-server doesn't work with ATI's older legacy drivers. Hardy has another year of life in it, Debian will be around for a while as well. The only other option is to replace the hardware.

Yeah I know. Some one also suggested Mint Linux but I haven't gotten around to that. I've been going back and forth between Hardy and 10.04 but each one has "an issue with me". Hardy doesn't fully shut down, where as 10.04 has this video card problem:popcorn:. 

I'm hoping 10.10 might work better so I'll see how Mint Linux goes, and then switch to 10.10 if it's a better solution.

@TBABill, this solution was already suggested by ollobollo. Thank you for posting. At least it shows I'm not alone in this issue.

---

### Post by Chrisco66 on 2010-06-03
I just reinstalled 9.10 on my laptop.  Its strange that after reinstallation, the video worked fine.  No wireless problems either.  

I dont know why they decided to remove or deactivate all the drivers in 10.04.  

Im looking for a replacement for Ubuntu, all suggestions are welcome..

---

### Post by Confused Computer User on 2010-06-03
> **Chrisco66 said:**
> I just reinstalled 9.10 on my laptop.  Its strange that after reinstallation, the video worked fine.  No wireless problems either.  

I dont know why they decided to remove or deactivate all the drivers in 10.04.  

Im looking for a replacement for Ubuntu, all suggestions are welcome..

Well i gave a few in my previous post.

1. Mint Linux (seems well rounded from what I've read... haven't tried it yet)

2. Kubuntu or Xubuntu (both are good... Xubuntu will work on anything)

3. Fedora (apparently the oldest linux distro)

4. Puppy linux (very light and versatile... I've tried and i like it)

any of these will do well.

I'm aiming to get Mint linux, and if things go well with that I'll stick with it.
Hope this helps.

---

### Post by Chrisco66 on 2010-06-03
I tried mint some time ago.  I assumed since it was based on Ubuntu, all the problems would carry over.  Maybe I should look at it again.

I like Ubuntu, but it continues to cause problems on the laptops/netbooks.  I thought it might be older hardware, but the machine Im on now is a HP, a600n, at least 5 years old, probably more.  I thought it only had problems with wireless, but I have a machine at home that works fine with wpa2 running.  I am just disappointed.  The only probs it has is with "portables".  There was a minor problem with disc burning on my main machine, but it fixed its self.

I also tried pclinux on my "test" box.  It worked good there, but would not install on my laptop.  I guess I want one OS that will work on any computer, without having to chase down fixes for stuff that used to work. 

I guess for now, Ill run 9.10 on the laptops/netbooks, and 10.04 on the desktops.  I will look into alternatives though.  Thanks for the suggestion, I will look at mint and fedora again, puppy is a little "light".

---

### Post by efflandt on 2010-06-03
If all else fails, with default drivers/modules try **nomodeset** kernel boot parameter to use regular video modules instead of the new kernel mode setting (KMS) driver.  I needed to do that to fix video issues on some computers with legacy ATI, and also to fix suspend/hibernate on one PC.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

---

### Post by Chrisco66 on 2010-06-03
efflandt, I might look into that, but they seem to run fine with 9.10.  It just seems to me, that when they list the minimum sytem requirements, maybe they should mention that ATI cards over 3 years old will not work.  Maybe they should also mention that wireless cards that worked perfectly in 9.10, will no longer work.

I really dont mind tweaking a few things, but these are major systems that no longer work.  How is this an upgrade?  I dont get it.

I will just keep 9.10 till I find a replacement.  Maybe one of the other distros will work on all computers, with a minimum of fixing.

---

### Post by Confused Computer User on 2010-06-05
@Chrisco66
I hope I am not too late to save you the hassle for Mint. You are right. It's the same issue as with 10.04.

Puppy linux is indeed "light" as you put it but it works. Same goes for xubuntu but to a lesser degree. Problem for me with Xubuntu is that most of the eye candy is not available, witch makes having a 500+ MB of video memory useless.

I'm back on 9.10 as well but even this gives me some problems. I have that shutdown problem with it but it's still good compared to 10.04. I'm waiting for 10.10 or a better alternative. Please post back if you find it.

---

### Post by Chrisco66 on 2010-06-05
Thanks for the warning, no, I downloaded it, but never burned it to disk.

Have you tried pclinux?  It worked well on my test box, but it wouldn't install on my laptop.  I may try it again though.  I think I tried out 3 distros in a day, and if one didn't install, I just moved on.  Maybe I will try it one more time though.  I still have the disk.  

Have you looked at something called meego?  It looks similar to the netbook remix.  Im going to go "shopping" on Distrowatch.com, and get about 5 more to try.  I will find one.  

Ill let you know if I find anything..

---

### Post by coldraven on 2010-06-06
I'm glad that I read this thread, I was just about to install 10.04. 
9.10 is working well on this Compaq 6715b the only thing not found is the fingerprint reader. The ATI X1250 card will even run Sketchup in a VM XPpro (Virtualbox) at the same time as spinning cubes etc.
No good for 3D games though! Tux racer gives 4fps!!
 
I just installed 10.04 32bit as dual boot with the existing 9.10 64bit. It all seems to work OK and now Tux Racer gives 12fps!
The reason for going down to 32bit was because Adobe are not supporting 64bit Flash and there is a security risk with the current version. See: [http://www.theregister.co.uk/2010/06/11/64_bit_flash_for_linux_dead/](http://www.theregister.co.uk/2010/06/11/64_bit_flash_for_linux_dead/)

---

### Post by Confused Computer User on 2010-06-06
> **Chrisco66 said:**
> Thanks for the warning, no, I downloaded it, but never burned it to disk.

Have you tried pclinux?  It worked well on my test box, but it wouldn't install on my laptop.  I may try it again though.  I think I tried out 3 distros in a day, and if one didn't install, I just moved on.  Maybe I will try it one more time though.  I still have the disk.  

Have you looked at something called meego?  It looks similar to the netbook remix.  Im going to go "shopping" on Distrowatch.com, and get about 5 more to try.  I will find one.  

Ill let you know if I find anything..

I've got a limited band with of 1GB (and i'm already over the limit). Once I go to school tomorow i'll download fedora, pclinux, and meego.

I haven't heard of either of them but I'll give it a go. I'm looking for something for the desktop. My laptop is an HP Pavilion dv2755 TX witch is pretty comfy with Vista so I'm not too eager to add Linux to the mix especially with the recent strings of issues I've had so far.

For now I'll keep 9.10 and try the others as live cd's. If they work well as that, then no issues.

EDIT.
I just realized. If the Distro uses the KDE interface then it will most likely not work with the X1600 Video Card. The reason for that is that I tried Kubuntu (which uses KDE) and that was no better than Ubuntu.

---

### Post by waynefoutz on 2010-06-09
> **Confused Computer User said:**
> @Chrisco66
I hope I am not too late to save you the hassle for Mint. You are right. It's the same issue as with 10.04.

Puppy linux is indeed "light" as you put it but it works. Same goes for xubuntu but to a lesser degree. Problem for me with Xubuntu is that most of the eye candy is not available, witch makes having a 500+ MB of video memory useless.

I'm back on 9.10 as well but even this gives me some problems. I have that shutdown problem with it but it's still good compared to 10.04. I'm waiting for 10.10 or a better alternative. Please post back if you find it.

Try these: Debian 5.0 (Lenny) or CentOS. They still run older versions of xserver.xorg that won't conflict with the ATI Legacy driver.

---

### Post by waynefoutz on 2010-06-09
> **coldraven said:**
> I'm glad that I read this thread, I was just about to install 10.04. 
9.10 is working well on this Compaq 6715b the only thing not found is the fingerprint reader. The ATI X1250 card will even run Sketchup in a VM XPpro (Virtualbox) at the same time as spinning cubes etc.
No good for 3D games though! Tux racer gives 4fps!!

You're going to get better performance out of 10.04 than you will Jaunty. The open source drivers for that chipset weren't nearly as developed as they are now. You'd do better to downgrade to Hardy right now though. I have the same card. I'm getting 45-60 fps out of tuxracer (I just checked) with Hardy and the fglrx drivers. Staying with Jaunty is the worst thing you could do.

---

### Post by Confused Computer User on 2010-06-09
> **waynefoutz said:**
> Try these: Debian 5.0 (Lenny) or CentOS. They still run older versions of xserver.xorg that won't conflict with the ATI Legacy driver.

I wanted to try debian for a while but I was confused about the DVD set. Never seen a Linux distro take more than a DVD. Oh well. there goes the bandwidth. Out of curiosity, will OO 3.2.1 run on Debian?

Also thanks for the post. :p

---

### Post by waynefoutz on 2010-06-09
> **Confused Computer User said:**
> I wanted to try debian for a while but I was confused about the DVD set. Never seen a Linux distro take more than a DVD. Oh well. there goes the bandwidth. Out of curiosity, will OO 3.2.1 run on Debian?

Also thanks for the post. :p

Download the 200 megabyte network install iso. then plug your machine into your router, and the net installer will download just  the packages that  it needs. There's no need to download all those DVDs unless you want your own local repository. 

Yeah it will run Open Office.

---

### Post by Confused Computer User on 2010-06-09
> **waynefoutz said:**
> Download the 200 megabyte network install iso. then plug your machine into your router, and the net installer will download just  the packages that  it needs. There's no need to download all those DVDs unless you want your own local repository. 

Yeah it will run Open Office.

Thanks for the reply (again:p)

That is amazing but at home my bandwidth is 1 Gig (upload and download combined) and I'm already over 7 Gig in excess of that. But I did download the dvd's at school so I now have the first 4 which I understand is more than enough. If not tomorrow I'll download the last remaining two.

 Again thank you for the feedback and I'll post back with results.

---

### Post by Confused Computer User on 2010-06-10
OK.

Well, Debian is ok in terms of install but not much help with my issue the driver doesn't work and I'm stuck at the same point as with 10.04. I can't turn on the compiz effects at all. I've tried. I'm missing something. Even if the xorg is older I still couldn't get it to work.

Why can't they keep the the old 9.10 drivers?

---

### Post by Chrisco66 on 2010-06-10
I think the Ubuntu website should clearly point out that Ubuntu will no longer run on older hardware.  That is not even true because it runs fine on that ancient POS at work, and on my testbox which I know is ten years old.  They need to warn people that they will have video, wireless and on some machines disk burning issues.  

With all the fanfair of the new LTR, you would have thought that someone would have noticed the problems and fixed them in the beta releases.  

I was going to try the netbook remix.  I dont know if it would fix the wireless and video problems.  I really dont feel like wasting my time trying.  Even if it does work, maybe they will screw it up again with the next release?  

It seems that the problems relate to the new kernel.  I tried several other distros, and if it had the new kernel, it had problems.  Im not sure I understand what is happening with Linux in general.  Who decides what changes are made to the kernel?  Who tests it?  Who approves it for release?  

My point is, even if you find a distro that is not using the new kernel, how long will it be before they "upgrade" and the problems come back?  

It just seems like Linux is going off in the wrong direction.  When I installed 8.04, I had no problems.  Everything just worked.  New hardware, 3 year old hardware, 10 year old hardware, no matter.  Now I have to tweak this, and change the setting for that.  I dont mind if it was one problem, and people knew and are working on it.  I have had at least four problems on different machines, and still, nobody who can fix it seems to be interested.  Im not talking about some obscure hardware.  Im talking about wireless cards and video cards.  This is basic stuff.  It should work on every machine, or we should be told before we install.  NDIS wrapper?  If I want to run windows software, Ill go back to windows.  Where is the native support that existed on previous releases?  PUT IT BACK.  

I wish I knew how to write code.  I would fix it myself and release my own distro.  Sorry, Im just pissed.  I spread the word about Linux and Ubuntu.  Now I look like a fool because peoples computers dont work anymore, and I dont have any answers for them..

---

### Post by waynefoutz on 2010-06-10
> **Confused Computer User said:**
> OK.

Well, Debian is ok in terms of install but not much help with my issue the driver doesn't work and I'm stuck at the same point as with 10.04. I can't turn on the compiz effects at all. I've tried. I'm missing something. Even if the xorg is older I still couldn't get it to work.

Why can't they keep the the old 9.10 drivers?


follow this guide:

[http://technowizah.com/2006/10/debian-how-to-ati-drivers.html]("http://technowizah.com/2006/10/debian-how-to-ati-drivers.html")

in the code boxes, substitute the version number of the driver with the version number ATI's site tell you your card needs. I can't remember which card you said you were using, but my x1250 uses ATI catalyst 9.3 which is ati-driver-installer-9-3-x86.x86_64.run

Sorry it takes me so long to respond...working these 16 hour days is killing me

---

### Post by waynefoutz on 2010-06-11
> **Chrisco66 said:**
> I think the Ubuntu website should clearly point out that Ubuntu will no longer run on older hardware.  That is not even true because it runs fine on that ancient POS at work, and on my testbox which I know is ten years old.  They need to warn people that they will have video, wireless and on some machines disk burning issues.  

With all the fanfair of the new LTR, you would have thought that someone would have noticed the problems and fixed them in the beta releases.  

I was going to try the netbook remix.  I dont know if it would fix the wireless and video problems.  I really dont feel like wasting my time trying.  Even if it does work, maybe they will screw it up again with the next release?  

It seems that the problems relate to the new kernel.  I tried several other distros, and if it had the new kernel, it had problems.  Im not sure I understand what is happening with Linux in general.  Who decides what changes are made to the kernel?  Who tests it?  Who approves it for release?  

My point is, even if you find a distro that is not using the new kernel, how long will it be before they "upgrade" and the problems come back?  

It just seems like Linux is going off in the wrong direction.  When I installed 8.04, I had no problems.  Everything just worked.  New hardware, 3 year old hardware, 10 year old hardware, no matter.  Now I have to tweak this, and change the setting for that.  I dont mind if it was one problem, and people knew and are working on it.  I have had at least four problems on different machines, and still, nobody who can fix it seems to be interested.  Im not talking about some obscure hardware.  Im talking about wireless cards and video cards.  This is basic stuff.  It should work on every machine, or we should be told before we install.  NDIS wrapper?  If I want to run windows software, Ill go back to windows.  Where is the native support that existed on previous releases?  PUT IT BACK.  

I wish I knew how to write code.  I would fix it myself and release my own distro.  Sorry, Im just pissed.  I spread the word about Linux and Ubuntu.  Now I look like a fool because peoples computers dont work anymore, and I dont have any answers for them..


The thread is about ATI, and with regards to ATI, AMD, who bought ATI is the one to blame in this circumstance. The drivers were always closed source, but kept updated and easy to obtain and install. AMD stopped updating them for older cards. The open source community, which had no reason to keep up, suddenly had to play catch up to get these cards functioning again. They've come a long way since they were broken with Jaunty's release, and performance has improved significantly with each kernel update. Open source means you have a bunch of people working on it, with no profit incentive. They are doing it only as a labor of love. Hats off to them. They're doing a great job. They have my old ATI card back up to 90% of where it was with the ATI drivers. If AMD kept up with it's drivers, we wouldn't be in this mess.

---

### Post by Confused Computer User on 2010-06-11
> **waynefoutz said:**
> follow this guide:

[http://technowizah.com/2006/10/debian-how-to-ati-drivers.html]("http://technowizah.com/2006/10/debian-how-to-ati-drivers.html")

in the code boxes, substitute the version number of the driver with the version number ATI's site tell you your card needs. I can't remember which card you said you were using, but my x1250 uses ATI catalyst 9.3 which is ati-driver-installer-9-3-x86.x86_64.run

Sorry it takes me so long to respond...working these 16 hour days is killing me

First:
Thank you soo much for the reply.

Second:
No appologies. Work comes first and even late I really appreciate the reply (better late then never :p)

Third:
I have X1600 which, following the prompts from the ATI website gave me the same catalyst as you. I did install it on Debian 5.0 but not with that specific sequence of steps.

In the end each time I ran compiz --replace in the terminal, I kept getting a white screen.

I'll try it again but with the new list of steps.

Thanks again and plase be pacient. I'l post back with results as soon as I have any (ETC 5 hours)

---

### Post by waynefoutz on 2010-06-11
> **Confused Computer User said:**
> First:
Thank you soo much for the reply.

Second:
No appologies. Work comes first and even late I really appreciate the reply (better late then never :p)

Third:
I have X1600 which, following the prompts from the ATI website gave me the same catalyst as you. I did install it on Debian 5.0 but not with that specific sequence of steps.

In the end each time I ran compiz --replace in the terminal, I kept getting a white screen.

I'll try it again but with the new list of steps.

Thanks again and plase be pacient. I'l post back with results as soon as I have any (ETC 5 hours)

I have to admit I've never installed it in Debian, but I used the same guide to install it in Ubuntu Intrepid (8.10) and it worked for me. Intrepid is end of lifed, so I downgraded to Hardy Heron, 8.04, which is an LTS version, and supported until next April. Installing it on that couldn't be simpler, just user the Hardware Drivers app in the System menu, enable it, reboot and you're done. Debian shouldn't be much different. Keep me posted. Because I'm just a poor truck driver with a house full of kids back home, I'm hoping to keep this old Dell Latitude humming for a few more years. After Hardy goes EOL, Debian 5 is probably my next move. I do have Debian running on an older desktop at home.

---

### Post by Mark Phelps on 2010-06-11
> **Chrisco66 said:**
> I think the Ubuntu website should clearly point out that Ubuntu will no longer run on older hardware.  That is not even true because it runs fine on that ancient POS at work, and on my testbox which I know is ten years old.  They need to warn people that they will have video, wireless and on some machines disk burning issues.  
Since Canonical, unlike Microsoft, doesn't have untold MILLIONS of dollars to spend testing every machine config imaginable, there are bound to be machines that will present problems.  Which is WHY the LiveCD was invented in the first place.  Anyone too lazy to spend 15 minutes booting in LiveCD mode, to find out what problems they have, IMHO, is asking for trouble.

> With all the fanfair of the new LTR, you would have thought that someone would have noticed the problems and fixed them in the beta releases. 
Beta testing is NOT about spending untold MILLIONS of dollars testing every imaginable hardware setup; it's about testing the new features and settings, on a limited set of hardware, to see what happens.  Since Beta Testing, in Ubuntu, is freely open to everyone who asks, if you don't ask, you can't whine later about your machine not working.

> I was going to try the netbook remix.  I dont know if it would fix the wireless and video problems.  I really dont feel like wasting my time trying.  
If you're not willing to waste your time, why should Canonical waste theirs?

> It seems that the problems relate to the new kernel.  I tried several other distros, and if it had the new kernel, it had problems.  Im not sure I understand what is happening with Linux in general.  Who decides what changes are made to the kernel?  Who tests it?  Who approves it for release?   Canonical is the "owner" of Ubuntu, but they openly invite Linux community participation in deciding what goes into future releases, and they openly allow community participation in testing those releases.

> My point is, even if you find a distro that is not using the new kernel, how long will it be before they "upgrade" and the problems come back?  
Excellent point!! Which is WHY the SMART thing to do is to try the LiveCD mode first -- to see how well the latest version detects your hardware and load the proper drivers.

> It just seems like Linux is going off in the wrong direction.  When I installed 8.04, I had no problems.  Everything just worked.  New hardware, 3 year old hardware, 10 year old hardware, no matter.  Now I have to tweak this, and change the setting for that.  I dont mind if it was one problem, and people knew and are working on it.  I have had at least four problems on different machines, and still, nobody who can fix it seems to be interested.  Im not talking about some obscure hardware.  Im talking about wireless cards and video cards.  This is basic stuff.  It should work on every machine, or we should be told before we install.  NDIS wrapper?  If I want to run windows software, Ill go back to windows.  Where is the native support that existed on previous releases?  PUT IT BACK. 
Here's where I agree with some of what you said -- I have personally found 8.04 to be the absolute BEST Ubuntu version they ever built!  I installed in on a Tablet PC and, like you, I found everything to work out of the box.  Not a single release since then has worked on my tablet PC -- which is why I reluctantly replaced it with Win7 -- in which, everything works, again! 

> I spread the word about Linux and Ubuntu.  Now I look like a fool because peoples computers dont work anymore, and I dont have any answers for them..
If it's any consolation, I feel much the same way.  I've been a strong advocate of Ubuntu for years, and it seems that every new release starts out with the same 3-6 months of disasters for early adopters. Most folks out there simply want a PC environment that works!  They don't want to spend days, or weeks, hacking around with one setting after another just to get basic stuff working.

When I installed 10.04 a couple of days ago, I was visibly impressed by how much stuff had been improved over 9.10, but then, maybe I'm one of the "lucky ones".

---

### Post by Confused Computer User on 2010-06-11
> **Mark Phelps said:**
> 
When I installed 10.04 a couple of days ago, I was visibly impressed by how much stuff had been improved over 9.10, but then, maybe I'm one of the "lucky ones".

Well if your video card is an intel, then you probably don't have issues. They do aim there releases for the majorety of computers out there but then again what is a majorety (99%, 90%, 60%)?


@ waynefoutz
I've tried it and no go for me.... guess i'm back to 10.04 hopefully the next ones will get better. if not i'll just result to using my integrated chip. I just feel bad about not getting to use it. Oh well, I'll stick to no effects for the time being.

Also, if this offers some hope, it appears the ATI Mobility Radeon X1600 works fine with 10.04 with the exception of the external monitor. Still, I'm guessing there can't be that much of a difference between the right?

See:
[http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card](http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card)

---

### Post by waynefoutz on 2010-06-12
> **Confused Computer User said:**
> Well if your video card is an intel, then you probably don't have issues. They do aim there releases for the majorety of computers out there but then again what is a majorety (99%, 90%, 60%)?


@ waynefoutz
I've tried it and no go for me.... guess i'm back to 10.04 hopefully the next ones will get better. if not i'll just result to using my integrated chip. I just feel bad about not getting to use it. Oh well, I'll stick to no effects for the time being.

Also, if this offers some hope, it appears the ATI Mobility Radeon X1600 works fine with 10.04 with the exception of the external monitor. Still, I'm guessing there can't be that much of a difference between the right?

See:
[http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card](http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card)


Well, good luck. I'm going to stick with 8.04 for now. Everything just works so well, I just can't bring myself to get rid of it. Sorry Debian didn't work out for you.

My X1250 worked pretty good with 10.04. I had the desktop effects. But some of the 3d games didn't display properly, and the ones that did had abhorent frame rates. But, if you aren't into that, or don't mind dual booting into Windows when the urge to play a game takes over, the performance 10.04 will give you is fine for the average user. You will have some 3d, but it doesn't perform all that well.

My experience with 10.04: Google Earth had jagged lines radiating out from the center of the globe, in SuperTuxKart the cars looked like they were travelling under the road instead of on it, and Urban Terror looked beautiful, but only gave me 5-10 FPS. Other 3d games like Neverball worked fine. Everything 2d worked great. Flash worked perfectly.

---

### Post by waynefoutz on 2010-06-12
> Here's where I agree with some of what you said -- I have personally found 8.04 to be the absolute BEST Ubuntu version they ever built!  I installed in on a Tablet PC and, like you, I found everything to work out of the box.  Not a single release since then has worked on my tablet PC -- which is why I reluctantly replaced it with Win7 -- in which, everything works, again! 



I remember when it first came out. There were a lot of angry users. Pulseaudio got less than a warm reception, and they bundled it up with a BETA version of Firefox. My vote for best though would be 8.10. It was the only version ever made that EVERYTHING works on my laptop, out of the box. I still to this day keep a 2 gigabyte USB key in my laptop bag with Linux Mint Felicia, which is 8.10 with Java and Flash installed, just in case my hard drive fails while I'm on the road, I can boot off Felicia and have a fully functioning computer until a replacement drive arrives. 


> If it's any consolation, I feel much the same way.  I've been a strong advocate of Ubuntu for years, and it seems that every new release starts out with the same 3-6 months of disasters for early adopters. Most folks out there simply want a PC environment that works!  They don't want to spend days, or weeks, hacking around with one setting after another just to get basic stuff working.


That's what the LTS versions are for, and why their support life overlaps by a year. I can hang back with Hardy for a while, let the folks with the brand new gear be the guinea pigs.


> When I installed 10.04 a couple of days ago, I was visibly impressed by how much stuff had been improved over 9.10, but then, maybe I'm one of the "lucky ones".


I personally don't care much for the default themes. I don't like the default icon set at all. Maybe that's knit-picking, because it can all be changed easily enough.

---

### Post by Chrisco66 on 2010-06-12
Try out the new live cd?  Its an upgrade.  I did it online, just like the website told me to.  I didnt burn it disk till later, when things stopped working.  Too lazy?  If I were too lazy I would have gone back to windows a long time ago.  Save the insults, it has no place here.

No, I dont expect Conanical to test every possible hardware config, but some of these problems come up every time.  My point is, if it worked in the last release, why change it?

I dont beta test anymore because I simply dont have the time.  I installed the 10.04 beta on one machine.  I didnt even get back to play with it before the LTS was released.  Im sorry my level of participation is not up to yours.  Whining?  No, just tired of trying make something work...again.

Gee Mark, I guess I really hurt your feelings or something.  The reason I am not going to try netbook remix, is because it is based on Ubuntu, which doesnt work.  If it did work, what is the chance it will still work after the next upgrade.  My point again, why fix something that is not broken?  How many times should I reinstall before I start looking for other answers? I realise that the technology is not supposed to stand still.  To move forward it has to get better, not worse. 

This has been the most troublesome version yet.  There are bug reports that show some of the problems fixed.  Not from where I am standing.  I have gotten at least 3 people to switch to Linux completely, and several more to dual boot.  I have demonstrated Linux (Ubuntu) to at least 20 people.  I cant tell people its the best.  I cant even tell people its ok.  I have to tell people that "most stuff works on desktops, but you may have wireless or display problems on notebooks".  Who in their right mind would consider trying it now?

---

### Post by waynefoutz on 2010-06-12
> **Chrisco66 said:**
> Try out the new live cd?  Its an upgrade.  I did it online, just like the website told me to.  I didnt burn it disk till later, when things stopped working.  Too lazy?  If I were too lazy I would have gone back to windows a long time ago.  Save the insults, it has no place here.

No, I dont expect Conanical to test every possible hardware config, but some of these problems come up every time.  My point is, if it worked in the last release, why change it?

I dont beta test anymore because I simply dont have the time.  I installed the 10.04 beta on one machine.  I didnt even get back to play with it before the LTS was released.  Im sorry my level of participation is not up to yours.  Whining?  No, just tired of trying make something work...again.

Gee Mark, I guess I really hurt your feelings or something.  The reason I am not going to try netbook remix, is because it is based on Ubuntu, which doesnt work.  If it did work, what is the chance it will still work after the next upgrade.  My point again, why fix something that is not broken?  How many times should I reinstall before I start looking for other answers? I realise that the technology is not supposed to stand still.  To move forward it has to get better, not worse. 

This has been the most troublesome version yet.  There are bug reports that show some of the problems fixed.  Not from where I am standing.  I have gotten at least 3 people to switch to Linux completely, and several more to dual boot.  I have demonstrated Linux (Ubuntu) to at least 20 people.  I cant tell people its the best.  I cant even tell people its ok.  I have to tell people that "most stuff works on desktops, but you may have wireless or display problems on notebooks".  Who in their right mind would consider trying it now?

In just about every case where I've had something break after an upgrade it was because of a closed source, proprietary driver I was using didn't get upgraded. Open source drivers always survive the upgrade. There's nothing Ubuntu can do about that.
 
 Ubuntu is a distro that tries to stay on the bleeding edge.  A Linux distro is nothing more than a collection of applications bundled together to make an operating system. When Xorg gets updated, Ubuntu runs with it. Ubuntu comes out with a completely new version every six months, Microsoft once over 7-10 years. That's a big difference. Ubuntu isn't for everyone. There are Linux distros out there that don't get overhauled as often, some of them not at all. Debian 5, CentOS, and any one of the "Enterprise" versions of the popular distros is probably a better choice if you want something more stable. And for Ubuntu, there is no law written that you have to upgrade it. You said earlier that 8.04 was your version of choice..it's mine too. I'm running it now and have no plans on updating any time soon. I have until the end of April 2011, I'll see how well the open source video drivers have progressed, and if they aren't to my liking I'll either go to Debian or just continue running 8.04 with no updates.

---

### Post by Chrisco66 on 2010-06-12
Actually, I said I had the best luck with 9.10, but I get your point.  

My point is that if something is said to be improved, it should work better.  If it were something minor, I would just live with it.  I dont expect any OS to be perfect, but wireless and video is mandatory.  Yes, I had problems finding drivers in windows too.  Maybe Im just spoiled by the last upgrade which went perfectly.  Maybe I wouldnt be so pissed if I had found the answer and it was fixed already.  

Yes, I know I am not being forced to use Ubuntu, or Linux for that matter.  Its just a really uncomfortable feeling when you thought you had something figured out and then someone pulls the rug out from under you. I though Ubuntu was my OS.  Now, I dont know.  

As far as bleeding edge goes, when they say "stable release" or something similar, I take that to mean that it will work.  Maybe Im just naïve.  I know I avoid software that is not in the repositories, and I try not to add repositories unless it is necessary.  In other words, I try not to create my own problems by using anything untested.  

As for the proprietary drivers, maybe there is nothing that can be done.  Its just disappointing when something used to work, now it doesnt.  Someone posted that ATI is now owned by AMD, and they dont share.  Not the fault of Ubuntu.

I found a fix for my video problem and posted it here, I hope it helps somebody.  Now I am stuck with two machines with limited or no wireless.  The search continues..

---

### Post by waynefoutz on 2010-06-13
> **Chrisco66 said:**
> Actually, I said I had the best luck with 9.10, but I get your point.  

My point is that if something is said to be improved, it should work better.  If it were something minor, I would just live with it.  I dont expect any OS to be perfect, but wireless and video is mandatory.  Yes, I had problems finding drivers in windows too.  Maybe Im just spoiled by the last upgrade which went perfectly.  Maybe I wouldnt be so pissed if I had found the answer and it was fixed already.  

Yes, I know I am not being forced to use Ubuntu, or Linux for that matter.  Its just a really uncomfortable feeling when you thought you had something figured out and then someone pulls the rug out from under you. I though Ubuntu was my OS.  Now, I dont know.  

As far as bleeding edge goes, when they say "stable release" or something similar, I take that to mean that it will work.  Maybe Im just naïve.  I know I avoid software that is not in the repositories, and I try not to add repositories unless it is necessary.  In other words, I try not to create my own problems by using anything untested.  

As for the proprietary drivers, maybe there is nothing that can be done.  Its just disappointing when something used to work, now it doesnt.  Someone posted that ATI is now owned by AMD, and they dont share.  Not the fault of Ubuntu.

I found a fix for my video problem and posted it here, I hope it helps somebody.  Now I am stuck with two machines with limited or no wireless.  The search continues..

I feel your pain. My laptop is just over a year old, and my x1270 is considered obsolete. What's enraging is that they are still putting this chipset into low end laptops and netbooks today.

As for your wireless, why not go get yourself a $25 usb dongle and be done with it?

---

### Post by Mark Phelps on 2010-06-13
> **Chrisco66 said:**
>  ...Gee Mark, I guess I really hurt your feelings or something...

No, you didn;t hurt my feelings ... and sorry if I came on a bit too strong!

> This has been the most troublesome version yet.  There are bug reports that show some of the problems fixed.  Not from where I am standing.  I have gotten at least 3 people to switch to Linux completely, and several more to dual boot.  I have demonstrated Linux (Ubuntu) to at least 20 people.  I cant tell people its the best.  I cant even tell people its ok.  I have to tell people that "most stuff works on desktops, but you may have wireless or display problems on notebooks".  Who in their right mind would consider trying it now?

IMHO, Linux in general, and Ubuntu specifically, has always been focused on folks who want to experiment with Alternatives to MS Windows.  In many cases, Ubuntu has just installed and worked for folks, but as Canonical changes more and more underlying stuff to stay on the "leading edge", they DO run the risk of making installation riskier for more and more of the community.

I, too, use to strongly recommend Ubuntu to other folks -- but I've had to revert three machines that I support BACK to MS Windows.  Why? Because changes to the kernel and other stuff caused those machine to begin failing and LOTS of posts in the forums failed to come up with solutions that worked.

I now use 10.04 on my desktop and like it, and keep 8.04 on my Tablet PC because it still works -- but the other machines are all back to MS Windows now (XP).  As I said earlier, most folks just want a machine that "works".

---

### Post by Confused Computer User on 2010-06-17
Hi all,

I finally got it to work (ATI Radeon X1600). The credit is not mine but belongs to a forum user named Temüjin.

> **Temüjin said:**
> ```
gksu gedit /etc/modprobe.d/radeon-kms.conf
```
Copy/paste:
```
options radeon modeset=0
```
Save. Quit. Restart.


I'm not sure what exactly this does but the effect was that I was able to run compiz and advance effects without so much as a stumble. 

Now I just have to wait for the update of the driver to get rid of the horizontal tearing that occurs when watching movies. By the way this was happening before this command lines were executed so if you notice it at well, I can garunty that this procedure is not at fault.

Well, here's to hoping things get better.

Please comment on outcome if possible.

---

### Post by animale81 on 2010-06-18
It works!!!!!!!!

Are you great? no mooooooooore..

thanks really...
 
just to give you my experience:
i came from 9.10 with ati 1950 pro were compiz worked fine. After upgrading nothing work more and especially boxee freeze always. After you suggestion  it works in a wonderful way....

Thanks!!!!!!

---

