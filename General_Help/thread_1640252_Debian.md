---
title: "Debian"
date: 2010-12-07
forum: General Help
---

### Post by Hippytaff on 2010-12-07
I am going to dual boot debian and my current maverick. Is it possible for debian and ubuntu to share my existing seperate /home partition?

---

### Post by bodhi.zazen on 2010-12-07
> **Hippytaff said:**
> I am going to dual boot debian and my current maverick. Is it possible for debian and ubuntu to share my existing seperate /home partition?

Yes.

In general I advise a unique UID for each OS, but you do not "need" to do that.

---

### Post by Hippytaff on 2010-12-07
Excellent - thanks bodhi.zazen...just got some way through the install but debian can't see my wireless...ethernet it is :-)

Thanks again :-)

---

### Post by QLee on 2010-12-07
Just be careful Hippytaff, depending on the version of Debian you are installing, you might have a different version of some (or all) of the applications and sometimes that means different and incompatible version of the user configuration files. Then you could end up with dueling distros rather than dual booting. Might also have legacy GRUB - GRUB2(grub-pc) issues between different distros. Probably nothing you can't deal with, you reply to a lot of threads.

---

### Post by bodhi.zazen on 2010-12-07
> **Hippytaff said:**
> Excellent - thanks bodhi.zazen...just got some way through the install but debian can't see my wireless...ethernet it is :-)

Thanks again :-)

Yep, Debian does not always have as many "creature comforts" installed out of the box, you sometimes need to track down a few more drivers then with Ubuntu.

---

### Post by Hippytaff on 2010-12-07
this is what I'm learning :-)

Ubuntu converted me and now I need more, to be fair debian recognised what proprietery driver was needed, just happened to be my wireless one :-)

---

### Post by QLee on 2010-12-07
[QUOTE=Hippytaff]...
Ubuntu converted me and now I need more, to be fair debian recognised what proprietery driver was needed, just happened to be my wireless one :-)[/QUOTE]

Broadcom, maybe? Lenny(stable), maybe? fw-cutter to get the firmware, maybe?

---

### Post by Hippytaff on 2010-12-07
> 
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

I know, I thought it would just work out of the box too, maybe not!? yes lenny stable, firmware cutter maybe, but ethernet for now :-) untill I do a bit more research at least :-)

---

### Post by QLee on 2010-12-07
Oh, hardly any of this stuff worked out of the box with Lenny, old kernels. Maybe a backport kernel but I suggest you think about loading Squeeze, it's currently the "testing" release candidate but it's been frozen(only release critical bug fixes) because they are trying to get it released by the end of the year. It's already past the target date but Debian policy is to release when "it is ready" and that's a pretty loose policy and cycle has varied widely, although there is pressure to become more like Ubuntu with a set cycle, not all of the voting developers agree.

---

### Post by Hippytaff on 2010-12-07
Maybe I'll give that a go then, though I'm not sure I'm confident enough to do a pre-RC install of any distro. But I guess we learn this way. Not sure I can be bothered with debian unless I can, without too much bother, use my wireless, though that said I've always got ubuntu to fall back on

---

### Post by bodhi.zazen on 2010-12-07
> **Hippytaff said:**
> Maybe I'll give that a go then, though I'm not sure I'm confident enough to do a pre-RC install of any distro. But I guess we learn this way. Not sure I can be bothered with debian unless I can, without too much bother, use my wireless, though that said I've always got ubuntu to fall back on

I would at least try debian squeeze, it has been reasonably stable and is close to a release. A few packages here and there are rough around the edges.

---

### Post by Hippytaff on 2010-12-07
> **bodhi.zazen said:**
> I would at least try debian squeeze, it has been reasonably stable and is close to a release. A few packages here and there are rough around the edges.

Your right, wheres my sense of adventure?

I've only recently come back to linux, after wiping my windows with Mandrake (which really didn't work as an intro to linux) about 12 years ago. thanks to the ease and user friendlyiness of ubutnu, I've been able to learn ,quite easily and quicky, some of the workings of linux,  byobu, screen, and cli stuff, which what attracted me to linux in the first place, all those years ago.

---

### Post by QLee on 2010-12-07
[QUOTE=Hippytaff]Maybe I'll give that a go then, though I'm not sure I'm confident enough to do a pre-RC install of any distro. But I guess we learn this way. Not sure I can be bothered with debian unless I can, without too much bother, use my wireless, though that said I've always got ubuntu to fall back on[/QUOTE]
If you choose to try.
Make sure your system is fully upgraded.
Edit your sources list and replace "lenny" if you use codenames, to "squeeze". If you use "stable", I'd still suggest you replace it with "squeeze", if you replace with "testing" you will get a big surprise next upgrade after release.
Then (I prefer to do this from a console so I'm not upgrading X from within X):
apt-get update
apt-get dist-upgrade

You can use Synaptic too, if you prefer GUI. I guess you've already figured out the no sudo stuff and are familiar with doing system tasks as su.

Nothing to lose but time.


[Edit] Oh poo, I see my post is number 13, I hope that doesn't foul your luck.  Interesting, I started with Mandrake too, it just that I stuck with GNU/Linux. I still miss the "wand". Give Slackware a try sometime, if it's still the same, it has lots of "opportunities to learn". :-)

Darn, already the 13 is fouling, no capitols on the codenames, I've edited above, sorry.

---

### Post by sgosnell on 2010-12-07
You might give Linux Mint Debian Edition a try.  It's Debian Testing, with some tweaks, and when I moved there from Ubuntu everything worked out of the box.  You can change the repositories from testing to Squeeze if you want.  IME, though, Debian Testing is far more stable than Ubuntu.

---

### Post by bodhi.zazen on 2010-12-07
> **sgosnell said:**
> IME, though, Debian Testing is far more stable than Ubuntu.

I agree with that general statement. There are individual packages that can be problematic though.

---

### Post by sgosnell on 2010-12-07
Well, there are always individual packages that cause problems.  Every new version of Ubuntu is an adventure, though.  Every 6 months lots of things break.  With Debian Testing, everything has been rather thoroughly tested in Unstable before it gets into Testing, moreso than the Ubuntu stuff.  The breakage, and the threat of Unity, has finally sent me to Debian, and away from Ubuntu.  I may eventually regret it, and I might someday return to Ubuntu, but for now I'm very happy with Debian.

---

### Post by Hippytaff on 2010-12-08
Thanks all for your input and advice - I'll install lenny and upgrade to squeeze and give it a bash.

---

### Post by Hippytaff on 2010-12-08
So, to clarify, before I jump in head first - 
 
1 Resize ubuntu with gparted to make room for Debian
2 Don't worry too much about overwritting grub2 (just do sudo update-grub)
3 Use a the same UID to be able to use the same /home partition for both distro's
4 Change sources.list to squeeze (sudo apt-get update && sudo dist-upgrade)
5 Rock on
:-)

---

### Post by nolag on 2010-12-08
> **Hippytaff said:**
> I know, I thought it would just work out of the box too, maybe not!? yes lenny stable, firmware cutter maybe, but ethernet for now :-) untill I do a bit more research at least :-)
 
It's not too hard, I did a google search and got the results for my card.  Most are easy but need backports.  I needed IWLAGN 
 
> **sgosnell said:**
> You might give Linux Mint Debian Edition a try. It's Debian Testing, with some tweaks, and when I moved there from Ubuntu everything worked out of the box. You can change the repositories from testing to Squeeze if you want. IME, though, Debian Testing is far more stable than Ubuntu.
 
Well, testing should be more stable than ubuntu in theory, since ubuntu is based off sid.  Also LMDE would not let you learn as much, since like ubuntu, it does a lot for you.  I know the reason I installed Debian (along side ubuntu and windows 7) was to learn more about linux and get experience with things ubuntu does for me (please don't say try arch linux I want the farmiliarity of deb's and some things that are set up in debian).

---

### Post by QLee on 2010-12-08
[QUOTE=Hippytaff]So, to clarify, before I jump in head first - 
 
...[/QUOTE]

I suggest you re-read the whole thread very carefully.

This is not really the place to support Debian and given the list you just showed, we could try to set the record for the longest thread in the General Forum. As an example, what sudo?

There are lots of Debian specific forums, some of them are fairly friendly, that would be the better place to deal with Debian installing and configuration.

---

### Post by Hippytaff on 2010-12-08
> **QLee said:**
> I suggest you re-read the whole thread very carefully.
 
This is not really the place to support Debian and given the list you just showed, we could try to set the record for the longest thread in the General Forum. As an example, what sudo?
 
There are lots of Debian specific forums, some of them are fairly friendly, that would be the better place to deal with Debian installing and configuration.
 
Point taken...guess I was looking for some reassurance :-) I'll check the Debian forums, I've just grown used to the ubuntu forums that where people haven't instantly dismissed my questions as stupid and me as incompitent. A re-read (as you suggested) has clarified stuff. :-) (su not sudo being one example, being another doh!)
 
 
[http://grub.enbug.org/Debian](http://grub.enbug.org/Debian)

---

### Post by QLee on 2010-12-08
[QUOTE=Hippytaff]... I've just grown used to the ubuntu forums that where people haven't instantly dismissed my questions as stupid and me as incompitent.[/QUOTE]
Well, we all have to learn, before we "know". Not all Debian users are "oldschool", RTFM types but you might encounter some.

You have enthusiasm and a willingness to help, with more knowledge you'll be awesome here.

 [QUOTE=Hippytaff]A re-read (as you suggested) has clarified stuff. :-) (su not sudo being one example, being another doh!)[/QUOTE]

Yeah, after Lenny had mucked with the user config files in your ~home, you would have tried sudo, only to be told you aren't in the sudoers and that your attempt would be reported. After reboot, legacy GRUB wouldn't have known about your Ubuntu install. Would have been a mess for us to try and fix and lots of people who didn't understand enough, and who didn't read the whole thread, would have been throwing advice at you. I had surgery just over three weeks ago and can't be here all the time these days, didn't want you to think it was going to be easy.

---

### Post by Hippytaff on 2010-12-08
It will be a challenge...got this though
[http://www.debian.org/releases/stable/i386/](http://www.debian.org/releases/stable/i386/)
 
But there doesn't seem to be much documentation about dual booting linux, loads on windows-linux dual boot...so yeah, the grub thing is going to be fun :-)
 
If I don't break it I can't fix it :-D
 
I hope your recovering well. :-)

---

### Post by bodhi.zazen on 2010-12-08
> **Hippytaff said:**
> It will be a challenge...got this though
[http://www.debian.org/releases/stable/i386/](http://www.debian.org/releases/stable/i386/)

Ubuntu is an ancient African word for "can't install Debian"

---

### Post by QLee on 2010-12-08
[QUOTE=Hippytaff]...
But there doesn't seem to be much documentation about dual booting linux, loads on windows-linux dual boot...so yeah, the grub thing is going to be fun :-)
 ...[/QUOTE]

Don't let Lenny install legacy GRUB in the MBR, (actually, legacy GRUB can boot an Ubuntu install, I have one on an old system that I chainload to Ubuntu), you're going to be upgrading Lenny to latest versions right away and then moving on to squeeze. (Your Ubuntu OS prober can find Lenny and Squeeze  just fine.)

---

### Post by QLee on 2010-12-08
[QUOTE=bodhi.zazen]Ubuntu is an ancient African word for "can't install Debian"[/QUOTE]

<chuckle> Yup, seen that lots in Debianspace, I wouldn't have dared post it here but people won't argue with you, admin.

---

### Post by Hippytaff on 2010-12-08
> **bodhi.zazen said:**
> Ubuntu is an ancient African word for "can't install Debian"

haha - does linux mean 'won't play nice with other linux distros...but  will boot ok with windows' theres hardly any documentation on dual  booting two linux distros :-)

Cheers all, I'm going to try it anyway, in the name of...frustration and angst? :-s maybe without trying to share a home partition though.

---

### Post by QLee on 2010-12-09
Good morning!

[QUOTE=Hippytaff]haha - does linux mean 'won't play nice with other linux distros...but  will boot ok with windows' theres hardly any documentation on dual  booting two linux distros :-)[/QUOTE]
Well, by the time most users get to the stage of distro hopping with multi-boot, they wouldn't read said documentation anyway. The issue is that widely different versions of binaries can vary widely, generally new versions include new features and sometimes that means compatibility problems. (It's possible to code backward compatibility into new versions but it isn't possible to build "forward" compatibility into old versions because the new stuff wasn't thought of at the time the old version was coded.) And the bootloader stuff, multi-booting distros that use legacy GRUB with ones that use GRUB2 just take a reasonable stragety. It's a temporary issue, already many users have only experienced GRUB2 and as time goes on and newer releases emerge  only experienced users will have any of the old stuff around. It's just the point in history that you're coming back to GNU/Linux that is biting you.


[QUOTE=Hippytaff]Cheers all, I'm going to try it anyway, in the name of...frustration and angst? :-s maybe without trying to share a home partition though.[/QUOTE]

No, no, do it in the spirit of fun. ;-)

Separate homes is the safe way. While experimenting, you can rename any dot config file in the Lenny ~home and copy one from the Ubuntu ~home to see if it works, and then it would be easy to restore. That way your Ubuntu will always work upon reboot so you have it for fixing whatever happened. It's pretty easy to symlink any data from Ubuntu ~home to the Lenny/Squeeze test ~home and thus have access to it from Lenny/Squeeze. Things like music and video and text formats are still the same. Actually, by the time you've upgraded to Squeeze, the versions will probably be close enough to Ubuntu to be compatible, I just didn't want to guarantee that the ones from Lenny would be during the transition. And I didn't want to go to the trouble of analysing it closely enough to recommend anything but a safer route.

I expect you to be successful, but "if you break it, you get to keep both pieces" as the saying goes. :-)

---

### Post by Hippytaff on 2010-12-09
Tonight is the night...I'm happy that I've researched enough now and your posts have been an excellent help, thankyou. I discovered that you don't have to install grub during the Debian installation process and that ubuntu's grub2 os prober should pick up the both distros...fingers crossed. I've got a few liveCD's handy if it all goes pear shaped :-)
 
I'll let you know how it goes!

---

### Post by QLee on 2010-12-09
[QUOTE=Hippytaff]... I discovered that you don't have to install grub during the Debian installation process and that ubuntu's grub2 os prober should pick up the both distros...fingers crossed. ...[/QUOTE]
Yeah, back about post 25, eh? This thread has become long enough to be somewhat hard to follow.

[QUOTE=Hippytaff]I'll let you know how it goes![/QUOTE]
I'm sure we'll know.

Why, I might even be one to help you over in Debian forums, who knows, I only use this nick here. However, be warned, I'm actually one of the oldschool guys, I just clean up my act here.

[/Debian_support]

Over and out.

---

### Post by Hippytaff on 2010-12-09
```

back about post 25

```
yip - re-reading certainly helps...might see you in the debain forums to be torn to shreds when I ask a question that was answered three times by three seperate people in posts #2, #3 and #4 :-D
 
I'm learning to pay more attention ;-)

---

### Post by Hippytaff on 2010-12-09
So...all kind of went well, didn't install grub, booted into ubuntu after installing Debian, did update-grub, os-prober found debian. Went to boot into debian and it ahngs at

```

waiting for root filesystem

```thought it was all going a bit too smoothly...I'll jump across the the debian forums and have a read - this isn't a request for help, though if there is any available I will appreciate it, but an update just incase anyone is interested :-)

---

### Post by QLee on 2010-12-10
OK, one more.

Come on Hippy, stop smoking that stuff, while you are working. You know the drill, at the GRUB prompt for Debian, push e to edit the commands and then examine what the system is trying to do. Presumably, you know where you installed Debian and can see what is wrong with the lines.


I don't know why you chose to reboot into Ubuntu, update-grub and reboot into Lenny (as it appears you have done), I thought you were going to move to Squeeze. You know, like in post 13.
> Make sure your system is fully upgraded.
Edit your sources list and replace "lenny" if you use codenames, to "squeeze". If you use "stable", I'd still suggest you replace it with "squeeze", if you replace with "testing" you will get a big surprise next upgrade after release.
Then (I prefer to do this from a console so I'm not upgrading X from within X):
apt-get update
apt-get dist-upgrade


You can use Synaptic too, if you prefer GUI. I guess you've already figured out the no sudo stuff and are familiar with doing system tasks as su.
It's kind of hard to help you, you assured you were going to re-read and pay attention.;-) And, you answer too many posts to be asking beginner questions.

If you're just yanking my chain, well that's OK but, fool me once, shame on you, fool me twice, shame on me.

---

### Post by Hippytaff on 2010-12-10
haha, I'm naturally confused, don't need to smoke anything :-)
 
When I rebooted grub didn't see Debain, so had to update grub for the osprober to pick it up. Then I get than hang.
 
Debian is on sda3, I edited grub (by pressing e at the grub menu). I am going to update to squeeze as per post (lucky 13) as soon as this is fixed.
 
I've started a new post which has my boot sript on it [http://ubuntuforums.org/showthread.php?t=1641929](http://ubuntuforums.org/showthread.php?t=1641929)
 
I am still a beginner, (at this at least - never before tried dual booting 2 linux distros)
:-)

---

### Post by QLee on 2010-12-10
[QUOTE=Hippytaff]...
When I rebooted grub didn't see Debain, so had to update grub for the osprober to pick it up. Then I get than hang.[/QUOTE]

That was my point above, you were already in Debian, Lenny, the step-by-step would have taken you to Squeeze, which we had agreed was your target. I didn't try to cover issues outside of that path, as I mentioned, this is not the appropriate place to write all of that stuff. 
 
[QUOTE=Hippytaff]Debian is on sda3, I edited grub (by pressing e at the grub menu). I am going to update to squeeze as per post (lucky 13) as soon as this is fixed.[/QUOTE]

What fixed, can't you boot to Lenny by making appropriate changes to the GRUB lines and pushing b to boot?
 
[QUOTE=Hippytaff]...
I am still a beginner, (at this at least - never before tried dual booting 2 linux distros)
:-)[/QUOTE]

Well, one can only claim n00b for a reasonable amount of time, not just for everything new they try. The way this is proceeding, you choose to do something that will assure failure each time. Even when you've been given a workable path. I notice in the other thread you chose to slam "linux" as being at fault ("doesn't work"), even though in this thread I explained that wide version differences present problems. Then you say you're going to take the Homer Simpson Approach, when the going gets tough, quit. As I stated, you're hard to help.
  
Sometimes the most help for the person is a suggestion to think, and do better. I'm sorry if that seems harsh.

This thread has gone on far too long, I'm somewhat surprised a mod hasn't moved it.

---

### Post by Hippytaff on 2010-12-10
> 
you were already in Debian

after the install finished it automatically reboots - after that it booted straight into ubuntu bevause grub wasn't aware of Lenny until I updated grub.
 
Ill try again to alter grub so that it boots succesfully, I don't really intend to give up on this, can't let it beat me, then I can proceed with the upgrade to Squeeze (which I know how to do).
 
Noob - I've only been using linux for about 6 months (I would say that is fairly new, and I feel I've learned quite a bit already, this is another learning curve for me)
 
> 
I'm sorry if that seems harsh

This isn't harsh, you should meet my wife :-) seriously, I can take it, I prefer honesty even if it can be seen to be a bit harsh.
 
> 
This thread has gone on far too long

 
That's why I thought it would be a good idea to start a new one with the boot scripts so people can help me read it (still learning to read the boot script - though this issue is helping immensely - learning ;-) )
 
Edit -> apparently, in some instances lenny uses hdx rather than sdx, so I'll try to ammend grub accordingly (root=/dev/hda3) and see if that does it :-)
 
after work *sigh*

---

### Post by Hippytaff on 2010-12-10
Success!!!

Thanks for the stern talking to :-)

tried changing root=(hd0,dos) to root=/dev/hda3, but it didn't work. Then, after five or six attempts I realised that there was another instance of root=, which had root=/dev/sda3. Changed to hda3 voila!

---

### Post by QLee on 2010-12-11
Yes, Lenny era kernels (read that as "old" if you want to) considered IDE drives as hd(x).

Sorry, I forgot about the automatic reboot (it has been years since I installed Lenny), I suppose I thought there was a way to interrupt that reboot.

---

