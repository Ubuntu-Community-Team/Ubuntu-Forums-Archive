---
title: "Lucid Freezes Randomly"
date: 2010-05-02
forum: General Help
---

### Post by Archimedes0212 on 2010-05-02
Hey all -

So I had a very cooperative installation of 9.10 on my computer.  Today I upgraded to Lucid.  

The first thing that I noticed is that the graphics on the login screen are all screwy.  I have lines that appear through the screen and I can't see the login button, nor the textbox where I type in my password. 
However, I can still login by using only the keyboard.

Once logging in, I get to my desktop and everything seems normal.  However, after some time, Lucid decides to randomly freeze.  First my mouse and keyboard become unresponsive.  Then, my screen turns black and I have to do a hard shutdown.  This happens randomly (twice while I was running update-grub, once when I clicked on the 'ubuntu one' tab on the upper right corner, once when I was clicking to get onto the internet, and once when I clicked the menu to go change my window appearance)

Has anyone been having these problems or know of a way that I can fix this.  For now, I am crippled in linux and am being forced to use only my Windows partition.

Thanks in advance for any suggestions.

-Archimedes

---

### Post by parm289 on 2010-05-02
Yes - I had random freezes with my install as well.  I need a little bit more info to see if your situation is the same as mine: when your computer freezes, does your caps/scroll lock light blink repeatedly?  This is a sign of a kernel panic, which happened to me at seemingly random times.

Regardless, I recommend looking at your system logs via System -> Administration -> View Logs.  Check syslog for any errors or panics at the time of the freeze.

When this happened to me, I got no errors or panic messages.  If this is the case for you, let me know and I can recommend the steps I took to work around the problem.

Also, it's probably best if you post your system specs.

---

### Post by walter_j on 2010-05-02
I have lockups to in both ubuntu and kubuntu 10.04 (64 bit). I'm running a i7 asus p7p55d pro mb with a nvidia video card, 4 gb ram. I've had lots of trouble with 10.04 and won't change over to 10.04 for now (or maybe never - since i hate some changes). Better wait for awhile before making this your main os. seems to have real stability issues for some. my main os 9.10 is still pretty solid - some issues with some apps, but no show stoppers.

---

### Post by Archimedes0212 on 2010-05-03
No, my scroll lock or any other keys don't flash when it crashes.

I checked my syslog file and there are no errors or anything of that sort.  Would you be able to tell me what steps you took to fix your problem?
The latest lockup occurred when I clicked on my name in the upper right corner.  My mouse and keyboard locked up and I am currently staring at a screen of alternating purple and black vertical lines.

Any help would be much appreciated.  Thanks!

---

### Post by qabulin on 2010-05-04
Having the same issue on a Dell Vostro.  I have yet to get the machine in my hands to check the logs.

In the meantime, the user has reluctantly set the special effects to none.  Its frozen three times with different applications loaded at various intervals, so no definite pattern is yet determined.  The only consistent scenario is that the the mouse interface cannot select anything thing, yet the keyboard can be used to move about an open window and the power button can be used to open the shutdown dialog.

We'll see if this will stave off the "gremlins" until i get the system back in about 5 hours.


No other graphics related issue except for some VERY small "sketchy lines" that appear on a regular basis as windows are being drug around and the effects are set to their highest and the compiz settings manager has been managed.

---

### Post by prayersfor.rain on 2010-05-04
> **qabulin said:**
>  
In the meantime, the user has reluctantly set the special effects to none. Its frozen three times with different applications loaded at various intervals, so no definite pattern is yet determined. The only consistent scenario is that the the mouse interface cannot select anything thing, yet the keyboard can be used to move about an open window and the power button can be used to open the shutdown dialog.
 
 
I'm having the exact same problems.  Doesn't matter what program I'm using, my  usb mouse just randomly freezes and never comes back.  I can still control the computer via keyboard, the prgrams still work (movies still run if they were on), but the mouse is just frozen.  Sometimes it takes only a minute, sometimes I can use the computer for an hour.  
 Anyway, I hope this gets figured out soon.  I'm back to using 9.10 because my mouse works on that.

---

### Post by plane phanatic on 2010-05-04
> **prayersfor.rain said:**
> I'm having the exact same problems.  Doesn't matter what program I'm using, my  usb mouse just randomly freezes and never comes back.  I can still control the computer via keyboard, the prgrams still work (movies still run if they were on), but the mouse is just frozen.  Sometimes it takes only a minute, sometimes I can use the computer for an hour.  
 Anyway, I hope this gets figured out soon.  I'm back to using 9.10 because my mouse works on that.

I'm having the same problem in lucid (64 bit) I'm sure it'll be fixed soon....

---

### Post by _0R10N on 2010-05-04
Same problem here. I'm having it since karmic. It happens any time, switching windows, using firefox, on pidgin, any where... and, honestly, I don't think this is a compiz bug, since I cannot even get a tty. The whole system suddenly freezes, leaving hard reboot as the only possible option.

---

### Post by theantidj on 2010-05-06
I'm having a slightly similar issue.  My display freezes, but I can still ssh into the computer.  

I posted about my issue [here]("http://ubuntuforums.org/showthread.php?t=1474730").

Seems like I'm not alone, but haven't found any sort of fix yet.

---

### Post by mitoe on 2010-05-06
I can report similar problems with my Dell Dimension 2400 (with added Geforce 8300 pci and prism54pci wireless). 9.10 worked great for me, but lucid is doing this consistently after 3 fresh installs.

The crashes are completely random, anywhere from 2 minutes to 10 hours.  Mouse and keyboard completely freeze and I am forced to hard-boot. I can't change state of NumLock or CapsLock, and there is no indication of kernel panic (no ScrollLock blinking).  I have not yet tried ssh-ing in, but I have a feeling it won't respond.

These crashes happen with both versions of the nvidia driver as well as the nouveau driver, and turning off compiz has no effect.

Any assistance would be great... Thanks!

EDIT: I forgot to mention that the logs say nothing out of the normal before the crash.

---

### Post by StuartN on 2010-05-06
> **mitoe said:**
> Mouse and keyboard completely freeze and I am forced to hard-boot. I can't change state of NumLock or CapsLock, and there is no indication of kernel panic (no ScrollLock blinking).  I have not yet tried ssh-ing in, but I have a feeling it won't respond.

My Dell Inspiron 1501 with Radeon graphics behaves the same BUT (despite NumLock etc not working) I can use the SysReq keys - Alt-SysReq-REISUB (i.e. holding Alt and SysReq and pressing R, E, I etc) performs a relatively clean shutdown, which is preferable to a hard reboot. Ctrl-Alt-F1 etc is not giving me a console.

This indicates that X is locked, but some lower level processes are still running. I have set up SSH and guess it will be functioning, but have not had a freeze to try it with yet.

---

### Post by teranex on 2010-05-07
I also have this problem on an Acer Travelmate 4001WLMI. At first i thought it was in combination with Firefox usage, but now i also had it while using other applications, while using the Compiz desktop cube etc.
When it crashes i first see my mouse stopping to respond and my music hangs (it starts to sound like Hardcore/Jump/whatever ;)), then my display turns black. Ctrl+alt+F2 doesn't give my a console. I did try to ping my frozen laptop from another pc but that didn't seem to work.

I now disabled Compiz to see if that helps...

Around 6 months ago i had similar problems after upgrading to Karmic, but these problems disappeared, but i know now what made the problems go away. But they are definitely back now.

---

### Post by john newbuntu on 2010-05-07
I do not have this problem.  But I did read a few threads about an Xorg memory leak that lead to an eventual freeze.  Please search the forums or Google for that.  It had something to do with the version of GLX that is being used.  I believe 
```
glxinfo | grep "GLX version"
```should not be 1.4 since that is the buggy version.  It also suggested running this command:
```
grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
```to see if the numbers are increasing as you open and close applications that involve graphics/flash/multimedia etc.  Typically, this number should decrease after you are done with your app.  But if you still find it increasing, you are bitten by this bug. 
Also check your .xsession-errors file in your home directory for errors.  For those of you who have not run updates, please run it and use the latest kernel and see if it resolves it.

---

### Post by madhusker on 2010-05-07
This is sooooo disappointing for ubuntu!!!!  :evil:

I had quite a few lockups starting in 9.10 but was surviving until 10.04 where I was *hoping* it would be fixed with a new kernel, nope...

Hard locked quite often now with no response from numlock or caps lock.

No sure what sysreq key everyone is talking about, my keyboard doesn't have one....

No ssh, it's dead like the rest of the OS.

Logs are as blank as the look on my face every morning when I can't log in remotely because it's dead.

Compiz has never touched this install.

Right at this very moment I am away from home and my once reliable server is dead to the world just spinning it's fans again.....

i7-920
Nvidia 9800GT
x64 10.04 LTS

Anyone?  Looks like it's been a big problem even back in November (check x64 threads) with 9.10 which tells me it isn't going to be fixed any time soon.

---

### Post by StuartN on 2010-05-07
> **madhusker said:**
> No sure what sysreq key everyone is talking about, my keyboard doesn't have one....

SysReq might be on the same key as PrintScreen. Pressing Alt-SysReq and R,E,I,S,U and B should reboot more cleanly than power-cycling.

Here are some Launchpad bugs and forum threads about freezing / locking without memory leakage [http://www.iol.ie/~stuartneilson/Bootup_fsck.html](http://www.iol.ie/~stuartneilson/Bootup_fsck.html). One may match your own symptoms better than others.

---

### Post by teranex on 2010-05-07
> **john newbuntu said:**
> I do not have this problem.  But I did read a few threads about an Xorg memory leak that lead to an eventual freeze.  Please search the forums or Google for that.  It had something to do with the version of GLX that is being used.  I believe 
```
glxinfo | grep "GLX version"
```should not be 1.4 since that is the buggy version.
Ok, so i have this 1.4 version. Any suggestions on how/where to get a newer, none-buggy version?
I have currently disabled compiz (and use metacity instead). My laptop has been running for the alst 12 hours without any problems, so far... (but i'd like to be able to use Compiz again :))

---

### Post by newman on 2010-05-08
> **StuartN said:**
> SysReq might be on the same key as PrintScreen. Pressing Alt-SysReq and R,E,I,S,U and B should reboot more cleanly than power-cycling.

Here are some Launchpad bugs and forum threads about freezing / locking without memory leakage [http://www.iol.ie/~stuartneilson/Bootup_fsck.html](http://www.iol.ie/~stuartneilson/Bootup_fsck.html). One may match your own symptoms better than others.



Pressing Alt-SysReq and R,E,I,S,U and B should reboot more cleanly than power-cycling.

I get a hard lock-up -  no response from keyboard, so I have to hit reset key. :mad:

---

### Post by Zburatorul on 2010-05-08
I'm am experiencing the same problem with lucid as most users above, had to tab 30 times to get to this field to type it up:
The system runs fine for a while, then I leave, come back and the interface is completely unresponsive to the (usb) mouse, while mostly responsive to the keyboard. Alt-Tab doesn't always work (Switching windows).

Running a custom built pc with a Gigabyte mobo, Core2 Duo, nVidia video card. 
I also used to experience this with Karmic.

Just checked my "GLX version", it's 1.4. I monitor X with htop often and the MEM percentage reported for X is always low enough ~3%, so I don't see how memory leaks alone could be causing problems. I have been running a lot of graphics apps though. Compiz disabled.

Anyone have any suggestions on getting a version of X free of this bug? Other things to try?
Thanks.

---

### Post by john newbuntu on 2010-05-08
I use the 2.6.32-21-generic kernel and do not have any problems.  (Check using "uname -r" in a terminal)
Here are the links to what is/was a bug leading to Xserver crash:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981)
[https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)
Please search the forums/google for more information.

---

### Post by israeldl on 2010-05-09
I have the same problem:
[http://ubuntuforums.org/showthread.php?p=9231749#post9231749](http://ubuntuforums.org/showthread.php?p=9231749#post9231749)

---

### Post by israeldl on 2010-05-09
> **john newbuntu said:**
> I use the 2.6.32-21-generic kernel and do not have any problems.  (Check using "uname -r" in a terminal)
Here are the links to what is/was a bug leading to Xserver crash:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981)
[https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)
Please search the forums/google for more information.
 
I think that is not the problem. The system does not freeze, but just keyboard and mouse. (at least does not seem to be the problem of most the people on this thread)

---

### Post by svtdragon on 2010-05-09
I've had this problem since Intrepid.  Disabling legacy USB support didn't fix it.  Disabling Compiz solved it in Jaunty, but it's back in Karmic, even with Compiz disabled.

Running x64, fully-patched, on every kernel version since Intrepid.  nVIDIA graphics (triple-head setup on 2 GPUs, which is why I have to disable Compiz anyway).

I also have a USB KVM switch--this means my mouse and keyboard plug in through the same USB port.  My mouse will occasionally freeze, and when it does, if I switch away from the box and back to it, the light on the optical mouse goes out, but I can still use the keyboard *most* of the time.  Occasionally that will freeze too, but then I can use my PS/2 keyboard just fine.

If I try running "lsusb" when the mouse is frozen, it just hangs the terminal I try to run it in.

Useful information from everyone else in this thread:  Is your keyboard USB as well, or not?

---

### Post by israeldl on 2010-05-09
> **svtdragon said:**
> I've had this problem since Intrepid.  Disabling legacy USB support didn't fix it.  Disabling Compiz solved it in Jaunty, but it's back in Karmic, even with Compiz disabled.

Running x64, fully-patched, on every kernel version since Intrepid.  nVIDIA graphics (triple-head setup on 2 GPUs, which is why I have to disable Compiz anyway).

I also have a USB KVM switch--this means my mouse and keyboard plug in through the same USB port.  My mouse will occasionally freeze, and when it does, if I switch away from the box and back to it, the light on the optical mouse goes out, but I can still use the keyboard *most* of the time.  Occasionally that will freeze too, but then I can use my PS/2 keyboard just fine.

If I try running "lsusb" when the mouse is frozen, it just hangs the terminal I try to run it in.

Useful information from everyone else in this thread:  Is your keyboard USB as well, or not?

My mouse and my keyboard are ps/2.

---

### Post by SpaceBison on 2010-05-11
I'm having the same problem with my keyboard/mouse randomly freezing. Stuff like music, movies, clock still continues to run. If I hit the power button I get the pop up dialog with shutdown, restart, suspend, etc. but can't click or navigate on it or anything. Never had this problem in the previous releases on this machine.

I'm running Ubuntu 10.04 64 bit. ps/2 logitech wireless mouse keyboard. Switched it out for a wired one, wouldn't respond.

```
$ uname -a
Linux spacebison 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```

---

### Post by jafurcha on 2010-05-11
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

[https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

Also having problems with random freezes after having just fixed the problem of having lucid not boot up (I did this: echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u).

It happened when I used either Chrome or Firefox, and at the time I was running [www.newgrounds.com/audio](www.newgrounds.com/audio) which has heavy visualization in the background.

also has problems with ZSNES Emulator when playing Breath of Fire (when I tried to switch back&forth between my strategy guide and the emulator it would freeze up) and I had problems running YouTube videos as it would crash in the middle of them.

I thought it might be a GEM Leak so I went here:
[https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

jacob@jacob-laptop:~$ grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
61542400 object bytes
jacob@jacob-laptop:~$ 

I did this but it didn't update anything:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
  sudo apt-get update
  sudo apt-get dist-upgrade

glxinfo | grep "GLX version"
GLX version: 1.2

---

### Post by MarkieB on 2010-05-21
no longer participating in ubuntuforums.org

---

### Post by Jakiejake on 2010-05-21
Remember Lucid Is still new and they are still ironing out bugs
Good Luck :guitar:

---

### Post by Jakiejake on 2010-05-22
> **prayersfor.rain said:**
> I'm having the exact same problems.  Doesn't matter what program I'm using, my  usb mouse just randomly freezes and never comes back.  I can still control the computer via keyboard, the prgrams still work (movies still run if they were on), but the mouse is just frozen.  Sometimes it takes only a minute, sometimes I can use the computer for an hour.  
 Anyway, I hope this gets figured out soon.  I'm back to using 9.10 because my mouse works on that.
Same Here

---

### Post by Jakiejake on 2010-05-22
I've got an ATI
And I am getting freeze up's too
Supposedly it is the ATI drivers

---

### Post by pirog on 2010-06-03
hi guys,

i had Xubuntu 9.04 installed and working just fine, that was a few months back. Recently I added on Lucy (Lucid). I have a few problems described above, like the black screen, purple vertical lines and a static square. I was tracking my cpu and mem consumption. Once i started things like Firefox, update manager or rhythmbox, then ram mem jumped beyond 70% (of 512Mb - old comp) and off we go.
I reinstalled OS many times, the best I could get out of it was with a ReiserFS partition ~ 15 mins of uptime. so it is either power management or memory allocation problem, in my view. I am not an expert but I noted a few things like that, if it helps. I am re-installing it right now, as soon as I restart it and crash it, then I'll have a look at the logs.

:confused:

---

### Post by pirog on 2010-06-04
right guys, here are my findings...

I installed i386 Lucy onto amd64 chip with /boot on primary reiserfs partition and "/" on reiserfs extended. I tend to log into the user space, but after a few minutes it would turn itself off. I can not update my kernel to a *-22-generic since the OS always fails. as from above post I mounted the partition via Xubuntu 9.04 and had a look at the syslogs. every crash would end with similar line every time:

```
Jun  4 01:44:22 ubi kernel: [   89.940100] wlan0: direct probe to AP 00:18:0b:0f:4a:00 timed out
```
or
```
Jun  4 16:10:00 ubi NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
```
or
```
Jun  4 17:12:17 ubi NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) complete.
```
or
```
Jun  4 16:14:07 ubi NetworkManager: <info>  (wlan1): supplicant connection state:  group handshake -> completed
```
or
```
Jun  4 17:17:19 ubi NetworkManager: <info>  wlan1: link timed out.
```

Now, i am going to have a look at the system performance without plugging my usb network card and report back to you. Any suggestions thus far?

P.

---

### Post by pirog on 2010-06-04
it's me again,

kernel log shows that the system froze at the times shewn above. another issue related to kernlog was that of "clocksource tsc unstable". not sure whether this might play the role.

---

### Post by Spook50 on 2010-06-05
I've been having a very similar random lockup issue as well in Lucid. On a Dell Inspiron 8200 w/ 512 RAM, P4M 2.4GHz with internal Broadcom wireless adapter and NVIDIA GF4 440 Go video chipset. It will randomly freeze, first losing control from my USB wireless mouse while still letting me move the cursor around with the little nub in the keyboard and with the touchpad, but no response from any mouse buttons and it won't do the automated shutdown (I set my power button to initiate the shutdown cycle if pressed once), leaving me having to do a hard shutdown.

I've found no errors that are obvious to me in any logs, and watching the system monitor, I notice no memory leaks, though my memory usage stays at about 250-255 MB and up when nothing is running. I'm still new to Ubuntu (Linux in general, actually) though.

One thing I did try so far is to remove Ubuntu One completely (via Software Center and then the last couple packages via Synaptic), and that greatly reduced how often Ubuntu freezes on me now. It still happens, but nearly as often. I think I'm on the right track.

My GLX version is 1.3 also, so no 1.4 to cause any of its issues here.

---

### Post by abdusamed on 2010-06-05
in my experience, compiz is the culprit for ubuntu freezing.. not the distro itself. Any errors in the login screen or during booting, then it's ubuntu distros bug..not the application which you installed.

Hope it help :D

---

### Post by Spook50 on 2010-06-05
> **abdusamed said:**
> in my experience, compiz is the culprit for ubuntu freezing.. not the distro itself. Any errors in the login screen or during booting, then it's ubuntu distros bug..not the application which you installed.
 
Hope it help :D
 
You referring to compiz being a possible cause to the freeze-ups I've described?

---

### Post by pirog on 2010-06-06
I dealt with the problem... I have gone native - installed Lenny...

soz, i am thinking it is a problem with kernel, since other derivatives like Mint and x86_64 (other derivatives will have to be checked ) crashed on my amd64. Lenny i686 works flawlessly!

:guitar:

P.

P.S. not the first time Ubuntu rushed into this mess.

---

### Post by DarkRage4 on 2010-06-06
Try installing a fresh Ubuntu 10.04. Upgrading can cause a lot of extra bugs and errors.

---

### Post by Spook50 on 2010-06-07
I'm running off a fresh install of Lucid myself, and still having occasional lockups (though considerably less since disabling Compiz and removing Ubuntu One.
 
It's always been a personal policy to do fresh installs whenever I redo an OS (starting clear back when I used to use Win 95), slipstreaming any not-already-integrated updates onto the install CD (worked great with XP, which I'm still dual booting), though I haven't done that with anything on Lucid yet. Are the install images themselves updated as updates are issued, or are updates at least able to be slipstreamed to the install disc?

---

### Post by paulxiii on 2010-06-07
> **Archimedes0212 said:**
> Hey all -

So I had a very cooperative installation of 9.10 on my computer.  Today I upgraded to Lucid.  

The first thing that I noticed is that the graphics on the login screen are all screwy.  I have lines that appear through the screen and I can't see the login button, nor the textbox where I type in my password. 
However, I can still login by using only the keyboard.

Once logging in, I get to my desktop and everything seems normal.  However, after some time, Lucid decides to randomly freeze.  First my mouse and keyboard become unresponsive.  Then, my screen turns black and I have to do a hard shutdown.  This happens randomly (twice while I was running update-grub, once when I clicked on the 'ubuntu one' tab on the upper right corner, once when I was clicking to get onto the internet, and once when I clicked the menu to go change my window appearance)

Has anyone been having these problems or know of a way that I can fix this.  For now, I am crippled in linux and am being forced to use only my Windows partition.

Thanks in advance for any suggestions.

-Archimedes
I had/have the identical problem, except no black screen.

I disabled compiz and it made no difference to the garbled screen at startup. I uninstalled the nvidia drivers and it sorted out the garbled screen, but the computer still freezes.

I've now installed an older kernel 2.6.31-10-rt, which I don't recommend as I don't think people normally need the rt kernels. This resulted in my screen going onto the wrong resolution so I reinstalled the nvidia drivers with none of the garbling problems.

Now I'm waiting for the next freeze up. 2 hours and counting. That's a lot better than between 1 and 10 minutes.

The only thing I conclude from my exercise is that the nvidia drivers don't run well with the latest two kernels on my computer.

If it means anything, I'm running the 64-bit version with 64 bit win 7 as a dual boot.

---

### Post by Spook50 on 2010-06-08
> **paulxiii said:**
> I had/have the identical problem, except no black screen.

I disabled compiz and it made no difference to the garbled screen at startup. I uninstalled the nvidia drivers and it sorted out the garbled screen, but the computer still freezes.

I've now installed an older kernel 2.6.31-10-rt, which I don't recommend as I don't think people normally need the rt kernels. This resulted in my screen going onto the wrong resolution so I reinstalled the nvidia drivers with none of the garbling problems.

Now I'm waiting for the next freeze up. 2 hours and counting. That's a lot better than between 1 and 10 minutes.

The only thing I conclude from my exercise is that the nvidia drivers don't run well with the latest two kernels on my computer.

If it means anything, I'm running the 64-bit version with 64 bit win 7 as a dual boot.

How would one go about installing an old kernel? My lockups are all of a sudden (just today) rediculously close together. I can barely go 10 minutes before having to do a hard boot. VERY maddening. I completely removed Firefox, thinking (hoping) that might be a contributing factor, but that made absolutely no difference. Running Chromium now and no change in frequency or symptoms when a lockup occurs.

---

### Post by walter_j on 2010-06-10
I've got a bug open in launchpad for this, but no progress whatsoever. A number of us have posted syslogs, but they aren't useful for nailing down the cause for the lockups. Maybe others can add their syslogs.

[https://bugs.launchpad.net/ubuntu/+bug/581947](https://bugs.launchpad.net/ubuntu/+bug/581947)

I like ubuntu one - best use for ubuntu yet. I have all my contacts there, so I can access the contacts from anywhere. Main reason i haven't abandoned ubuntu. I do hate the loss of tooltips in 10.04 though.

---

### Post by walter_j on 2010-06-26
segfault in npviewer this morning

 [ 1931.327478] __ratelimit: 278 callbacks suppressed
Jun 26 08:06:30 walter-lucid kernel: [ 1931.327485] npviewer.bin[2163]: segfault at 0 ip 00000000f6211041 sp 00000000ffe73d30 error 4 in libflashplayer.so[f5e72000+b04000]

anybody know what this means?

---

### Post by walter_j on 2010-06-29
another segfault and kaboom

[   43.273268] __ratelimit: 278 callbacks suppressed
Jun 28 21:16:57 walter-lucid kernel: [   43.273275] npviewer.bin[1708]: segfault at 418 ip 00000000f6089a56 sp 00000000ffa83d58 error 6 in libflashplayer.so[f5e3b000+b04000]
Jun 28 21:18:41 walter-lucid kernel: imklog 4.2.0, log source = /proc/kmsg started.

---

### Post by Tatarasokak on 2010-06-29
Perhaps i've got a clue.

Im on ubuntu Lucid 10.04 64 bit, kernel 2.6.32-22 generic.

I usually leave my pc on overnight to perform dv tapes encoding to dvd, and just for lazyness, i leave my firefox open on facebook, to read the notifications the next morning before going to work.

I am using the libflashplayer-latest_closed_beta.linux-x86_64.so, and what i noticed is that when i just close firefox before going to bed, the whole system just doesnt hang at all :3

But if i leave firefox open, looks like it will crash without any exception.

Shall this hang (frozen screen, mouse stuck, keyboard dead, but machine still alive in the guts) be related to flashplayer?

Can someone of you tell me if when they hanged firefox was open on webpages with flash content and they were using adobe's flash?

I am a total newbie somehow, now im documentating on how to post a syslog on that bug opened before, and also experimenting in keeping my machine running with/without firefox opened, to see what will happen.

What i can do further to investigate on my clue?

EDIT

I forgot to mention my video driver, its a closed source Nvidia 256.35 got from this repository [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)

Im running on a quad Q8200, 3 gig of ram, Asrock mobo (looking further for the exact model, this box was 2nd hand) and my card is an nVidia Corporation G98 [GeForce 8400 GS] (rev a1) (grepped from lspci)

---

### Post by walter_j on 2010-07-25
I updated to the latest kernal - 2.6.32.24 and immediately had a freeze. I also installed Opensuse 11.3 and it froze too. I'm staying away from the 2.6.32 and newer kernal til the freeze issue has been resolved. Maybe there's a bumch of issues here.

---

