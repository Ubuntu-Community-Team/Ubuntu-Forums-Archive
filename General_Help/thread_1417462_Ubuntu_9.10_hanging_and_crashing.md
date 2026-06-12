---
title: "Ubuntu 9.10 hanging and crashing"
date: 2010-02-27
forum: General Help
---

### Post by alexeix on 2010-02-27
Hi,

I have an issue with Karmic Koala, whereby Ubuntu regularly hangs/crashes and I have to hit the re-set button.
Sometimes I am then able to boot back into Ubuntu (for a while at least), but at other times I can't.

Some background details - I originally upgraded from the previous Ubuntu version and experienced these problems.
I therefore decided to do a fresh install (not an upgrade!) of 9.10 and initially all looked well, but now the same issues have returned.

One example of recognising an oncoming crash/hang, is when I'm browsing the internet using Firefox and it continually starts/stops hanging, then the browser will crash. When I restart it, there's a message saying that there is already an instance of Firefox running, but when I check, there are NO Firefox processes.

The system is pretty much unusable and I'm getting bored with it very quickly, as it's too unstable for me to continue with.

Are there any suggestions for troubleshooting the problem?
Losing patience with Ubuntu... :o(

Thanks in advance.

---

### Post by Enigmapond on 2010-02-27
What version of FF do you have? If you haven't upgraded to 3.6, I would and if ever you get that "another instance" message, you can always go to the system monitor and kill that instance of FF. Another way is to hit Alt + F2 and run 

```
killall firefox
```

Hope this helps.

---

### Post by alexeix on 2010-02-27
I'm not sure.  It wouldn't reboot at all earlier (sending this from my Windows7 laptop).

It's the default version of Firefox, plus whatever automatic updates have been applied (they're up-to-date).
I haven't done a manual installation of Firefox.

Thanks for the suggestion, but unfortunately I don't think it's a solution.
I suspect this is just a symptom of a deeper problem in Ubuntu.
Firefox doesn't need to be open for my machine to hang.

Anyone have any suggestions for how I can investigate the cause?

---

### Post by alexeix on 2010-02-28
Can anybody offer any advice on this issue?

This is a last ditch attempt, before I try another distro (and hope it works).

Today, when booting up the PC, I saw the following error:
Error: biosdisk write error
failed to boot default entries
press any key to continue


I switched it off and left it for a while. When I came back later, after several attempts and a filesystem check, the PC booted again (using it to typre this), but I know it's only a matter of time before the PC goes down, since Firefox has already crashed.

I'm using Opera right now.

Next stop Fedora???

---

### Post by chowdhury.indranil on 2010-03-01
Hello, I am using Ubuntu 9.10. I like it and mostly it is fast but I will be in the middle of something and all of a sudden there is no response from the keyboard or cursor. The cursor moves on the screen but is not recognized and I have to do a hard shut down and start all over. Anyone else have this problem and found a cure?

I'm facing this problem, speciaaly when i am watching something in youtube. also sometimes it happens when update manager suddenly starts. no icon appears for update manager in the panel. 

pleae help.
indranil.

---

### Post by chowdhury.indranil on 2010-03-01
> **chowdhury.indranil said:**
> Hello, I am using Ubuntu 9.10. I like it and mostly it is fast but I will be in the middle of something and all of a sudden there is no response from the keyboard or cursor. The cursor moves on the screen but is not recognized and I have to do a hard shut down and start all over. Anyone else have this problem and found a cure?

I'm facing this problem, speciaaly when i am watching something in youtube. also sometimes it happens when update manager suddenly starts. no icon appears for update manager in the panel. 

pleae help.
indranil.
I shoulkd add there was no such problem in ubuntu 8.04, i've started missing 8.04, should have not upgraded to 9.10.
thanks
indranil.

---

### Post by alexeix on 2010-03-01
This is exactly the same problem as I'm experiencing.

Having re-installed 9.10 yesterday, all looked good, however, this evening I booted up the PC and it hung pretty much straight after booting to the desktop.

Getting p*ssed off now and I presume there's some kind of incompatibility with my hardware (Shuttle SN95G5v2, AMD Athlon64 3200, 1GB DDR RAM, 500GB Samsung HDD).

I can't use the PC, so will have to install an alternative OS.

---

### Post by Josebas on 2010-03-09
Hi Alexeix!
I have a Shuttle St20g5 and I after installing Ubuntu for the first time (9.10) it went ok for a couple of days but now it starts to crash randomly too; using firefox, rhythmbox etc... Then I tried to install 8.04 ltc looking for a bit of stability but it didnt even load fully after instalation, also getting tired of ubuntu... 

The funny thing is that the PC I installed ubuntu in needed a format anyway so I instlled Ubuntu in the whole HDD. Now I cant reinstall windows :confused: since it does not recognize the HDD. There are plenty of threads about restoring the partition before the ubuntu installation but not if ubuntu has been installed in the whole HDD!!!

Any help/hope somewhere? Thanks!

---

### Post by alexeix on 2010-03-09
Hi there,

I installed the latest version of Linux Mint and it seems to be working fine.
I've had one instance where it crashed/hung, but otherwise it's been great.

I also had some difficulties installing it (I/O errors), but when I chose the whole hard drive option, it went through fine.

I did wonder if this problem might relate to the use of the ext4 file system, but really, I have no idea.

You should still be able to re-install Windows on the hard drive, but you'll need full install discs (i.e. not upgrade).
Don't you have those?

---

### Post by RT236 on 2010-03-13
Just thinking here... might want to be sure your main memory is OK. I just went through this here with one my custom desktops I built up. Passed mem tests OK, but one mem module was still bad, did not show bad during mem testing. I had noticed mem test and System Monitor were only showing 512mb than 1gb mem. System only hung on reboot and during install from live disk at reboot, and a few lockups. ...did mem module swaps and then one at a time, isolated bad mem module. All works OK now for 9.04 and 9.10.

Over the past couple of months the system had gotten flaky with a few occasional hangs. I had run mem test then, but had not noticed only half of my mem was recognized. I thought it strange mem test had not picked up bad mem module. Sounds to me like one address line was bad in my mem module.

I have no idea if this is of help to you, but was just thinking of this when I saw your problem.

---

### Post by alexeix on 2010-03-13
Thanks for the suggestion, but my memory is showing as the full 1GB and I'm now running Linux Mint without any issues.

I've no idea why it works, when Ubuntu doesn't, but I don't have the time to spend investigating at the moment.

Weird problem!

---

### Post by woodmaster on 2010-03-14
these sound like graphics crashes.  If you can still move the mouse, it's the x.org driver, not FF.  check this out.  It worked for me:)
[*http://ubuntuforums.org/showthread.php?t=789578 			*]("http://http://ubuntuforums.org/showthread.php?t=789578")
Hope it helps

---

### Post by gatordude on 2010-03-20
I am having similar issues also.
I purchased a new quad system and I installed 9.10 on it. After install my screen was flickering terribly and after I updated I installed the ATI/ AMD graphics drivers (FGLRX) and the screen flicker went away.

I am still having the freezing issue that is very random. I can go either a few minutes with minimal web surfing (FF) or I can have many windows open (doc viewers, FF, Oregano...) and it will run for a long while then freeze. Then it either turns off by itself or comes back but its very slow and I have to reboot.

System consists of: Biostar TA790GXE MB
                             AMD Athlon II X4 630 2.8Ghz AM3 CPU
                             OCZ Vista Performace Ed. 4096MB PC6400
                             OCZ 600W PS
                             Seagate (WD) 500G HD ( factory replacement of a failed drive)

I only have items installed from the normal repository.

Any ideas?

---

### Post by RT236 on 2010-03-20
> **gatordude said:**
> I am having similar issues also.
I purchased a new quad system and I installed 9.10 on it. After install my screen was flickering terribly and after I updated I installed the ATI/ AMD graphics drivers (FGLRX) and the screen flicker went away.

I am still having the freezing issue that is very random. I can go either a few minutes with minimal web surfing (FF) or I can have many windows open (doc viewers, FF, Oregano...) and it will run for a long while then freeze. Then it either turns off by itself or comes back but its very slow and I have to reboot.

System consists of: Biostar TA790GXE MB
                             AMD Athlon II X4 630 2.8Ghz AM3 CPU
                             OCZ Vista Performace Ed. 4096MB PC6400
                             OCZ 600W PS
                             Seagate (WD) 500G HD ( factory replacement of a failed drive)

I only have items installed from the normal repository.

Any ideas?

I've had somewhat similar wherein FF appears to be hogging more and more resources.  I've had other times wherein System Monitor was hogging resources.

I recently went to 2GB mem and for me the problem seems less.  I do know what you mean, working along fine, and then it suddenly slows down.  I've done a kill on FF a few times and that seemed to get me back OK.  If you look around on the forums (I'm sure you already did) you'll see some talking about issues with FF and also System Monitor causing some strange problems.

During these times I've noticed my two CPUs were pegged as fast as they could go and my memory was about 90% utilized (before I had 2GB mem), and swap was used, I forget the % utilization for swap.  Sometimes when I got things going again I was running in a degraded mode of some sort, responsiveness was sluggish, so I would reboot.

I was reading one report where they said if they rebooted several times the problem seemed to clear.  I wish I had an answer,  just sharing I've had the same happen and read others taking about it...  I went to 2GB mem (when I replaced a bad mem module) as I wanted more mem, I've not had it since, but I'm not saying that is the cure...  I had replaced that mem module because of reboot hangs during BIOS startup.

PS:  On another note, I installed the FasterFox 3.70 extension by ccman972 and that has helped me a lot with faster FF results on searches.

Just thought of this...  If you suspect FF is problem you might want to try Swiftfox. I did that once on an earlier release of Ubuntu and FF, and Swiftfox solved the problems I was having back then.  In fact, I think I might try Swiftfox again now.

Update:  I'm using Swiftfox 3.6 now and I find I am not getting hangs or unresponsiveness.  I'm using the Intel version.  I have a P4 3GHz dual core with 2GB mem.  I just added it to my repositories, etc. and am using it now by default for my browser.

I figured I'd share FYI what I've experienced.

---

### Post by gatordude on 2010-03-20
FF seriously? WOW!

Well I guess I could run with scissors and try Chrome or Opera!

---

### Post by alexeix on 2010-03-20
I'm trying Swiftfox too.  I already had Opera installed, but now that I've uninstalled Firefox, I'll see what happens.

Cheers.

---

### Post by RT236 on 2010-03-20
> **alexeix said:**
> I'm trying Swiftfox too.  I already had Opera installed, but now that I've uninstalled Firefox, I'll see what happens.

Cheers.

Yep, I loaded Swiftfox early today.  In my case I left FF installed since I had it so customized, addons, etc., so just loaded the repository, etc. for SF so I could use my FF setup.  Since I did that I've not had one hang, crash or anything.  I'm amazed and quite pleased.  I hope it keeps working.  Hope it helps you and the other poster that had similar problems with hanging/crashing.  Good luck!

---

### Post by gatordude on 2010-03-21
I installed a new browser (Chrome) and removed the System monitor from the panel and I have been using (over using actually) as many applications at once and have not had an issue for over 8 hours.

From an earlier post I thought I was having memory issues cause by caching. But after running across this post it may have been FF and the monitor all along.

Does anybody know if a plain Firefox install with no add-ons has these issues? I had FF loaded how I liked it with many add-ons and I wonder if a certain add-on or a combination of them is causing this.

---

### Post by alexeix on 2010-03-21
I think the only Firefox add-on I was using was for flash.
Maybe some other multimedia-type ones too, but only ones which i would have been prompted to apply, when browsing internet content, e.g. for watching embedded video, playing music, etc.

I'll reserve judgement until this has been working cleanly for a week or so, since the problem happened a lot less for me since switching to Linux Mint.

Oops.

I may well change back to Ubuntu if this resolves it though.

Version 10 is looking good.

---

### Post by dprestemon on 2010-04-01
The Karmic Koala problem is not with Firefox.  It only seems like it because, if you are like me, Firefox is usually running no matter what else you are doing.  I have used both Opera and Chrome.  Same problem -- random freezes anywhere from 10 seconds to two hours into a session.  

On my system, the pattern is always the same.  First, the mouse buttons stop working on links, even though they can still be used on the desktop and the cursor can be moved normally.  Then I click on the "System" menu and see that the icons have disappeared from the applet listing.  At that point, I know I am SOL.  If I click on an applet, I get a message box saying that it could not be started.  Shortly thereafter, the icons disappear from the main panel and the desktop.  

The problem is clearly with the GUI.  In the background, Ubuntu is running normally.  I just can't get to it without opening a terminal window.  Even then, the Gnome applets remain unavailable.  So, I reboot.

Absolutely no messages are generated in any of the log files when this happens, by the way. Between the completion of the original boot and the message reporting the restart, there is nothing.

Also, I have 2 GB memory, all new and healthy.  No problems running Windows XP or Ubuntu 8.04.   

Any ideas?

---

### Post by alexeix on 2010-04-01
I made the decision to change to Kubuntu and am very happy.
I still removed Firefox and installed Swiftfox instead.

Since doing this, I have not seen a single instance of this issue and everything has been running very smoothly.

I can't say for certain what the cause was, but I'm pleased with my new set-up.

---

