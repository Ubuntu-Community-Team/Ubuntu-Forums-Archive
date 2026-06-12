---
title: "Libreoffice freezes entire system when using Classic desktop - 11.04"
date: 2011-05-09
forum: General Help
---

### Post by yogiri on 2011-05-09
Hello! This is my first post here, sorry to make it a question, I promise I'll try to contribute too :)

Anyway, the title says it all basically. Can't run Libreoffice when using the Classic desktop (runs fine in Unity desktop). After the splash screen shows up, the loading bar starts loading and then everything freezes (at 1/6 of the loading bar). Can't do anything but turn off and on the computer. I already tried uninstalling/installing again.

By the way, I always mess with the Compiz settings a lot and maybe I did something wrong, but I can't figure out what.

Any help will be appreciated. Thanks!

---

### Post by ajgreeny on 2011-05-09
How about disabling compiz and running metacity with the classic desktop using ```
metacity --replace
```then try running libreoffice again?

That may help discover whether or not compiz is the problem.

---

### Post by yogiri on 2011-05-09
> **ajgreeny said:**
> How about disabling compiz and running metacity with the classic desktop using ```
metacity --replace
```then try running libreoffice again?

That may help discover whether or not compiz is the problem.

Yeah, it works this way. Looks like Compiz is the problem after all. I'll have to keep digging in the config until I find out what is wrong. I'll post the solution if I find it to help someone else with the same issue.

Thanks!

---

### Post by yogiri on 2011-05-09
All right! I solved it. I ran:

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

After that, restarted and everything works fine again!

Thanks for your help!

---

### Post by Spoom on 2011-06-03
I'm going to see if I can figure out which Compiz plugin is causing this.  Running LibreOffice from a default Compiz configuration (as the post above mentioned) works fine, but after enabling a few plugins I'm back to it freezing on the splash screen.  Works fine with Metacity though.

---

### Post by a.vlachos@radiokiss.gr on 2011-06-07
Thank god i found this post. Do u have any further news about the thing that's causing this pain???

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **a.vlachos@radiokiss.gr said:**
> Thank god i found this post. Do u have any further news about the thing that's causing this pain???

No idea. I've switched back to 10.10 for now until they can get this totally worked out.:popcorn:

---

### Post by dugh on 2011-06-15
metacity replace or unsetting compiz didn't work for me, although it did crash the desktop

Now chrome is hanging up all the time, too.  It freezes anytime you do something that pops up or closes a window, like when you want to bookmark something.

I also as in this thread get a hard freeze of about 10-15 seconds if I start up LibreOffice from a shortcut on the top toolbar in classic.  If I start LibreOffice from the command line it doesn't freeze at all.

---

### Post by Gyorgy on 2011-08-04
Hi,

I am joining 'the Klub', using :
- Lenovo t520 ( i7, 4G mem )
a/
- Ubuntu 11.04 ( 64 bit)
- LO 3.3, than swapped to LO 3.4.2
b/ 
 - W7
 - LO 3.4.1

Issue ( within Ubuntu 11.04 ONLY ),
- using Ubuntu Classic ( w or w/o effects )
- using LO, doing movement of cells ( copy, paste, cut, paste )
- causing system freeze = system non responding to any input devices. Only escape is the Power Off ( physical ! ) button.

When restarting, reopening the LO -> restore file, it happened often:
- the restauration did not happened -> it produced a file of 0 B !

Since a while I am browsing the forums, finding no people w/ similar issues...


Started to give up the 'Wonderland@ and turning back to the 'dark side' of Micro.

:-(


BR

Gyorgy

This never happens w/ w7 !

---

### Post by while_true on 2011-08-06
I had the problem that my **Compiz freezed when starting Libreoffice** (sometime it also freezes randomly).

Switching to the console worked though. Killing compiz solved the problem for the most part.

But now I found out that when **disabling then Detection plugin** (for a bit more clever hardware detection) in Compiz**,** libreoffice starts without problem.

I don't know if the random freezes are solved this way too though. Have to check in the future.

Maybe this solves the problem for someone else as well... hopefullly...

---

### Post by geoffreymatthews on 2011-08-08
Turning off Detection in Compiz did not immediately work for me. But I found LibreOffice running again after a couple of restarts. 

So maybe Detection is the culprit.

---

### Post by geoffreymatthews on 2011-08-08
I think it solved the problem for me ...

Turning off Detection in Compiz did not immediately work. But I found LibreOffice running smoothly again after a couple of restarts. 

Detection must be the culprit, because other things I tried failed to have any effect.

---

### Post by arscek on 2011-08-09
I disabled Detection plugin, and it still freezes when I select and copy some cells. Using 11.04 classic desktop

---

### Post by Garonenur on 2011-08-19
Hi,  I have a similar problem. My LO freezes when I try to copy cells.  The thing is: compiz is not running as I am using awesome and not gnome.  running 11.04 on a X220.

---

### Post by doktoreas on 2011-08-29
Same here.
Ubuntu 11.04 and tested with LO 3.3 and 3.4..no effects enabled.

Thx
L.

---

### Post by root101jp on 2011-08-30
I have same issue for LO with Ubuntu 11.04 on SandyBridge.

There are also issues Ubuntu 11.04 on SandyBridge.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065)

I did many workaround which I found in internet how ever I haven't resolved it yet.

I am not sure where cause of problem is.....

---

### Post by AlanDeSmet on 2011-09-14
I am very similar to Gyorgy.

Lenovo ThinkPad T520 (i5, 4 GB RAM)
Ubuntu 10.04 (32 bit)
LibreOffice 3.3.3
"Classic Mode"

Originally ran into this in plain Classic mode. Suspecting the graphics drivers to be a problem, I switched to classic mode no effect (no compiz), and reproduced the problem again.

I don't know exactly what triggered it, but in both cases I had a LibreOffice spreadsheet and document open and I was copying stuff from a table in the document into the spreadsheet, editing it, then copying it into gvim.

---

### Post by AlanDeSmet on 2011-09-14
Poking around the bugs site [this is very interesting.]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bugs?field.searchtext=libreoffice&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")  Three system hangs/crashes, all related to LibreOffice.  Now, LibreOffice shouldn't be able to take X down, but apparently it's tickling the bug.  People seeing this might want to review them and add comments.

In particular, [816075 sounds very familiar]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/816075") to me.  It suggests that disabling anti-aliasing might be a workaround, but I'm not yet desperate enough to try that.

---

### Post by Dan Lucier on 2011-09-21
> **yogiri said:**
> All right! I solved it. I ran:

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```After that, restarted and everything works fine again!


I am also having a problem with LO freezing and need to find a solution ASAP. Can anyone tell me what the code above will actually do, and how I could reverse it if it doesn't help me. I am using Kubuntu 11.04 so I'm not running Unity; is this even relevant for me?

Also, I am wondering if this might be a driver issue. How many of you out there are using an Intel video card? I am using a Thinkpad E520 with an Intel 3000 HD video card. I had trouble finding a distro that would work properly with this card. Kubuntu seemed to work for a couple of weeks but now I am having problems with LO. Interestingly, I do not have any problems with LO using Dream Studio on the same computer.

Here are the biggest difference between these distros:

Kubuntu 11.04 (64-bit), Kernel 2.6.38
Dream Studio (32-bit), Low-Latency Kernel 3.0.0

Note: Dream Studio is based on Ubuntu 11.04. It uses Unity by default. I have switch to classic Gnome and installed Linux Mint icons, themes, and menu.

---

### Post by khurtsiya on 2011-09-29
same here

Lenovo E520

Freeze after trying to copy column in LibreOffice

No Compiz, no effects

Any quick workaround?

---

### Post by SM666AT on 2011-10-04
Hi there same here.

I use Ubuntu 11.04 on four different machines, this one is a
HP Elitebook 8560p

it is the first one causing this problem
On a HP Compaq with ATI graphics -> NO PROBLEM
On a Samsung NC10 with Intel graphics -> NO PROBLEM
On a Dell Vostro 1000 with ATI -> NO PROBLEM.

It seems to be a graphics issue, but I couldn't figure out, what is causing the problem. Using the gconf-tool to unset compiz did NOT WORK. Disabling the "Detection" Plugin DID NOT WORK.

I am now trying with the "antialiasing" turned off in LO.

by the way I tried LO 3.3.3 and LO 3.4.3 and both share the same problem when cuting, pasting and shifting around with cells in a spreadsheet in LO Calc.

Is anybody working on this?

X.Org is using the following driver

```
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge

```

and tells me
```
(II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge

```


lspci tells me:
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

edit: btw this happens in classic mode w / wo effects and Unity

anybody out there that uses the same hardware? is it a driver issue or a LO issue?


SM

---

### Post by DrDee on 2011-10-04
I have not been able to use Libre Offfice on my new HP Pavilion dv7 with i5 for months, since 11.04, because of the freeze up in Kubuntu or Ubuntu classic.  The spread sheet and copy & paste actions also are the triggers.  Each freeze I have to reboot the computer.  My home desktop works without issue.  I am a newbie, but here is my X.Org and lspci info as well:

```
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,Sandybridge, Sandybridge

```
And

```
(II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge
```And

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
```In short, we (SM666AT and me) have identical issues with the same driver and version.  Please let me know how I can further provide info to improve/use my favorite OS experience.  I can duplicate the problem very easily.  Should we - someone file a bug report or issue?

---

### Post by SM666AT on 2011-10-05
hi there,

I've found that the disabling the anti-aliasing and hardware acceleration did the job for my HP. Though, I think that this is still a bug. There is already a bug report, which seems to be our problem: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/816075]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/816075")


Please try to turn anti-aliasing of and tell me about your experiences.

sm

---

### Post by aeronutt on 2011-10-16
I have the same problem, system locks up when trying to copy a cell or multiple cells. In both 11.04 and 11.10.  Dell laptop with Intel i3.

UPDATE: Turning off anti-aliasing fixed it for me, thanks!!

---

### Post by satriani on 2011-10-19
I have the same problem... Turning off anti-aliasing did not solve the problem.
Running 11.04 on a lenovo T420

I tried uninstalling LO, and installing OpenOffice, but this requires some libs of LO as well, and the same problem occurs with OO. (Downloaded latest DEB file of OO.org)

If anyone has the solution that would be really great! I need an office suite for my daily work, and this is almost undoable.

---

### Post by ionospheric on 2011-12-12
I am having the same problem:
- Lenovo G570
- Ubuntu 11.04
- Classic Desktop
- LibreOffice

When using LibreOffice Calc, the system freezes (at this point randomly to me, I don't know yet how to reproduce. But it is always when I use Calc)

The Freeze is so bad, I can't even switch to a console. Have to press power button for 4 seconds to do a hard reset.

Don't have that problem on my Dell Inspiron 15z laptop. (11.04, classic, LO)

---

### Post by aplysia666 on 2012-01-10
Hi there,
I also using a Sandy Bridge platform and Clac always freeze my system after a while.
Is there any solution for that problem, or even a bug report? 

Thanks!

---

### Post by scarleo on 2012-02-06
Same here on a i7 Asus laptop. Bad thing is, LO wont recover it after some crashes, file is completely corrupt. This need to be fixed and please someone take the SOLVED part of topic away.

---

### Post by mkalen on 2012-03-27
> **scarleo said:**
> This need to be fixed and please someone take the SOLVED part of topic away.

The original poster obviously solved his problem, you might consider opening up a new thread or filing a bug report.

I just solved a similar libreoffice 3.4.4 freeze issue on a Lenovo T420s running Kubuntu 11.10.

X.Org driver:
```
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server

(II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2+)
(--) intel(0): Chipset: "Sandybridge Mobile (GT2+)"
```

lcpci:
```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
```

LO freeze solved by turning off anti-aliasing in Tools, Options, LibreOffice, View, Graphics Output (uncheck "Use Anti-Aliasing"). See also [Bug #816075]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/816075") for a similar situation.

---

