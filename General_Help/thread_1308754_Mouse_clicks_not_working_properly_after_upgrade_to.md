---
title: "Mouse clicks not working properly after upgrade to 9.10 / Karmic"
date: 2009-10-31
forum: General Help
---

### Post by Esahp on 2009-10-31
It only started happening right after I upgraded to 9.10 (I upgraded from the previous release to the latest using Update Manager.)

Basically, whenever I click something, say, a link on a web page, a program running in the gnome-panel, the "Applications", etc menus.. doesn't matter where or what I click.. it seems the mouse click usually doesn't register. Sometimes it works the first click, sometimes it takes 3 clicks. This problem only started after I upgraded, and the mouse works fine with other operating systems, and other computers completely.

Any help would be great

---

### Post by jerkywez on 2009-11-03
Im getting the exact same problem!

---

### Post by staci on 2009-11-03
My mouse does not even work at all. It stays frozen in one place on my screen. Any help on that?

---

### Post by greenkiwi on 2009-11-04
I'm seeing the exact same thing.  It seems to register the "down" part of the click, but then the button doesn't get clicked.

Sometimes hitting enter or Alt+<letter> works, but sometimes that doesn't work either.

---

### Post by Yahoé on 2009-11-04
Since upgrading to 9.10 Karmic final release I lost the side button providing the "back page" in Firefox and Nautilus. Problem had not been noticed on 9.10 alpha and RC.

---

### Post by linuxinmt on 2009-11-04
I'm also seeing failed mouse clicks.  This seems to occur on many aspects of the system.  Eclipse, firefox, flash, thunderbird, titlebars, system menus, etc.  Also, I'm occasionally gettign a drag event for a single click for which I haven't moved the mouse.  I've read lots of stuff about gtk and flash / eclipse.  But I'm seeing this behavior all over the place.  Any help?

---

### Post by MelIrizarry on 2009-11-04
The same for me.  I was thinking my batteries were dying.  Everything works fine if I use the spacebar to "click", but the mouse button not working is getting annoying.

---

### Post by wroscoe on 2009-11-05
I have the same problem. Mouse clicks on buttons in certain applications ( I believe only those using qt) do not work. For me Eclipse and Spyder.  Any ideas how to find the cause of this problem.

---

### Post by karlofski on 2009-11-05
I was having the same problems, at first I tried playing with acpi settings msi and all those other menu.lst options with no luck. I could move the mouse cursor and click but the clicks would randomly stop working and sometimes I could click on one window but not another, etc. My machine would also freeze up after too much time with many windows open. Finally I looked up my mouse (Logitech MX1000) and Ubuntu. I found the xorg.conf settings that work for my type of mouse and my problems seem to be gone! I thought my whole USB controller was the problem or perhaps my IRQ settings, but it was actually quite simple. 

Here is what I added to the bottom of my xorg.conf file (in /etc/X11/xorg.conf):

Section "InputDevice"

Identifier "Logitech MX1000"

Driver  "evdev"

Option  "Name"  "Logitech USB Receiver"

Option  "HWHEELRelativeAxisButtons" "7 6"

EndSection

Note that this only seemed to work with MY mouse. You must find a solution for your OWN type of mouse. Just goes to show that even just having the wrong mouse settings can crash your whole machine in really funky ways.

---

### Post by karlofski on 2009-11-05
One extra note for the solution listed above is that you need to have evdev on your machine. To install enter the following in your console:

sudo apt-get install xserver-xorg-input-evdev

---

### Post by karlofski on 2009-11-05
And again one extra note ;)

If you have trouble finding the xorg options for your mouse you may be able to discover them if you check for your mouse device's name on the output listed when you type this in the console:

cat /proc/bus/input/devices

You should get some output like this:

I: Bus=0003 Vendor=046d Product=c50e Version=2500

N: Name="Logitech USB Receiver"

P: Phys=usb-0000:00:1d.3-2/input0

S: Sysfs=/devices/virtual/input/input5

U: Uniq=

H: Handlers=kbd mouse1 event5

B: EV=7

B: KEY=1f0000 0 100 38 c0000000 c0000 0 0 0

B: REL=103

Notice the "Name" parameter. the name listed there must be the name that you enter on the xorg.conf "Name" option line. It is upper/lower case sensitive. I don't fully understand how the xorg lines work and I haven't experimented much, but if your adventurous you can start there. (Just don't hold me responsible if your machine explodes). :-\"

---

### Post by linuxinmt on 2009-11-05
> **linuxinmt said:**
> I'm also seeing failed mouse clicks.  This seems to occur on many aspects of the system.  Eclipse, firefox, flash, thunderbird, titlebars, system menus, etc.  Also, I'm occasionally gettign a drag event for a single click for which I haven't moved the mouse.  I've read lots of stuff about gtk and flash / eclipse.  But I'm seeing this behavior all over the place.  Any help?

My issues were resolved by using a different mouse.  Didn't really like that old mouse anyway

---

### Post by bedge on 2009-11-05
> **karlofski said:**
> One extra note for the solution listed above is that you need to have evdev on your machine. To install enter the following in your console:

sudo apt-get install xserver-xorg-input-evdev

I have evdev installed, and I have never had to add mouse config data to my xorg.conf.

This is seriously broken. The friggin mouse doesn't work? It's not even wireless. 
I've seen this on all for of my machines, so it's not any specific hardware of brand. It's Karmic. Jeez, what a mess. I wish I had not upgraded now.

---

### Post by karlofski on 2009-11-05
> **bedge said:**
> I have evdev installed, and I have never had to add mouse config data to my xorg.conf.

This is seriously broken. The friggin mouse doesn't work? It's not even wireless. 
I've seen this on all for of my machines, so it's not any specific hardware of brand. It's Karmic. Jeez, what a mess. I wish I had not upgraded now.

Well just to make you feel better, I had this problem in 8.04 AND 8.10! I gave up using Ubuntu completely for a year just because of it. It is funny though because all the suggestions I could find on the forums never even mentioned a solution like this. I never suspected it was simply the mouse, as the symptoms seemed to span the whole system in general. It completely defies logic...

---

### Post by FogAudio on 2009-11-06
I'm seeing this behavior as well in Kubuntu. Karmic Koala has been a relative disaster for me and I have advised our IT department and our engineering staff to avoid Karmic for the time being (until most of these issues are resolved). About a 1/3 of our company uses Ubuntu/Kubuntu.

My specific issues with Karmic:

#1 kwin closes unexpectedly on startup
#2 Copy and Paste is broken (especially difficult to use in Java based apps Eclipse and Open Office), not sure if it is a Klipper problem or what
#3 Some AJAX and Javascript pages are completely hosed in Firefox (Flash apps, etc)
#4 Random poofing a couple of times that didn't crash machine but closed all my apps and logged me out
#5 The dreaded no sound coming out of the speakers (but does come out of the headphone jack)
#6 Still no sound coming out of YouTube apps in Firefox (works fine in Konqueror)
#7 Kontact still crashes on startup if left running in a prior session (this has been around in Jaunty for quite a while)
#8 And most annoyingly of all, mouse button down clicks working but no mouse up events so many things aren't actually clicked. This is broken on my MS Wireless 4000 and built-in trackpad so I don't think it is a mouse driver issue as some have suggested. 

Numbers #2 and #8 are especially annoying because they are affecting my productivity. All in all I've probably lost a whole day of productivity this week at work trying to solve some of these.

For the record I am on a Dell Precision M6300 with NVidia graphics.

The upgrade to Jaunty was so smooth which is why for me this is all especially disappointing.

Ryan

---

### Post by Niniel on 2009-11-06
Thanks, I was convinced my mouse (Logitech trackball, actually) had bitten the dust.

---

### Post by karyook on 2009-11-06
Hello,

I have the same problem over here. I am using an HP DV 6000t which has an internal mouse. 
Find below content of /proc/bus/input/devices, please advise on required changes to resolve problem.

/proc/bus/input/devices:



I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
U: Uniq=
H: Handlers=event3 
B: EV=21
B: SW=1

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=20000 20 0 0 500f02100003 3803078f900d401 feffffdfffefffff ffffffffffffffff
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=b
B: KEY=6420 70000 0 0 0 0
B: ABS=11000003

Gangareen

---

### Post by P4man on 2009-11-06
If you open 

```
xev
```

from a terminal, and click the mouse repeatedly does that reliably register your clicks?

If it doesnt, I suspect an irq polling issue. Try upgrading your bios or boot with 
```

irqpoll

```
or 

```
irqfixup
```

As kernel parameter. See if that helps. You can add those parameters to the grub menu (press escape to enter grub menu, E to edit the line, pick the kernel line, press E again and add one of them after the  *quiet splash* options. That will enable the option for that boot only, so just to test.

---

### Post by karyook on 2009-11-06
I tried xev, mouse working... issue arose after upgrade, only for a specific types of clicks..

---

### Post by P4man on 2009-11-06
> **karyook said:**
> I tried xev, mouse working... issue arose after upgrade, only for a specific types of clicks..

can you elaborate on the "specific types" ? Is it interpreting it as dragging perhaps? You could try changing the drag and drop treshold in mouse preferences

---

### Post by mxt on 2009-11-06
The bug is well known. Look for example here:
[https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

A common workaround is exporting GDK_NATIVE_WINDOWS=1 before running the application with click problems.

---

### Post by P4man on 2009-11-06
> **mxt said:**
> The bug is well known. Look for example here:
[https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

A common workaround is exporting GDK_NATIVE_WINDOWS=1 before running the application with click problems.

Thats for flash and flash only. While its interesting (I do have that on some flash sites) I doubt its what the posters here are experiencing.

---

### Post by karyook on 2009-11-06
P4Man, this "click" malfunction is a byproduct of upgrading to Karmic 9.10.

PS: I can't quote you now due to this malfunction

Gangareen

---

### Post by P4man on 2009-11-06
> **karyook said:**
> P4Man, this "click" malfunction is a byproduct of upgrading to Karmic 9.10.


That doesnt really help me understand the cause. You say specific clicks, which clicks? You say you cant quote because of that, does that mean clicking the quote button on this forum never works and other buttons always work? Is this a browser problem only? Firefox only? I got no clue where to start looking or thinking...

---

### Post by debayanm on 2009-11-06
hi all,

I have a dell inspiron 1525, quite new, 2 GB ram 160 GB HDD, core 2 due T 5750 processor, 2 MB Cache, etc etc

I downloaded ubuntu 9.10 desktop version and ubuntu 9.10 netbook version..They are in ISO version..but when i am running them using DAEMON tools lite, and restarting system, they UBUNTU is just showing a small logo and after that , system is going black..

Plz help..

---

### Post by P4man on 2009-11-06
debayanm, please start your own thread or find one about the same topic. This one is about mouse click problems (and is already confusing me enough as it is without another parallel and unrelated subthread).Thanks.

---

### Post by mxt on 2009-11-06
> **P4man said:**
> Thats for flash and flash only. While its interesting (I do have that on some flash sites) I doubt its what the posters here are experiencing.

Maybe it's not what the poster is experiencing but the workaround works for several applications. I use it for eclipse, azureus and chromium. I think the poster should give it a try.

---

### Post by karyook on 2009-11-06
I was experiencing this problem with eclipse and flash among other things...
problem solved!!!
work around:
export GDK_NATIVE_WINDOWS=1
$APP

Gangareen

---

### Post by _ppr on 2009-11-07
I also have this issue with mouse clicks after update from 9.04 to 9.10
It works randomly(Some times clicks just does not work) in the following applications: Eclipse, firefox, AWN

---

### Post by infallible on 2009-11-07
I'm having this problem as well. The behavior suggests that the click isn't 'focused' within the window. I can drag windows by title bar, or use the bar on the bottom to switch windows. I can use compiz hotkeys, as far as I know, but keyboard input into text fields is unpredictable, missing 3/5 presses.

Has anyone solved this one?

---

### Post by hebetude on 2009-11-08
[http://www.webupd8.org/2009/11/fix-mouse-clicks-not-working-in-flash.html](http://www.webupd8.org/2009/11/fix-mouse-clicks-not-working-in-flash.html)

Here's a bunch of different things to try.  Completely disabling compiz fixed the flash issues, but not the issues with eclipse.

---

### Post by infallible on 2009-11-08
Thanks for responding. My issue seems to be system-wide, not limited to Flash. In fact, I have had Flash disabled since well before the upgrade, because of a bug that caused npviewer.bin to hog system resources.

I'll try fooling around with compiz and report back, readers. As a window manager related utility, it could very well be the cause.

---

### Post by alstein on 2009-11-09
I'm running karmic [gnome version] (even not a update but a fresh install) with the most recent updates.
Confirm that the problem is a «system-wide» one and even disabling compiz doesn't change anything. Still with Ctrl+Alt+D combination keystroke you can minimize all windows and get to the gnome-panel, where with right click on application name in window list (gnome-panel applet) you can switch mouse control to this application but that is very
inconvenient way to work. ;-)
I couldn't find any fast way to reproduce the problem but noticed that 5-10 min work with NetBeans 6.7 in most cases is enough.
Small test made with xev showed that «uncontrolled» application gets no events. :-(

---

### Post by misja on 2009-11-10
I'm having a similar problem since I upgraded to Karmic: Mouse clicks occasionally hit the wrong window.
This only seems to happen when I want to click into a new window; sometimes this works, but sometimes some random other window is selected instead.
I don't have Compiz enabled and it happens system wide.

---

### Post by infallible on 2009-11-12
After tooling around with compiz with no success, I rebooted and logged into a failsafe GNOME session, which worked initially. When I came back to the system later, it had resumed poor pointer behavior.

 I have a wireless keyboard with joystick mouse, and a logitech mx. Unplugging the mouse allows the keyboard's joystick to function. I suspect it has something to do with xorg.conf and its core pointer setting. maybe.  I look at the file. One of these devices is 'mouse 0' and has been set as the core pointer. I don't know how to identify the device for xorg.conf, so I move on.

My dual monitor setup had been set for separate X screens; I had previously attempted to assign a separate keyboard and mouse for each screen. The update changed the layout to a single X screen displayed in TwinView. It seems that returning to the dual X screen format allowed me to use both input devices.

So, it could be that I fixed it, or it could be that I have a short window of full functionality after logging in.

---

### Post by chimiasanchi on 2009-11-12
the only symptom i'm having is with the gnome panel window list. Often, but not always, there is no response to a click on a window's button in the panel. So the result is that windows do not minimize or get focused as I expect. When this happens, the button doesn't change shaped to indicate that it's being "depressed". If I left click and hold (no release) on a window button, It eventually responds after either a few seconds, or when I drag the mouse around a little on the button. So i can always drag a window button to a different position.

I monitored my clicking with xev and didn't see anything unexpected, as far as I know.

Also, I'm not experiencing any unexpected behavior from clicking around in Firefox. I don't use Eclipse, so I haven't confirmed the mouse clicking problems other users are experiencing.

I haven't found any similar bugs to my issue in either bugs.launchpad.net/ubuntu/ or bugzilla.gnome.org

I upgraded to Karmic using the Update Manager.

---

### Post by chimiasanchi on 2009-11-12
in reply to my post #36, I rebooted my machine, and the problem disappeared.

---

### Post by jk-menifee on 2009-11-12
Could I please direct readers to:

[https://bugs.launchpad.net/ubuntu/+bug/468223](https://bugs.launchpad.net/ubuntu/+bug/468223)

and the bug referenced therein:

[http://bugs.freedesktop.org/show_bug.cgi?id=25020](http://bugs.freedesktop.org/show_bug.cgi?id=25020)

It certainly looks like upgrading to evdev 2.3.0 will address this issue for those that still have it (me being one of them). The only thing is, I don't feel confident enough to do it myself. Is there an easy way to do it? Is there any way for the Ubuntu team to push out evdev 2.3.0? I sure could use this fix...

JK

---

### Post by h4ppycl0wn on 2009-11-13
Hey. I'm having this problem too. I upgraded from 9.04 to 9.10, was working fine for some time. Then after an install of updates, mouse stops working. Here's the symptoms:
1) I can open an application and use menus on the gnome menu-bar with no problem.
2) Once an application is opened I cannot "click" any buttons in that application or manipulate the application window in any way (move, minimize, resize)
3) It does not seem to be related to window manager e.g. opening a terminal and using "metacity --replace&" did not fix the issue. 
4) It does not seem to be related to wireless as neither wireless nor USB mice are working.
5) A hard or soft reboot does not fix the issue.
6) It does not seem to be a delay but a non-function as if I hover over a button, or hold a click for 30 seconds plus it still doesn't work.
7) The problem is intermittent, minutes will go by with non-function, then 10 seconds of functionality followed by minutes of non-function.
8 ) The problem is not user-related. All users are effected.
9) Problem is not related to gnome, it also affects KDE (I installed kubuntu-desktop to check this out)... so suspecting it is X related as previously mentioned.

In short, I cannot use my Desktop PC.

I'm awfully tempted to try other Distro's Live CD's today and if one works, try a new install and kiss goodbye to Ubuntu. The 9.10 upgrade also broke the sound on my Dell laptop so I'm really cheesed off at the lack of quality control on this release. 

(Written from my happily stable FreeBSD machine that has functioned flawlessly after upgrades for 10 years... if only the desktop & HW support in FreeBSD matched Linux.. hey ho... makes a for frickin good server though :-)

Phil.... Another dissatisfied 9.10 user.

---

### Post by h4ppycl0wn on 2009-11-13
Ok... weird... Now everything works fine.

Only change made is that the /etc/X11/xorg.conf will have a new date-stamp on it as I thought I'd try things without an xorg.conf file. So....

moved /etx/X11/xorg.conf to /etc/X11/xorg.bak and rebooted... problem still there. Mouse clicks not functioning in apps. Crumby 800x600 resolution so I...

Moved /etx/X11/xorg.bak to /etx/X11/xorg.conf and rebooted... mouse problem not there anymore. Perhaps it will recur later. If so, I'll try and keep an eye on what I was doing at the time.

---

### Post by Niniel on 2009-11-14
Mouse is working fine again for me too. And I didn't try anything to fix it. Must have been one recent update or another.

---

### Post by h4ppycl0wn on 2009-11-16
..and everything is broken again. No idea what caused the problem. Just came back to my machine and it had stopped responding to mouse clicks. Hard reboot does not solve the problem. This is infuriating. :-(

---

### Post by h4ppycl0wn on 2009-11-16
After an hour of leaving my PC doing nothing in particular, the mouse has started working again when I switched back to X.

This is odd as I'd hard rebooted more than once during that hour trying to solve the problem. Went looking for files, deleted temporary files under /tmp & /var/tmp and couldn't fix it. 

It just fixed itself. I'll stop posting about this now suffice it to say, the problem exists and seems to be out of my control.

---

### Post by P4man on 2009-11-16
> **h4ppycl0wn said:**
> After an hour of leaving my PC doing nothing in particular, the mouse has started working again when I switched back to X.

This is odd as I'd hard rebooted more than once during that hour trying to solve the problem. Went looking for files, deleted temporary files under /tmp & /var/tmp and couldn't fix it. 

It just fixed itself. I'll stop posting about this now suffice it to say, the problem exists and seems to be out of my control.

Do you see anything in the log files that throw any light on the issue?

---

### Post by jeffrey.knight on 2009-11-16
I upgraded to 9.10 (Dell XPS) yesterday. My laptop's touchpad mouse did not work following the upgrade.

To upgrade, I clicked through all the default questions, and said 'yes' to all the menu.lst questions. I probably clicked "yes" to some question like "keep the local boot loader version currently installed?" -- I honestly didn't pay close attention to the popup questions during the upgrade.

Following reboot after the upgrade, I checked my /boot/grub/menu.lst and did not see any entries for the new kernel. From this, I realized that grub did not upgrade. 

So I did a 'sudo aptitude install grub2', rebooted, and everything looks good now.

So if this happens to you, open a shell (either ctrl+alt+f1, or in gnome alt+f2, then type 'gnome-terminal') and check/upgrade your grub.

---

### Post by mozillalives on 2009-11-16
> **P4man said:**
> Thats for flash and flash only. While its interesting (I do have that on some flash sites) I doubt its what the posters here are experiencing.

This is not for flash only as it finally let me get Eclipse working again.

---

### Post by h4ppycl0wn on 2009-11-18
Here's my dmesg output & xorg.log from the latest boot when the error occured again (today). No errors as far as I can see apart from in Xorg.log where "no core pointer device can be found" but later in the log the logitech mouse is found and recognised. Any other logs I should check?

---

### Post by h4ppycl0wn on 2009-11-18
My machine isn't a dual-boot system and grub was configured to boot the latest kernel... however, I tried installing grub2 anyway.

No joy. After installing & rebooting the problem is still in evidence. Mouse clicks not registering.

Its so confusing that its an intermittent problem that is not solved by a hard-reboot. Bizarre.

---

### Post by h4ppycl0wn on 2009-11-18
Ok. So, got my machine working.

First, I killed hald ("sudo kill <hald pid>"). This alone did not fix the problem so then I also killed gdm-binary ("sudo kill <gdm-binary pid>"). Which caused gnome to restart. Upon logging back in, mouse is working again.

If the problem recurs I'll try a kill on the gdm-binary without restarting hald, etc. and see if this is a workaround for getting the mouse up and running.

---

### Post by h4ppycl0wn on 2009-11-19
Hi,

After a bit more playing I can say:

- That the problem occurs at boot. If I reboot my machine, it occurs. I rarely rebooted my machine so I didn't notice this immediately. Reminder; the problem is the mouse can move but clicks are not registered. You get enough responsiveness to login, open an application from the menu-bar but the application does not respond (cannot move window, cannot click buttons), ultimately the gnome menu-bar also stops responding.

- That killing gdm-binary seems to fix the issue.

So, for basic users reading this wondering what to do:

[LIST=1]
[*]Open a terminal. If you cannot open a terminal because the menu has stopped responding press CTRL+ALT+F1 to get to a tty screen and login.
[*]Type:
```
 sudo kill `cat /var/run/gdm.pid`
```
[*]Gnome will restart. Login and everything should be working.
[/LIST]

If the command didn't work for you, perhaps you used the wrong syntax. You can also do this:
```
$ cat /var/run/gdm.pid 
2332
$ sudo kill 2332
```
... though obviously you will get a different process ID to 2332

OR this:
```
$ ps ax | grep gdm-binary
 2332 ?        Ss     0:00 gdm-binary
 2774 pts/0    S+     0:00 grep gdm-binary
$ sudo kill 2332
```

All have the same result of restarting the gdm-binary process.

---

### Post by P4man on 2009-11-19
the proper way to restart X (which is what you are doing) is

```
sudo service gdm restart
```

But that is hardly a real solution. Your boot log doesnt give me a clue, but after this happened, do you not see something in /var/log/messages around the time the problem occured?

---

### Post by dynam on 2009-11-20
I am having the same problem - after booting up the machine (9.04), I can start an application, do something for about 2 minutes but then all mouse clicks will become inactive even when I can move the mouse.

I tried to restart the gdm-binary process but the trick doesn't work for me. The only update I did recently was to install Firefox 3.5 - not sure if this is the source of the problem because after installing Firefox 3.5 the machine worked fine for a week. Please help.

---

### Post by h4ppycl0wn on 2009-11-23
Hi P4man,

Sorry for delay. Seeing as I can reliably recreate the problem (by rebooting ;-) ) I have taken a look in /var/log/messages (attached).

You can see all the messages from the reboot & my login up to 19:51:51. The error occurred once I'd started a terminal. At 19:53:34 I restarted GDM, logged back in and problem solved.

I don't see any obvious error messages but I'm no expert.

Thanks,
Phil.

---

### Post by jsvendsen on 2009-11-24
Hi all,

After having random mouse malfunctions ever since installing karmic, things finally seems to have stabilized after I went to "Mouse Preferences" and, in the "Touchpad" tab, disabled the option "Disable touchpad while typing".

Could anyone (try to) confirm?

---

### Post by jorisjoris on 2009-11-24
Hello,

An easier way of fixing it than restarting X is unplugging your mouse and then plugging it back in.  Haven't noticed anything strange in /var/log/messages when this stuff happens.

Best,

J.

---

### Post by misja on 2009-11-26
I did a fresh install of 9.10 on a new machine but got the same problem there: Mouse clicks sometimes selected the wrong window.
I don't know if it matters but on both machines I have a dual monitor setup.

I talked to a colleague who upgraded to 9.10 and had mouse problems too, although different than mine, and he advised me to put Visual Effects to 'medium'. So far I had them switched off.

So I've been working with the effects on medium for 2 days now and finally my mouse does what I want! I find the visual effects annoying though ..

---

### Post by FOBS1 on 2009-11-27
Same problem here. Here's what I did:
Delete all partitions with all versions -
Reinstall from 9.10 CD -
    Mouse did NOT work during Install
    Lots of internet activity - came up with ***.15 kernel (updated during install). Could update be the problem?
So-
delete partition
Reinstall from 9.10 CD  while disconnected from Internet
    Mouse worked on Most elements of Install, not all.
So-
delete partition
Reinstall 8.04 from CD (to see if my system was flaky)
Success - mouse works fine.

Therefore - the problem seems to be introduced almost immediately upon the start of the install.

Could it be in something in the installer?

---

### Post by nickleus on 2009-11-30
i have been experiencing problems mostly in eclipse, where dialog windows like *Find* wouldn't register my clicks on buttons. it would set the focus to the button, but wouldn't click the button. i had to press *Spacebar* or *Return* to get the *onclick* action to fire.
 
> **karyook said:**
> I was experiencing this problem with eclipse and flash among other things...
problem solved!!!
work around:
export GDK_NATIVE_WINDOWS=1
$APP
Gangareen

i tested this and it works! thanks karyook =)

**BUT**: when i add this to my **~/.bashrc** file like this:
open a *gnome-terminal* window, then:
```
cd
gedit .bashrc
```scroll down to the bottom of the file and paste in this text:
```
export GDK_NATIVE_WINDOWS=1
```save and close the *gedit* window.
back in the *gnome-terminal* window run this:
```
source .bashrc
```
and then start eclipse, it doesn't fix the problem. why does it only work from the command line?

---

### Post by h4ppycl0wn on 2009-12-09
Hi,

Seems that many different mouse issues being raised here. A reminder, my issue was that mouse would move but clicks would not register at all. Restarting GDM fixed it but upon reboot the problem would recur.

@jorisjoris, I tried many different mice while X was running and no success. 

@FOBS1, I agree this is an issue to do with version. Mouse has always worked successfully up to 9.04. Problem immediately occurred on upgrade to 9.10.

@nickleus, tried this and no success. I think the solution you're suggesting is for problems on very specific apps, not an X/Gnome wide issue.

@misja, tried metacity in-place of compiz as window manager but saw same issue. Think it was more X related than specific window manager.

I say WAS because the issue has disappeared after last round of updates. I wasn't paying attention to exactly what updates were applied on 7-Dec but there was a new kernel (2.6.31-16) so maybe that did the trick.

So... thanks for everyone's help but problem has resolved itself. Just one of those very odd issues that I'll never get to the bottom of I guess.

Phil

---

### Post by bcboybuzz on 2009-12-09
Okay. I'm having pretty much the same problem with my mouse. Never had any kind of problem before upgrading from 9.04. Currently I am finding that r-clicking on the most recently accessed item (ie in the firefox window, or the taskbar, or whatever i last l-clicked on) and then l-clicking on whatever i actually want to use will restore functionality. But if a window pops up (ie a re-post warning in firefox when clicking the back button) then i have to clear that window with keyboard shortcuts or suffer a loss of mouse functionality. I am very underwhelmed with Krappi Koala so far. I have never had a single problem with any other version of Ubuntu, except during the learning process when pretty much everything I did seemed to break the system. I've tried every single suggestion i could find in this forum and others, and nothing seems to work. 'xev' seems to register clicks and releases, though it was my first use of that program and the data that flowed was almost pure Greek to me.

Somebody somewhere mentioned that the mouse wasn't 'giving focus' to the clicked app, and that seems to be the case for me. Once I can get focus to an app the mouse works fine, until I want to do something else. May have something to do with several things I've done recently:

A) again, somebody somewhere mentioned that the desktop bg image being larger than the resolution of my monitor may be an issue. I had recently changed the bg, so I switched it to something smaller than the resolution. No change.

B) recently installed GL-Dock. Ending process didn't help, neither did uninstalling.

Wierd thing is, the mouse thing did not occur immediately after upgrading (had other problems, like fglrx [don't get me started on that], to keep me busy), and the time between boot-up and click-failure is decreasing. I can basically load firefox and then I have to play 'scream-at-my-box-till-my-voice-dies' for the rest of the session.

Frustration city. For the first time ever, I'm disappointed in the Ubuntu team. I have never had that many problems after an upgrade before. Is it just me or do I detect the odiferous presence of a MicroSpoof engineer in the works?

Wanna know the best part? Thinking that this would be just like any other upgrade, I didn't bother with a backup. Turns out there's no easy way of getting Krappi Koala off my system short of a fresh install. Great. All that work to get the perfect OS, the perfect setup, the perfect perfection, and one upgrade ruins it all. Thanks a heap.

I hate to admit it, but I'm actually glad I'm a gamer, and kept my Windows OS. At least my $2K machine is still useful to me, despite efforts to the contrary.

My ten cents (inflation ;))

---

### Post by bcboybuzz on 2009-12-10
Did some more webcrawling, and came up with a thought. How long has the 'evdev' driver been in use? I can't remember if it was used in Jaunty. Seems likely that if the driver was changed and now the hardware doesn't work, the driver must be fubar. Anyone here with more experience able to show me how to revert to another driver? Using Logitech MediaPlay cordless USB mouse. I don't care in the least if all the buttons are working, as long as the first three (and the wheel) are.

---

### Post by pepsifx357 on 2009-12-10
Mine won't highlight or click and drag properly.

---

### Post by joe_pacific on 2009-12-12
Just wanted to add my name to the list of users affected by this issue. Generally my mouse (Logitech MX518) will work for a couple minutes after starting up, and then I'll lose left-click functionality first. After a while, the right click will stop working as well, and then I'm not able to even alt-tab through windows. This happened after upgrading to 9.10. 

Has there been a bug report filed? If so, could someone share the link? Many thanks.:o

---

### Post by bcboybuzz on 2009-12-12
Well, I figured out my solution. Bye bye, Krappi Koala, back to Jaunty for me. Couldn't get fglrx to load anyway, so there really wasn't any point in trying to get this fixed. Now I just gotta spend another year or so getting my OS set just the way I like it. Next time, though, I'm makin' a backup.

You really let me down this time, Canonical...

---

### Post by bcboybuzz on 2009-12-14
HA HA HA! Effin' great. The same bug just showed up in 9.04 after the install... Now what?

EDIT: please note that the bug did NOT show up immediately, but after a couple days of use... I suspect firefox somehow has something to do with it...

UPDATE: confirmed, technically not firefox...but when I removed flash plugins from repository, I regained the normal use of my mouse while using firefox...can anyone else confirm this? and does the newest plugin from adobe site work?

UPDATE #2: Not firefox's fault. Bug now shows up immediately upon startup...

---

### Post by bcboybuzz on 2009-12-16
Okay so here it is:

I also was affected by the mouse bug (where the focus/click wasn't working), after upgrading to Karmic. I also couldn't seem to get fglrx to work, so in frustration, I reinstalled Jaunty. 

For a couple days, all was well. Then, out of nowhere, the bug returned. Imagine my reaction to finding the bug in Jaunty, as well! Gee, that's effin' great, right? 

At first, I thought it was caused somehow by using Firefox, since the bug seemed to only show up after starting that program. But, before long, it was affecting my system right after boot up. So, I tested it on my Karmic and Jaunty LiveCD's as well. Sure enough, they both had it. So began a hearty round of wtf's...

Eventually, I wondered if maybe the LiveCD's were being affected by some config on my HDD. Yeah, I know, it's about as likely as getting killed by a falling zebra while walking down the street. Sure enough, the bug was still there after disconnecting everything but the DVD-RAM drive.

Finally, I thought about the fact that my keyboard and mouse were both connected to the same USB hub. So, what happens if I move the mouse to a different hub? Well, it would appear that this was the solution for me. I guess we'll have to wait a couple of days and see if the bug returns.

It's about this time that I wish my motherboard had a second PS/2 plug. I have a second mouse, but its part of a wireless combo that requires connecting to two PS/2 plugs. I also have a USB-PS/2 thingie, but the mouse won't operate on the plug I have. I guess it's keyboard only...

Anyway, I'll give it a week on Jaunty, and if the mouse bug doesn't return, I'll install Karmic, and see what happens. My /home is a mess anyway, and a fresh install might do some good. I'll post updates before and after the upgrade, and a week after that too, to show if it worked for good.

Concerns: what if Ubuntu decides it doesn't like having a mouse on that hub too? It's not like I have an infinite number of USB slots to play with...And when the bug first showed up, the mouse and keyboard were NOT on the same hub...At least, I don't think they were. I was rather busy with the whole fglrx thing at the time the bug showed up...

Anybody who reads this post: Try putting your mouse on a separate hub from your keyboard. If that works, post your success. If not, post that too! The more data we collect, the faster we can get rid of this extreme annoyance. 

There's a great many posts about this bug all over the net. If I visit any, I'll refer them to this post. 

Good luck.
BC

---

### Post by Emilie on 2009-12-17
***
EDIT: Ok, this does *not* work :(  I'm leaving it here for reference.

Everything was fine after a couple of reboots... it seems like when I suspend something gets messed up permanently.  Does that sound familiar to anyone?
***

Hello, I seem to have it working, with fglrx, flash, compiz, etc.  I let you know if it resurfaces in a few days, hope not!

Background:
- I had this problem with both 2.6.31-16-generic, 2.6.31-15-generic kernel, with the default radeon driver, the radeonhd driver, and fglrx
- Firefox doesn't seem to be the problem but I think it's must interact with the input device interface in such a way as to make the bug show up easier than other simpler applications
- Both with the touchpad and the USB mouse

Setup Now:
- Fully updated karmic system
- 2.6.31-16-generic kernel
- xserver-xorg version: 1:7.4+3ubuntu10
- Fglrx driver 9.11 (8.671) from ati

What you need to do is install the newest version of evdev over top of your installation.

First make sure you can build things on your computer:
```
sudo apt-get install build-essential
```Next download [xf86-input-evdev-2.3.2.tar.gz]("http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/") and [util-macros-1.4.1.tar.gz]("http://cgit.freedesktop.org/xorg/util/macros/"). (click on the names of the files)

Now you need to install the xorg macros:
```
tar -zxvf util-macros-1.4.1.tar.gz
cd util-macros-1.4.1
./autogen.sh --prefix=/usr
sudo make install
cd..
```Now you need to install the new evdev driver:
```
tar -zxvf xf86-input-evdev-2.3.2.tar.gz
cd xf86-input-evdev-2.3.2
./autogen.sh --prefix=/usr
make
sudo make install
cd..
```Now Reboot.  Good luck, I hope this helps someone.

---

### Post by EricDrijv on 2009-12-17
Maybe look here? 
[http://www.webupd8.org/2009/11/fix-mouse-clicks-not-working-in-flash.html](http://www.webupd8.org/2009/11/fix-mouse-clicks-not-working-in-flash.html)

It's not only about flash also about Ubuntu

---

### Post by Emilie on 2009-12-19
**** EDIT: Ugh, so it came back.  Installing GRUB2 didn't help.  It has to be in Xorg somewhere or devicekit/hal.  I am going to try downgrading Xorg and upstart.   The instructions below probably won't help you.  ***

Ok, so I am hesitant to post success but so far it is working with a number of reboots, suspends, and hibernates.  Here's my reasoning:

- The mouse works in other OSs => not the hardware
- It happens on many different kernels => not the kernel
- It happens with the open-source ati driver, radeonhd, and fglrx => it's not the video driver
- It happens with metacity and with compiz => it's not metacity or compiz
- It happens with old, current, and new versions of evdev => it's not evdev
- Furthermore: it happens with the touchpad AND with external pice => not synaptics or evdev (ie not mouse driver)
- It happens with a newly rolled version of mesa => its not mesa

So, the problem is that windows and window elements are not correctly receiving the focus.  It's not the device, not the device driver, not the video driver, not the window manager, and it's not the kernel.  What's left?  **Xorg.**

What I did was install a newer version of xorg from xorg-edgers.  To do this:

- Open synaptic package manager
- Go to to repository configuration
- "Other" sources tab
- Click "add"
- Add: "http://ppa.launchpad.net/xorg-edgers/ubuntu" for URI, "karmic" for distribution, and "main" for the next line.  Ok, close.  Then hit Reload/Refresh in synaptic to get the new packages.
- I found and updated the following packages: ```
xserver-common 2:1.6.4-2ubuntu4
xserver-xephyr 2:1.6.4-2ubuntu4
xserver-xorg-core 2:1.6.4-2ubuntu4
xserver-xorg-dev 2:1.6.4-2ubuntu4
xserver-xorg-input-evdev 1:2.2.5-1ubuntu6
xserver-xorg-input-synaptics 1.1.2-1ubuntu7
xutils-dev 1:7.5~1ubuntu0sarvatt

```Reboot and cross your fingers.

As a final note.  I have a R600 based card (Radeon HD 2400XT) and we can finally get full 3d acceleration without fglrx!  Hooray!  To do that, install the next-drm kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/current/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/drm-next/current/") (install the image and the headers, "all" and for your arch).  Then follow [http://www.phoronix.com/forums/showthread.php?t=17603](http://www.phoronix.com/forums/showthread.php?t=17603) starting from step 5.

So far so good, here's hoping it stays fixed!

---

### Post by joe_pacific on 2009-12-19
I heard from other people that upgrading to grub2 fixes the issue. I tried that out, and sure enough, there are no problems after 5 hours. Usually I would lose mouse functionality within 5 minutes.

Go [here]("https://help.ubuntu.com/community/Grub2") for instructions on how to upgrade. It's pretty easy to do.

---

### Post by DarthDogCow on 2009-12-20
Hi Folks,

I have the same issue, however I have a workaround, which at least works on my Dell XPS M1710.  It's actually the same workaround I use to get around the M1710 intermittent video corruption, and is as follows:

Invoke the screen blanking script:

  ***[FONT="Courier New"]/usr/share/acpi-support/screenblank[/FONT]***

It seems to kick the window manager (or whatever is the source of the problem) back into life.  I have it bound to a keystroke so I don't need to keep shutting the lid.

Anyone want to try it out and see if it helps?  It's certainly preferable to a reboot or X restart.

Cheers,

Warren

---

### Post by Emilie on 2009-12-20
Hey, so maybe I am completely losing my mind here... this bug is stressing me out.  I installed a clean Karmic installation on another partition, no fglrx or anything fancy.  I got the same bug, not only with the install but on the Karmic Live CD!  This is weird because my Karmic worked fine for a month before I installed fglrx...

Then: I did a clean Jaunty install.  No problems, the bug doesn't show up.

BUT: If I go into my old Karmic install, and the mouse problem is active, then I reboot into the clean Jaunty install: the bug is there!!!  If the mouse problem is active in my Karmic and I reboot into the Jaunty Live CD, I also get the bug!

This is crazy.  Does this mean that something gets loaded into video cache/ram and doesn't get flushed?  Or the card gets put into a certain state that persists?  Can anyone else confirm this or am I totally crazy?

I would blame it on hardware but it happens for my touchpad, and for two different USB mice that work fine on other computers.

So I guess what I am suggesting is this: is it possible that something in Karmic, possibly related to installing of the fglrx drivers (even if they are uninstalled later), is loading something into the graphics card that a) causes the mouse problem and b) doesn't get flushed out on a reboot and can cause the problem in other installations (maybe OSes)?

Has anyone gotten this bug without an ATI card?  Has anyone gotten it if they have never had fglrx installed on their system?  Can anyone confirm that this bug persists in this way so I don't think I'm losing my marbles?

---

### Post by DarthDogCow on 2009-12-21
> **Emilie said:**
> 
Has anyone gotten this bug without an ATI card?  Has anyone gotten it if they have never had fglrx installed on their system?

I can confirm that this occurs with NVidia GPU's too.  I haven't had an ATI card in years and have seen this on two machines so far.

Warren

---

### Post by joe_pacific on 2009-12-26
> **joe_pacific said:**
> I heard from other people that upgrading to grub2 fixes the issue. I tried that out, and sure enough, there are no problems after 5 hours. Usually I would lose mouse functionality within 5 minutes.

Go [here]("https://help.ubuntu.com/community/Grub2") for instructions on how to upgrade. It's pretty easy to do.

Just want to say that I thought this did the trick at first, but the mouse problem hasn't gone away. This is super frustrating. I've thought about doing a complete reinstall, but I've heard others have tried that and still had the problem. 

What now? :(

---

### Post by hewee on 2010-03-29
My wife is currently experiencing this problem.  She has been using a fresh installation of Karmic (64-bit) for over a month now, and had no mouse issues until a couple of days ago.  Nothing significant changed on her system (a couple days before it started happening, she updated Kerberos, Samba, gstreamer, and 'devicekit-disks'; nothing mouse-related).  I've been using 64-bit Karmic for much longer and have never experienced the problem myself.

We thought at first it was a sticky button on her mouse, but we switched from her Microsoft optical USB mouse to a wireless USB mouse and the problem continued exactly as before.

She has observed the problem in google chrome (both in a flash app and on a link in a normal HTML page) and in aMSN.  It might occur elsewhere, but we're currently unsure.  The symptoms are that the occasional mouse click is ignored.  Sometimes the first click is responsive, but sometimes she has to click two or three or even five times just to switch tabs or activate a button or follow a link.

NONE of the suggested solutions on this thread help.  We have tried the export GDK_NATIVE_WINDOWS=1 solution, and restarting X/GDM, and rebooting the computer, and the screen blanking.  Unplugging and reinserting the USB mouse MAY help for a minute or two, but if so the problem quickly returns.  Otherwise, no help whatsoever from any of this.

This stinks.  I've been an avid Linux user for years, and just convinced my wife to try it.  She's been happy with it for a month or so, but now she can't even use her mouse without irritation.  If anyone has any other suggestions, I'm itching to hear them....

EDIT: One more note.  I've looked in /var/log/messages and /var/log/syslog and /var/log/Xorg.0.log, and aside from the normal messages that get posted when the mouse is unplugged and plugged in, there doesn't seem to be anything mouse related.

---

### Post by atisss on 2010-04-25
I started to have problems with my mouse yesterday. 

Last updates were week ago, and I'm running 9.10 for a long time already.

I have observed that mouse click is received on some previous location of mouse, not the current one. For example I try clicking on browser tab or skype icon to switch, then click somewhere else, and I still got the previous click. That makes very frustrating to switch windows, or sometimes even operate inside them. 

For example if I have open Konsole on the background, then Skype popup, and I click on skype window it will still receive click on konsole window. The same goes for Gnome menu and taskbar. 

What's weird that keyboard works great, with exception to Alt+Tab - so practically no way to switch windows.

Sometimes switching to terminal (Ctrl+Alt+F1) and then back to X (Alt+F7) helps for few minutes, sometimes it doesnt.

I use fglrx on ATI card, but there's also integrated nvidia (without driver however)

---

### Post by atisss on 2010-04-26
Apparently my mouse's middle button was pressed all the time (due to damaged button). So I got really weird symptoms:

Everything works when first right-click then left-click.
Alt+Tab doesn't work.
xev shows that window receives all events even when out of focus, so only top-most window can receive events, switching to other windows is problematic (only right-click first, left-click after sometimes works)..

I wonder if this is something software can detect, and show up as warning.. I.E. "your middle mouse button has been pressed longer than 1 minute".

---

### Post by ubeautu on 2010-05-28
> **joe_pacific said:**
> Just wanted to add my name to the list of users affected by this issue. Generally my mouse (Logitech MX518) will work for a couple minutes after starting up, and then I'll lose left-click functionality first. After a while, the right click will stop working as well, and then I'm not able to even alt-tab through windows. This happened after upgrading to 9.10. 

Has there been a bug report filed? If so, could someone share the link? Many thanks.:o
yes, same sort of thing has been happening on my laptop. Its an intermittent problem, i have had since 9.10 (when I started using Ubuntu) and now it still occurs in 10.04. It can happen in pretty much any program but i seem to notice it most acutely when I'm typing in a web page text box in Firefox and then it crashes and I lose all that I had written, thats when it really tests my peace and happiness. ( just happened  when I was in Google reader and sent a great email comment from the blog (took 10min to write and then lost it when it did a random lock up of the left mouse button and jumped up the page)
 
My wife uses the same setup on her toshiba notebook but does not have the same problems I do.

I am on an Asus F3s notebook and my version of Ubuntu is Gnome 32bit and use ATI Catalyst Control Center
--------

---

### Post by mrmodem on 2010-10-03
This thread seems related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/637208"). There is a temporary solution further down in the comments, using the xinput command.

---

### Post by beenny on 2011-01-03
Having just read through this I've tried some of the fixes to no avail. Like others I can move my mouse (wireless logitech) but it doesn't register clicks (all the time).

I'm running 10.04 since May and the problems came out of the blue.

One thing that I've noticed, that no one else has brought up, is that I have no problem if I take out my mouse and just use my touchpad (using Dell Latitude). I was curious if anyone else had this situation and if this helps diagnosis.

I'm more of a novice so don't have any great insight but it would be excellent if a fix were found...

bg

---

### Post by Kaileo on 2011-01-09
I just did a recent update on my Ubuntu booted portion of my ASUS eeePC, and I'm encountering the same problems; I'm unable to click anything around Ubuntu. I can navigate with the keyboard, but my touchpad clicks don't register, either.

I know for sure it's not my touchpad or my mouse in regards to hardware, because I've also got Windows 7 dualbooted, and they appear to be working fine in there.

When I had my desktop computer, I ran into the same problems, both with 9.10 and 10.04. I'd originally blamed it on the fact that it was 10.04, but I ended up with the same issues on 9.10, so I knew it wasn't that. Thing is, I was also running on an old, failing drive [it failed a month later on me], so I thought that would fix it.

I've been running Ubuntu now for... A few months. My laptop's only about 6 months old, so I don't think it could be a drive failure [unless it's because I use it a lot...]

Basic gist: my wireless mouse won't scroll, click, nothing. I don't think it's a hardware issue considering the mouse still works on Windows. I've been using Ubuntu for a few months - and quite a bit, mind you - and I've never had problems until now. I had to use CTRL + Alt + Delete in order to restart my laptop and boot into Windows; I couldn't click anything on the panels or any windows I had open.

I'm going to try some of the fixes, but how well I'll be able to navigate to actually do the fixes could be difficult...

---

### Post by gsgleason on 2011-01-09
My suggestion would be to test with a current (10.10) live bootable CD/usb and see if it works.  If so, I'd back up your home directory and reinstall from scratch with 10.10.

---

### Post by berniev on 2012-03-06
Since 11.10 I had noticed that the mouse cursor needs to be stable, not moving, when a button is clicked or it is ignored. Even the slightest movement when clicking and no response to the button. This was becoming painful.

While writing this note I went to system->mouse and tested button operation on the little smiley face there. I changed no settings. I was surprised to see button clicks were responsive there. Exit that and back to this note and it is still fine.

Did something in mouse settings update itself? 

I don't know but all of a sudden mouse clicks are easy again!!:D

---

