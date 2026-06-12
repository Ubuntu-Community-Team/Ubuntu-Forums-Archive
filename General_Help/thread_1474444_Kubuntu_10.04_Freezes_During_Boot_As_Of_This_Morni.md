---
title: "Kubuntu 10.04 Freezes During Boot As Of This Morning"
date: 2010-05-06
forum: General Help
---

### Post by robertv on 2010-05-06
I have had Kubuntu 10.04 installed and running fine for a few days now. However, this morning when I attempted to boot it froze on the blue Kubuntu screen with the five dots. None of the dots illuminated, it just appeared to show the first image statically. After a few minutes still nothing had happened. I have repeated this 3 times and each time it behaves the same. Trying to switch to a different console did not work, so I couldn't get any text output as to what exactly was going on, if anything.

If it matters I have an ATI graphics card, and am using the drivers suggested by the Hardware Drivers application.

I am currently using a Live CD to post this. Let me know if you want any specific information about the system.

---

### Post by sourcerh on 2010-05-08
I'm experiencing exactly the same problem as you...

I'm writing from another laptop.

Have you found a way to solve this critical problem ?

For now, I let the laptop run all this day, hoping this blue screen will disappear...

The fact is, some days before, ubuntu has checked the disks, and it has taken a very long long time... (a thing that was taking a couple of minutes before upgrading to 10.04...)


Why have I upgraded to this crappy 10.04 so quickly.... rha...

---

### Post by robertv on 2010-05-08
So far my only solution is forcing a reboot when the screen shows by hitting the power button on my PC. After a few times it's like Kubuntu finally gives in and let's me boot :P That's dreadful for usability.

If the disk check is what is causing this, shouldn't a message be displayed on screen to let the user know? Also, I've left it on that screen for far longer than a disk check ever took on 9.10. That suggests to me that a disk check isn't causing it.

---

### Post by kacm88 on 2010-05-10
Hello, I've been having the same problem booting. I installed 10.04 on Saturday, it was working until this afternoon. I get the Kubuntu loading screen with the dots, and after that it shows me a black screen with a cursor and it freezes. Weird thing is that sometimes this happens but sometimes it doesn't.

If I press shift, I can see the GRUB loader and I can load Kubuntu but it shouldn't be this way.

---

### Post by RJARRRPCGP on 2010-05-10
Sounds like slowly failing hardware. (The motherboard or HDD.)

---

### Post by fuzzyworm on 2010-05-15
I'm having the same problem, and I really hope it's not failing hardware - it's all brand new!

It only does it to me when I switch on for the first time - restarts, either soft or hard, don't trigger it.

Also, it never happened in 9.10 - it was only after I upgraded to 10.04.

I too have an ATI Graphics card - maybe that's the problem. I might try disabling the proprietary hardware.

---

### Post by Azazelus on 2010-05-15
I guess it is not related to any particular graphic card. I am having the same problem on nVidia. What is strange is that it's completelly non deterministic - sometimes system starts up without problems, somethimes it hangs.

This issue didn't show up after upgrading to 10.04, i would rather blame one of the recent updates.

---

### Post by Azazelus on 2010-05-30
Any news? 
For several days problem seemed to disappear, but today I've had to go through 5 or 6 restarts before being able to log-in. Sometimes it didn't hang on blue kubuntu startup page, it started Xs but apparently some invalid driver was loaded (artifacts on the screen, very slow response time, eventually freezing).

I went through grepping all the logs but didn't find anything interesting. To be honest I'm not sure what should I look for...

---

### Post by ganda99 on 2010-05-30
Count me in. I'm having the same issue. After it (Kubuntu) stops booting I get dropped into a blank screen with no disk activity, I hit CTRL-ALT-DEL and a Kubuntu splash pages comes up immediately and then the PC shuts down and reboots. 

After doing this once or twice after a cool start I eventually get my login screen.

---

### Post by ezsit on 2010-05-30
I have the exact same problem under Ubuntu, Kubuntu, and Xubuntu on both my computer and my daughter's computer. This has been happening to me since release day and I've been waiting for an update to fix it. Still no joy. I assume its a Plymouth problem since Plymouth is the newest kid on the block to take over bootup. Usplash never gave this type of problem. I don't run any proprietary graphics drivers, just whatever comes stock with a regular Ubuntu install on Nvidia graphics hardware, so I assume its Nouveau now. I doubt it's hardware related. I went back to Karmic. No problems!

---

### Post by takaratiki on 2010-06-10
Same issue as stated before. Began approximately five days ago, seemingly random lock ups when running the kubuntu blue screen. Did not occur before. Multiple restarts seem to be the only solution. Canceling a disk check also seemed to help the time that one popped up, but who is to say it is not coincidental? Nvidia graphics, newer laptop. Booting in safe mode shows no discernible problems. Log files seem ambiguous though I've seen:

plymouth-stop pre-start process (1296) terminated with status 1

in the syslog followed by some grim Xserver can not start message.

---

### Post by lavinog on 2010-06-10
My system has been freezing during boot this morning.
Last night there was an update (Most of these are proposed packages)
```


Start-Date: 2010-06-10  00:02:01
Upgrade: libkrb5-3 (1.8.1+dfsg-2, 1.8.1+dfsg-2ubuntu0.1), libk5crypto3 (1.8.1+dfsg-2, 1.8.1+dfsg-2ubuntu0.1), libido-0.1-0 (0.1.5-0ubuntu1, 0.1.6-0ubuntu1), kpackagekit (0.5.4-0ubuntu4, 0.5.4-0ubuntu4.1), evolution-plugins (2.28.3-0ubuntu9, 2.28.3-0ubuntu10), evolution (2.28.3-0ubuntu9, 2.28.3-0ubuntu10), libecal1.2-7 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), xserver-xorg-core (1.7.6-2ubuntu7, 1.7.6-2ubuntu7.1), xserver-common (1.7.6-2ubuntu7, 1.7.6-2ubuntu7.1), libgdata-google1.2-1 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), libedata-cal1.2-6 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), evolution-common (2.28.3-0ubuntu9, 2.28.3-0ubuntu10), mysql-server-core-5.1 (5.1.41-3ubuntu12.1, 5.1.41-3ubuntu12.3), libmysqlclient16 (5.1.41-3ubuntu12.1, 5.1.41-3ubuntu12.3), gstreamer0.10-plugins-good (0.10.21-1ubuntu2, 0.10.21-1ubuntu3), linux-firmware (1.34, 1.34.1), telepathy-butterfly (0.5.9-0ubuntu1, 0.5.11-0ubuntu1), libsdl1.2debian (1.2.14-4ubuntu1, 1.2.14-4ubuntu1.1), libedataserverui1.2-8 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), gdm (2.30.2-0ubuntu1, 2.30.2.is.2.30.0-0ubuntu1), libkrb5support0 (1.8.1+dfsg-2, 1.8.1+dfsg-2ubuntu0.1), libedata-book1.2-2 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), mysql-client-core-5.1 (5.1.41-3ubuntu12.1, 5.1.41-3ubuntu12.3), libsdl1.2debian-pulseaudio (1.2.14-4ubuntu1, 1.2.14-4ubuntu1.1), libegroupwise1.2-13 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), compiz-gnome (0.8.4-0ubuntu15, 0.8.4-0ubuntu15.1), libexchange-storage1.2-3 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), libgnomekbd4 (2.30.0-0ubuntu2, 2.30.1-0ubuntu1), gstreamer0.10-pulseaudio (0.10.21-1ubuntu2, 0.10.21-1ubuntu3), compiz-plugins (0.8.4-0ubuntu15, 0.8.4-0ubuntu15.1), libdecoration0 (0.8.4-0ubuntu15, 0.8.4-0ubuntu15.1), libcamel1.2-14 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), evolution-data-server-common (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), evolution-data-server (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), compiz (0.8.4-0ubuntu15, 0.8.4-0ubuntu15.1), libebackend1.2-0 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), libgssapi-krb5-2 (1.8.1+dfsg-2, 1.8.1+dfsg-2ubuntu0.1), compiz-core (0.8.4-0ubuntu15, 0.8.4-0ubuntu15.1), libgdata1.2-1 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), mysql-common (5.1.41-3ubuntu12.1, 5.1.41-3ubuntu12.3), libedataserver1.2-11 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3), libgnomekbd-common (2.30.0-0ubuntu2, 2.30.1-0ubuntu1), libebook1.2-9 (2.28.3.1-0ubuntu2, 2.28.3.1-0ubuntu3)
End-Date: 2010-06-10  00:03:58

```
I tried downgrading linux-firmware, gdm, xserver-xorg-core, and xserver-common
downgrading didn't help

All logs after a failed boot are empty

booting in safe graphics mode worked
and finally uninstalling the fglrx driver allowed me to boot with the radeon driver.
```

# going from memory:
sudo /usr/share/ati/fglrx-uninstall

```

I was using the 10-5 fglrx drivers (more recent than the ones installed by hardware manager)

I will try to see if installing the drivers will fix the issue.
Update:  Reinstalling the driver worked fine.

---

### Post by roffez on 2010-06-14
I can confirm this with nvidia-restricted drivers. Sometime requires 3+ reboots.... looks like a race condition.

---

### Post by madengineer on 2010-06-28
Happening to me too, HP Pavilion dv4t with NVidia graphics, restricted driver. I have what seem like the same messages in syslog from a failed boot:

```
Jun 28 20:55:24 Obsidium init: plymouth-stop pre-start process (1310) terminated with status 1
Jun 28 20:55:38 Obsidium kdm[967]: X server startup timeout, terminating
Jun 28 20:55:38 Obsidium kdm[967]: X server died during startup
Jun 28 20:55:38 Obsidium kdm[967]: Failed to start X server. Starting failsafe X server.
```

This leads to a frozen Kubuntu blue startup screen, which I've been able to escape from by rebooting with the power button or Ctrl+Alt+Del. Has anyone reported this as a bug yet?

---

### Post by codefish on 2010-07-02
Happening to me also. Dell Studio 15 Laptop with ATI graphics card. I installed the suggested drivers. I haven't done any updates. It is a brand new laptop and is 2 days old.

---

### Post by slartybartfeast on 2010-07-05
I have the exact same problem running 10.04 on two machines: one at home and one at work. At home it's an ATI graphics card with the proprietary drivers. At work it's a virtual machine with an ATI card in the host.

Anyone with a fix?

The sporadic nature of it is the frustrating part.

Also, it doesn't seem that rare: much closer to 50% of the time than 5%, for example.

---

### Post by Slug71 on 2010-07-05
Yup, i been getting the same problem on my custom install. Ubuntu with XFCE.
Seems to be after getting the updates in the last few days. My Ubuntu install on another PC lost its wireless too.

Anyone filed a bug?

---

### Post by myrddinemrys on 2010-07-06
Just chiming in with another "me too": nVidia card, restricted drivers (though it's been doing this even before I installed the restricted drivers). about 40-50% of the time, it will freeze on startup, but a re-boot usually will get it to boot up fine.

The weird intermittent nature of the problem makes it hard to troubleshoot.

---

### Post by themalcontent on 2010-07-07
Another me-too confirmation.
Kubuntu boot freezes (during either a cold boot or restart) on the kubuntu logo blue screen with all the dots turned on.  It only happens sporadically (1 start in 10-15 maybe) and, when it does, pressing the power button causes the system to shut down in an orderly fashion (so I think the system is up).

Has anyone filed a bug report?  What other information is required?
I had a quick look on launchpad and this thread sounds similar to [this]("https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/538524") (fixed) plymouth/kdm bug.

---

### Post by RJARRRPCGP on 2010-07-07
> **roffez said:**
> Sometime requires 3+ reboots

Looks like random freezes, because of a faulty motherboard. Or bad HDD. 

Reportedly, bad caps can cause strange stuff like that. 

[http://badcaps.net](http://badcaps.net)

I know, the way I bumped in, sounds like Dr. House. LOL.

---

### Post by RJARRRPCGP on 2010-07-07
> **myrddinemrys said:**
> Just chiming in with another "me too": nVidia card, restricted drivers (though it's been doing this even before I installed the restricted drivers). about 40-50% of the time, it will freeze on startup, but a re-boot usually will get it to boot up fine.

The weird intermittent nature of the problem makes it hard to troubleshoot.

And your PSU may be bad. Sorry. :(

---

### Post by suelynnes on 2010-07-09
There is nothing wrong with our hardware. I am a builder and have checked my system thoroughly. You have a definite problem with the current OS. I am trying to use kubuntu 10.04lts with the same poor result.

---

### Post by alexsb on 2010-07-13
I have the same problem here, and it's definitely not the hardware, since I experience the issue on two different Lenovo ThinkPad Notebooks (T61 and W510). Both worked fine before, and both work fine as soon as I'm finally able to boot.

Is there no bug report for it yet?

---

### Post by Protocol84 on 2010-07-22
Another"me too" to add to the pile, but another symptom too to go along with it, it was happening only every once in a while until the latest kernel update happened. Now I cannot log into the latest kernel from grub, I have to use the second newest one otherwise it hangs on the blue screen with the dots, EVERY time. 

Normally when I boot my monitor doesn't change modes fast enough for me to even see that screen.

No, it is not a hardware issue, I was running 9.10 perfectly fine for a while without so much as a glitch, this definitely has to do with the distro, too many people are having the same problem with this specific distro for it to be slowly failing hardware. And my computer is almost new (6 months).

I hope they can find a fix for this soon, I really want to be ably to use the up to date kernel.

Newest kernel (2.6.32-24) relieved the problems,after I knew the newest kernel was good I did a total re-install and now have Kubuntu 64 bit, Ubuntu 32 bit and Ubuntu studio all installed and running flawlessly.

---

### Post by paran0rmal on 2010-07-22
Me too on Kubuntu 10.04, and everything was fine on 9.10. At work on an ATI / Intel laptop, and now at home on an NVidea / AMD desktop. I don't think this is hardware related. 

I never imagined my Linux distro would have a blue screen of death...

---

### Post by ytzml on 2010-07-25
Well, I haven't found any bug report concerning this issue, so I've just reported one (my first bug report ^_^ ):

[https://bugs.launchpad.net/ubuntu/+bug/609845](https://bugs.launchpad.net/ubuntu/+bug/609845)

We'll see if there will be any response.

---

### Post by linux18 on 2010-07-25
I have had this problem once in 9.04 and several times in 10.04 however, I have found a workaround:
```

-choose recovery mode at grub
-drop to a root prompt
-type " telinit 3" and login
-then type " xinit "
-when xinit starts type: " metacity & " - for ubuntu OR " compiz & " - if you have it OR flux/openbox & - if you have it OR " fvwm & " - for xubuntu
-then type " gnome-panel & " -for ubuntu OR " xfce4-panel & " -for xubuntu
-lastly type " nm-applet & " -for networking

```
once you do this, the next few boots are almost guaranteed to work properly

---

### Post by ytzml on 2010-07-26
Well, at launchpad guy called chilicuil wrote:

> 
 In order to determine if this issue is plymouth related, please boot  your computer with plymouth disabled and then shutdown to see if you  can reproduce the issue. To disable plymouth for a single boot, follow  these steps: 1. Press Esc during Grub boot delay to access the boot menu.
2. Select your actual Ubuntu boot line and press "e" to edit it.
3. Select the "linux" line and at the end of the line, remove "splash" and "quiet".
5. Type "ctrl + x" to boot the custom boot line.
 

Described problem happens to me rather rarely, once every ten boots or so. Maybe if someone experiences this issue more often can easier check if this seems to fix the issue.


Cheers

---

### Post by _sleeper on 2010-07-28
My laptop hangs 1 out of 5 or so. It's interesting that the frequency of freezing differs from 50% to somewhat 5% according to what I've read so far. My wild guess is that we're dealing with a plymouth bug, no one had it before Lucid. The tragedy of this, is that after 3 months a severe bug like this cannot even be identified as to what it's causing it.

---

### Post by Ko$ on 2010-08-13
+1

---

### Post by Ko$ on 2010-08-13
It`s amazing to see a real bug that freezes the system and no one seems to bother.

---

### Post by _sleeper on 2010-08-13
I think it's not that no one seems to bother, rather it's impossible to be reproduced. The guys out there are doing a great job, but this one's tough to deal with, since it's randomness and variety of different platforms it appears, makes it unbelievably hard to trace it's origin. But, if that bug passes onto Meerkat, then that would be a disaster.

And as I said before, I'm guessing it's a plymouth bug, since this is the major change between lucid and karmic.

---

### Post by mgleahy on 2010-08-17
I found the same problem...I think I've run unto this not too long ago.  Sometimes, after updates the fglrx driver and/or its config gets fubar'd.

I uninstalled fglrx from the failsafe boot prompt, then re-installed it, then ran 'aticonfig --initial -f'.  Then I rebooted, and everything was back to normal.

Of course, I tinkered around with other things prior to that, but nothing seemed to help until I re-installed fglrx.  I may have cleared out my xorg.conf as well, before reinstalling fglrx, so that's something else to try.

Good luck.

---

### Post by _sleeper on 2010-08-19
I don't think it's a fglrx problem. I, for example, am running the closed source nvidia drivers.

---

### Post by Ko$ on 2010-08-23
> **_sleeper said:**
> I think it's not that no one seems to bother, rather **it's impossible** to be reproduced.

Don't know how impossible is it but after my post my problem is gone after kernel upgrading.

So thank you guys if you fixed it cause I didn't have any freezes since..

---

### Post by _sleeper on 2010-08-23
Yeah, for the last week or so I haven't had any freezes at all.

---

### Post by tomdavidson on 2010-08-29
same symptoms... freeze at splash, couln't get a different terminal...  but by taking out the quite and splash options from the boot i was able to get in and see that xorg.conf was boogered up. restored a backup and all is well.

br,

---

### Post by jonny.dee on 2010-09-03
I deactivated plymouth by removing 'splash' boot option from within Grub and could boot my machine without problems. So it seems like this problem is indeed plymouth related.

---

### Post by _sleeper on 2010-09-04
> **_sleeper said:**
> Yeah, for the last week or so I haven't had any freezes at all.

Although it seemed like that the bug was fixed, I continue to encounter the same problem.

---

### Post by james_xxx on 2010-09-12
Just chiming in. 

Same problem here on a completely up-to-date K/Ubuntu 10.04.1 system, using the restricted Nvidia driver.

I have a number of PCs and laptops, but only my primary desktop is affected.

None of the other machines are using proprietary graphics drivers.

---

### Post by Kir_B on 2010-09-12
He guys. Interesting thread you all have here!

I'm having interesting boot up difficulties also (I'm running Ubuntu). Unlike some of you, I have yet to get it to boot a single time, but perhaps I haven't been as persistent. I'm running the nVidia drivers, but instead of seeing the plymouth during boot, I've only seen lines along the top of the screen since the upgrade to Lucid. When I get to my grub screen, everything appears normal. Normal kernels, when selected never reach the login screen. When I select a kernel's recovery mode, absolutely nothing happens! I've tried booting with the "quiet" and "splash" removed from the boot command, but get the exact same result, it appears to be booting for about ten minutes, then the light on the front of the computer goes out and never flashes again.

I'm currenly runing off of an old backup USB HDD from months ago, which I've removed from the case and installed into my computer cases HD bay, so I no longer think it's a power supply or mother board issue.

I hope someone finds a fix soon. Until then I'll keep looking for a fix. If I find something, I'll post it here.

Good luck everyone. Kirby :confused:

---

### Post by Jebtrix on 2010-09-17
Another me too. Kubuntu 10.04 gets stuck on plymouth boot screen as soon as I activate nvidia proprietary drivers. Its not random, I can't even get it to log in once. Even tried 10.10 beta but that failed to even configure grub properly. 1 step forward 2 steps back as usual... ](*,)

---

### Post by pclinux on 2010-09-23
Count me in, I am having this problem with Kubuntu 10.04 using the closed Nvidia drivers. It freeze at the blue plymouth screen and the dot stop moving. A force restart will usually fix the problem. This problem has been happening randomly and I have not experienced it for the past few days. Keeping my fingers cross.

---

### Post by magick.crow on 2010-09-26
I hate to post a me too, but this problem has been happening to me since I installed 10.04. I have been waiting because these things are usually fixing in the fist few weeks but this is nuts. It comes and goes. Gets better, gets worse but is back today with something like a 5% success rate at booting!! It has been months and no one has fixed it. Is any one even trying? It can't be that hard.

Nvidia drivers, all up to date, strange USB errors on booting but it gets passed that(Was hopping that would go away to like these problems used to do.)

---

### Post by buntunub on 2010-09-28
+1

Also, after yesturday's kernel update, it will no longer boot Xorg calling out dozens of errors for Nvidia kernel mode settings issues. Tried uninstalling/reinstalling various and sundry Nvidia drivers, mucking about with xorg.conf, the whole 9-yards and nothing.

---

### Post by buntunub on 2010-09-28
I fixed the Nvidia Xorg issue. The latest kernel update had some hosed up packaging going on that somehow borked DKMS. It was a bit of a nasty surprise, but its something I am becoming used to with Ubuntu and the sometimes unprofessional and shoddy work that goes into it at times. You get what you pay for and all that jazz. 

Anyway, the Plymouth freeze still occurs at random. A bug report needs to be filed about this issue.

---

### Post by drbobbeattie on 2010-10-08
+1. My first experience of Kubuntu. Not what you would call exactly impressive. Is Ubuntu any more reliable? I normally use Centos which is pretty solid, but is maybe getting a bit old.

---

### Post by ytzml on 2010-11-03
If anyone is still struggling with this problem : it seems, that disabling plymouth solves it. See [https://bugs.launchpad.net/ubuntu/+bug/609845/comments/3](https://bugs.launchpad.net/ubuntu/+bug/609845/comments/3) for detailed instruction on how to do that.

---

### Post by _sleeper on 2010-11-03
This problem was resolved for me, but after I updated to the meerkat, it came back. The only solution is to remove the "quiet splash" from the /etc/default/grub file.

---

