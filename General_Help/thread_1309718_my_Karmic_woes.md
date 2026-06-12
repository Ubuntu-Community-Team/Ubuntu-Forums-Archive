---
title: "my Karmic woes"
date: 2009-11-01
forum: General Help
---

### Post by michaelzap on 2009-11-01
Alrighty there are already a lot of threads with complaints and diatribes, so I'm not going to go there. I'm actually going to do everything that I can to stick with Karmic and work out the bugs that I've had, since it really does show great promise. So far, however, my computer is too unstable to use, and that's not just a minor gripe.

Bugs affecting me:
[LIST]
[*]Random freezing requiring complete hard reboot
[*]Presistent Flash issues, sometimes also provoking complete system freezes
[*]No 5.1 sound from my laptop speakers
[*]Forced to disable my modem in order to get any sound (I don't care much about this, however)
[*]Not possible to resume from suspend/hibernate
[*]Error message at boot up regarding not being able to mount the swap partition (possibly due to the encrypted home directory?)
[*]Adding applications/commands to Startup Applications doesn't make them start up on login
[*]Editing the Grub2 config has no effect
[*]Occasionally software that loads at boot will freak out, with the most dramatic example being Gnome Do using all of my CPU until I kill it (it shows up to 200% CPU use in the System Monitor - never seen that before! maybe it's 100% of both cores?)
[/LIST]

On the bright side, in some ways my audio works better than it did in 9.04 (no glitches when playing from multiple sources), my display driver seems to work much better (no random dimming or ugly tearing), and overall Karmic feels snappy (when it works).

My machine is a Lenovo Y530 (Core2Duo) with integrated Intel video and sound running a fresh installation of Karmic x64 with an encrypted home directory and separate Vista and system restoration partitions.

Anyone have any advice or tips for me? How about others with similar experiences? Maybe we can work out some of these issues here together.

---

### Post by commonplace on 2009-11-01
> **michaelzap said:**
> How about others with similar experiences? Maybe we can work out some of these issues here together.

I'm afraid that's all I have to offer: solidarity. I don't have any solutions, but I have most of the same problems and on the same machine (Lenovo IdeaPad Y530). Hoping to find some fixes. :)

/Kevin

---

### Post by Roasted on 2009-11-01
I cannot provide anything positive here in terms of resolving your issues, but just to throw in a "you're not alone" post here, I'm having issues with Karmic as well. I run 4 hard drives in my system. 2 for me (1 main 1 backup) and 2 for network storage (1 main with samba and 1 backup).

In short - I need multiple drives in my main desktop. Not having them just kills the possibility of running that OS. Period. And when I went to install Karmic, it failed to recognize my drives properly. I unplugged them and decided to just install Karmic with 1 drive installed and add the others later, but that was a disaster. I pulled my /etc/fstab file from my old install on 9.04 that worked fine, yet on 9.10 it failed to mount drives properly. Further reviews about Karmic revealed others were having the same issue.

The reality is, 9.04 is very stable and reliable for me, so I'm sticking with it. If I don't ever get to use 9.10, oh well. The next release is an LTS release anyway, so I'm already excited about that.

But the bottom line is, I'm keeping faith in the Ubuntu developers out there. They always do a killer job, so I'm sure they'll fix it. After all, Karmic has only been out for DAYS. At least we don't have to wait a year for a system to stabilize, like our MS friends. :P So we'll have to see what happens today, tomorrow, next week, etc. But I'm sure it'll get fixed up.

---

### Post by michaelzap on 2009-11-01
@Kevin: Solidarity is always welcome. Maybe we'll be able to help each other out. I'm always amazed by how the biggest computer problems are usually solved with a really minor tweak.

@Roasted: I don't have multiple drives (having only installed Karmic on a laptop so far), but I believe that issue is caused by Grub2. I think that you could probably go back to legacy Grub and get your drives to mount in Karmic if you wanted to try that. Search the forums for more info (from people who've actually done it).

---

### Post by hal8000 on 2009-11-01
I 've only used karmic about an hour so not had thorough time to test.
For me I've had no instability but just long boot time.

My first tuneup was to change from grub 2 to grub 1.

Next tip is to install sysv-conf-rc

Running  sysv-rc-conf allows you to turn off services you dont need, however caution is
needed as if you disable a service needed at boot , you will be reinstalling.


For example if you dont use bluetooth then disable bluetooth.

Only make one change at a time and reboot, luckily a thread exists already

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

although a little old, you need to use google to research other services.

Instability can be many things, but probably software, so by tuning your boot,
you will be running less processes some of which may possibly interact with
something else on your system.

I've not tweaked my system yet but am currently dual booting both karmic and hardy,
hope that helps.

---

### Post by Roasted on 2009-11-01
> **michaelzap said:**
> @Kevin: Solidarity is always welcome. Maybe we'll be able to help each other out. I'm always amazed by how the biggest computer problems are usually solved with a really minor tweak.

@Roasted: I don't have multiple drives (having only installed Karmic on a laptop so far), but I believe that issue is caused by Grub2. I think that you could probably go back to legacy Grub and get your drives to mount in Karmic if you wanted to try that. Search the forums for more info (from people who've actually done it).

I don't believe it has anything to do with Grub. In the partitioning screen of Karmic, it's evident Karmic has no idea what drives are which. It has my pair of 250gb drives mapped together as if they are RAID. My motherboard doesn't even support RAID, so I couldn't rig up RAID if I tried. Secondly, if I boot into Hardy/Intrepid/Jaunty, it brings up all of my hard drives just fine. One after another. sda, sdb, sdc, sdd. At this point, Grub isn't even in the picture, which is why I think the issue lies within Karmic itself.

---

### Post by commonplace on 2009-11-01
Alright, here's something weird (at least, to me): I wiped out everything and installed **K**ubuntu 9.10 -- and it works great. Sound works. No freezes. No kernel errors. No speed issues. Everything is great.

I don't understand why this is, unless my issues were specific to GNOME...?? That doesn't really make sense to me, but it's the only explanation I have at the moment. I mean, this is the same kernel... so it's not the kernel, apparently.

I prefer KDE over GNOME but I'm going to stick with this for awhile and adapt -- it's better than having an unusable GNOME-based system (Ubuntu).

/Kevin

---

### Post by itlarson on 2009-11-01
As a refugee from kde 3.5 I have been using xubuntu.  It actually has the ability to remember what apps were open last time you used it unlike gnome, and the taskbar autohide is reasonably fast and complete.  I just upgraded to karmic, and so far it has been bug free, although I am using a low- spec desktop, not a laptop.

---

### Post by Roasted on 2009-11-01
> **commonplace said:**
> Alright, here's something weird (at least, to me): I wiped out everything and installed **K**ubuntu 9.10 -- and it works great. Sound works. No freezes. No kernel errors. No speed issues. Everything is great.

I don't understand why this is, unless my issues were specific to GNOME...?? That doesn't really make sense to me, but it's the only explanation I have at the moment. I mean, this is the same kernel... so it's not the kernel, apparently.

I prefer KDE over GNOME but I'm going to stick with this for awhile and adapt -- it's better than having an unusable GNOME-based system (Ubuntu).

/Kevin

Ironically, I tried to install Kubuntu 9.10 in Virtualbox, but Virtualbox pulled support on installing Kubuntu 9.10 because there was an issue with KDE.

That's at least what I've read. Not sure how accurate it is. But I know one thing - Kubuntu 9.10 won't install on my Virtualbox.

---

### Post by autocrosser on 2009-11-01
I can't help on all fronts, but look here for the sound "fix": [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

Grub2 has a very good tutorial in the Tutorials & Tips forum that will really help there....

I really recommend to anyone that is having problems to look thru the (closed) testing forum--we covered quite a bit of what you are having before--- [http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

---

### Post by michaelzap on 2009-11-01
> **autocrosser said:**
> I can't help on all fronts, but look here for the sound "fix": [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

Grub2 has a very good tutorial in the Tutorials & Tips forum that will really help there....

I really recommend to anyone that is having problems to look thru the (closed) testing forum--we covered quite a bit of what you are having before--- [http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

Thanks for your help, autocrosser. Unfortunately I already tried those audio fixes and I've edited my Grub2 config file according to that guide but it doesn't affect how Grub2 works. I also did read the Karmic testing forums a lot in the run-up to the final release, and of course those threads are still available in search results.

---

### Post by michaelzap on 2009-11-01
> **commonplace said:**
> Alright, here's something weird (at least, to me): I wiped out everything and installed **K**ubuntu 9.10 -- and it works great. Sound works. No freezes. No kernel errors. No speed issues. Everything is great.

I don't understand why this is, unless my issues were specific to GNOME...?? That doesn't really make sense to me, but it's the only explanation I have at the moment. I mean, this is the same kernel... so it's not the kernel, apparently.

I prefer KDE over GNOME but I'm going to stick with this for awhile and adapt -- it's better than having an unusable GNOME-based system (Ubuntu).

/Kevin

Very interesting indeed! I may have to install KDE to see how it goes. That actually makes me think that perhaps this bug won't be so hard to resolve...

---

### Post by michaelzap on 2009-11-07
Dedicating a little time today to trying to resolve this...

Reverting to the Intrepid Intel video drivers didn't work for me. I wasn't able to enable compositing or Compiz using it. I didn't actually try it out for long enough to see whether my laptop keeps crashing (since I want Compiz), so I suppose it might have worked in that sense (if what I'm experiencing is a GPU lockup).

Now I'm running the latest Release Candidate for the kernel (2.6.32-rc6) as found here:
[http://ubuntuforums.org/showpost.php?p=8263419&postcount=135](http://ubuntuforums.org/showpost.php?p=8263419&postcount=135)

I have hopes that this will work! I won't really know for sure until my laptop goes a few hours without crashing.

---

### Post by michaelzap on 2009-11-07
Progress report so far::
[LIST]
[*]Random freezing requiring complete hard reboot[COLOR="Blue"] - still testing the new kernel RC to see if this resoves the crashes[/COLOR]
[*]Presistent Flash issues, sometimes also provoking complete system freezes[COLOR="Blue"] - now running Flash from the repos instead of the Adobe alpha; have the issue of difficulty clicking on controls and buttons but no more crashes and segmentation faults[/COLOR]
[*]No 5.1 sound from my laptop speakers[COLOR="Red"] - still not resolved[/COLOR]
[*]Forced to disable my modem in order to get any sound (I don't care much about this, however)[COLOR="Red"] - still not resolved, and still don't care[/COLOR]
[*]Not possible to resume from suspend/hibernate[COLOR="Blue"] - still need to test this[/COLOR]
[*]Error message at boot up regarding not being able to mount the swap partition (possibly due to the encrypted home directory?)[COLOR="Red"] - the error message is more verbose with the new kernel, but the boot time slowdown is the same[/COLOR]
[*]Adding applications/commands to Startup Applications doesn't make them start up on login[COLOR="Blue"] - this is resolved using the workaround [here]("http://ubuntuforums.org/showpost.php?p=8171569&postcount=4") (and if you hate the bootup spotlight as much as I do, try the wallpaper daemon script mentioned [here]("http://www.omgubuntu.co.uk/2009/11/desktop-wallpaper-as-xsplash.html"))[/COLOR]
[*]Editing the Grub2 config has no effect[COLOR="Blue"] - this seems to have been fixed by an update[/COLOR]
[*]Occasionally software that loads at boot will freak out, with the most dramatic example being Gnome Do using all of my CPU until I kill it (it shows up to 200% CPU use in the System Monitor - never seen that before! maybe it's 100% of both cores?)[COLOR="Red"] - still not resolved, but not critical[/COLOR]
[/LIST]

---

### Post by michaelzap on 2009-11-07
> **michaelzap said:**
> Progress report so far::
[LIST]
[*]Not possible to resume from suspend/hibernate[COLOR="Blue"] - still need to test this[/COLOR]
[/LIST]

Still not resolved. My laptop actually will not suspend or hibernate, even with the RC6 kernel. Need to look for other solutions or wait for the final kernel.

---

### Post by michaelzap on 2009-11-08
Update: I was able to run my laptop using the Release Candidate kernel (2.6.32-rc6) for 24 hours without a single crash! That was by far the most productive that I've been in Ubuntu since Karmic came out. But then Update Manager told me that there was a kernel update to install (2.6.31-15), so I tried it out. My laptop crashed using that kernel within 20 minutes, so I'm back on 2.6.32-rc6. I encourage anyone who's having crashes or freezes to give it a try.

---

### Post by michaelzap on 2009-11-11
Hooray! I was able to get my Lenovo Y530 surround sound working by adding 
options snd-hda-intel model=lenovo-sky
to the end of
/etc/modprobe.d/alsa-base

as described in [this old thread]("http://ubuntuforums.org/showpost.php?p=5460960&postcount=2").

---

### Post by michaelzap on 2009-11-11
Also fixed the Flash problem of not being able to click on controls using this method:
[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

I'm using the Flash from the Karmic distros instead of the 64-bit alpha from Adobe's site, since that caused Firefox to crash whenever I loaded Gmail (as I do constantly).

---

### Post by railgrinder762001 on 2009-11-13
I dont know if this helps, but i had the freezing problem too. I went nuts for about 2 weeks trying to get it to stop freezing. Im not going to get into details about what all i did, but i eventually fixed it ( i think ) by running MEMTEST,  and i had to switch my ddr2 ram out for just plain old ddr ram. So i at least am going to suggest running MEMTEST to see if you have any errors. I don't know if it will fix everything  but since i ran it and put different ram in  it hasn't froze once. Memtest should be part of your installation cd if you cant find it i would google it. Google finds everything. lol

---

### Post by michaelzap on 2009-11-14
> **railgrinder762001 said:**
> I dont know if this helps, but i had the freezing problem too. I went nuts for about 2 weeks trying to get it to stop freezing. Im not going to get into details about what all i did, but i eventually fixed it ( i think ) by running MEMTEST,  and i had to switch my ddr2 ram out for just plain old ddr ram. So i at least am going to suggest running MEMTEST to see if you have any errors. I don't know if it will fix everything  but since i ran it and put different ram in  it hasn't froze once. Memtest should be part of your installation cd if you cant find it i would google it. Google finds everything. lol

Good general advice to check RAM. In my case it was just the Karmic kernel (or included drivers) that don't like my hardware, since it works with Jaunty, Vista, and other systems. I'm running the 2.6.32-RC7 mainline kernel now and it doesn't crash at all anymore.

---

### Post by growlf on 2009-11-19
I have an Acer Aspire One ZG5, and had been struggling with sound and video issues (crackling and slugishness/blankout respectively) on Jaunty. I finaly had decided to upgrade because the screen blankouts were getting to the point that I could not work effectively.

Well, with the one exception of the login screen config issue over the userlist (thank you @michaelzap !! for your help there) - I am here to report everything WORKS.  Well.  ..and correctly.  No issues or holdbacks.  It has only been a little over 3 days, but I have pushed every envelope I can think of, and all checks out.  Wireless even has lights without me doing any backport shinanigans.

So.. there's that.  :)

---

### Post by michaelzap on 2009-11-19
> **growlf said:**
> I am here to report everything WORKS.

Excellent - I may have to get an Acer Aspire One...

---

### Post by michaelzap on 2009-12-02
So thanks to the udev update that fixes USB automounting I've also now got the [pulseaudio memory leak]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655") that causes pulseaudio to grow in size to gigs and gigs of RAM. For now I'm just entering "killall pulseaudio" every hour or so, since the only other fix (reverting to the old udev package) disables USB automounting. DoubleplusUNCOOL!

---

### Post by DarkDead on 2009-12-02
[LIST]
[*]Adding applications/commands to Startup Applications doesn't make them start up on login
[/LIST]
I was also having this issue. I have gnome configured to start session automatically and for some reason it was set to failsafe mode. Moments ago I logged off, noticed this, changed to normal mode and now everything is working.

---

### Post by michaelzap on 2009-12-02
> **DarkDead said:**
> [LIST]
[*]Adding applications/commands to Startup Applications doesn't make them start up on login
[/LIST]
I was also having this issue. I have gnome configured to start session automatically and for some reason it was set to failsafe mode. Moments ago I logged off, noticed this, changed to normal mode and now everything is working.

Interesting. I thought it was just a bug in the GUI.

---

### Post by michaelzap on 2009-12-03
The final version of kernel 2.6.32 is out! Instructions for getting it and installing it are [here]("http://ubuntuforums.org/showpost.php?p=8435578&postcount=27"). So far it works as well as the last three Release Candidates did for me (which is to say, a whole lot better than 2.6.31, which is a train wreck on my laptop).

---

### Post by Mike BFD on 2010-02-26
An interesting issue, gentlemen.

My wife used Ubuntu 9.04 and it used to get frozen sometimes. Upgrading to 9.10 resulted in freeze at bootup so she returned to 9.04... But installing newer kernels (2.6.32 and then 2.6.33) lead to the same freezing at bootup!

2 questions regarding to that:
- Any ideas why a new kernel which helped so many people here works, in my case, in just the opposite way?
- Please can anybody tell a stupid newcomer how to UNinstall kernel?

Thanx!!

---

### Post by michaelzap on 2010-02-26
> **Mike BFD said:**
> An interesting issue, gentlemen.

My wife used Ubuntu 9.04 and it used to get frozen sometimes. Upgrading to 9.10 resulted in freeze at bootup so she returned to 9.04... But installing newer kernels (2.6.32 and then 2.6.33) lead to the same freezing at bootup!

2 questions regarding to that:
- Any ideas why a new kernel which helped so many people here works, in my case, in just the opposite way?
- Please can anybody tell a stupid newcomer how to UNinstall kernel?

Thanx!!

If you installed the kernel via a deb file, you can uninstall it in Synaptic (sort by Origin and look in Local/main). You can also just not choose it from the grub menu, of course. I imagine that the newer kernel won't work with Jaunty because of the many changes to the hardware abstraction layer and grub2 (and probably other things that would conflict with the other software in Jaunty).

---

### Post by Mike BFD on 2010-02-26
> **michaelzap said:**
> If you installed the kernel via a deb file, you can uninstall it in Synaptic (sort by Origin and look in Local/main). You can also just not choose it from the grub menu, of course. I imagine that the newer kernel won't work with Jaunty because of the many changes to the hardware abstraction layer and grub2 (and probably other things that would conflict with the other software in Jaunty).
Thank you, I'll try that in Synaptics.
Just too lazy to enter grub menu every time I restart...
However, 9.10 Karmic Strange Bear (equipped with a newer kernel, I believe, and "more compatible" to it) has never started up on that machine...
I mean, it's not about a conflict between new kernel and old Jaunty, I guess.

---

### Post by Mike BFD on 2010-02-27
...Yes, that's quite easy in Synaptics.
And also I noticed, Karmic also uses "27" and "28" kernels, not younger

---

### Post by michaelzap on 2010-03-20
Getting ready to pull the plug on Karmic. For the last six months I've soldiered on with it, but it never really worked properly on my main laptop. So I thought I'd provide a bit of a wrap-up to this thread.

Problems that I still have:

[LIST]
[*]Not possible to resume from suspend/hibernate - This is a serious enough issue to make me not use this distro.
[*]Pulseaudio memory leak - Another big issue. I have to killall pulseaudio at least once an hour or it grows to consume 2 GB of RAM or more. And once I kill it, running applications can no longer play sound until they're restarted.
[*]Running hot/excessive fan activity - I didn't mention this previously, but I'm pretty sure that my laptop is running far too hot on Karmic, which may be related to the Pulseaudio memory leak.
[*]Error message at boot up regarding not being able to mount the swap partition (possibly due to the encrypted home directory?) - This is just an annoyance that adds twenty or so seconds to my boot time
[*]Gnome Do frequently locks up at boot and uses all of my CPU until I kill it - Another annoyance
[*]Forced to disable my modem in order to get any sound - Doesn't matter to me, but it might to others.
[/LIST]
Plus in general Karmic feels sluggish to me. This could be related to the assorted issues mentioned above, or it might just be a symptom of increasing bloat. It's not a fresh installation anymore, of course, but I don't remember it ever feeling as snappy as Jaunty did.

I just tried the Lucid beta on this laptop and it seems to run much better (no fan noise and much quicker boot and response). But suspend (now "Sleep") still doesn't work, and I feel like six months of never putting my laptop to sleep is about as long as I'd like to go without that feature. So for now I think I'll be trying out Debian and seeing how that goes, although I'll test Lucid again once it's final.

Kind of a drag, since I definitely have tried hard to make Ubuntu work on this laptop.

---

