---
title: "Screen resolution problem"
date: 2012-04-12
forum: General Help
---

### Post by brosville on 2012-04-12
Been trying for hours to sort the following problem - reinstalled 11.04, since when I can't get my monitor's resolution to work properly - I've tweaked the Nvidia x- server settings, which show several resolutions, the maximum being 1360x768 - it will run ok on 1152x864 (but circles are flattened ovals), but if I try to get it to run at it's proper resolution (1440x900), it will do so, but the top and side of the screen "disappear off the edges" - help!

---

### Post by roelforg on 2012-04-12
Post the output of:
```

cat /proc/cmdline

```

Check if nvidia's config app has an 'overscan' button, use this to fix the edges (but maybe your screen just won't take the resolution?)

---

### Post by brosville on 2012-04-12
BOOT_IMAGE=/boot/vmlinuz-2.6.38-14-generic-pae root=UUID=b028fb7c-7c37-4f08-8375-5bfc71112124 ro quiet splash vt.handoff=7

---

### Post by roelforg on 2012-04-12
> **brosville said:**
> BOOT_IMAGE=/boot/vmlinuz-2.6.38-14-generic-pae root=UUID=b028fb7c-7c37-4f08-8375-5bfc71112124 ro quiet splash vt.handoff=7

Reboot, when grub shows it ugly face:
hit e
navigate to the line you posted above and insert this after quiet (add a space before it and after it):
```

nomodeset

```
Hit ctrl-x
if it works, post so and i'll tell you how to make it persistent

---

### Post by brosville on 2012-04-12
That broke it! (I had to resort to the "boot repair" cd as it caused it to "freeze", either on the Asus flash screen, or a green message saying "input signal out of range"):confused:

I'd only got as far as hitting "e" when it froze

---

### Post by roelforg on 2012-04-12
> **brosville said:**
> That broke it! (I had to resort to the "boot repair" cd as it caused it to "freeze", either on the Asus flash screen, or a green message saying "input signal out of range"):confused:

I'd only got as far as hitting "e" when it froze

What part of "not persistent" was unclear?
Just a reboot and grub would have reset itself!
Permanent changes have to be made in /etc/defaults/grub followed by
```

sudo update-grub

```

---

### Post by brosville on 2012-04-12
Really sorry, I'm not particularly adept at this  - I've found the file, and tried to edit it, but it won't let me.....

Do I gather that the correct place to put "nomodeset" is after the word "quiet" here - 
"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

---

### Post by brosville on 2012-04-12
ps, just to clarify, I did as was suggested - 
"Reboot, when grub shows it ugly face:
hit e" - as soon as I hit "e" it froze - I tried several times, and eventually it wouldn't boot at all, and had to resort to the "repair boot" cd

---

### Post by roelforg on 2012-04-12
> **brosville said:**
> Really sorry, I'm not particularly adept at this  - I've found the file, and tried to edit it, but it won't let me.....

Do I gather that the correct place to put "nomodeset" is after the word "quiet" here - 
"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


Wait, i meant if nomodeset worked.
you said it didn't so this only hurts!
I also advise installing openssh-server in case you break video-config.
Can you post the output of:
```

sudo lshw -C display
sudo lspci

```
the first one will take time, wait for the prompt to return (might appear stuck at "pci (sysfs)", it's just scanning)

EDIT:
nomodeset might work but i'm lost as to why grub freezes...
you need sudo to edit /etc/defaults/grub

---

### Post by roelforg on 2012-04-12
> **brosville said:**
> ps, just to clarify, I did as was suggested - 
"Reboot, when grub shows it ugly face:
hit e" - as soon as I hit "e" it froze - I tried several times, and eventually it wouldn't boot at all, and had to resort to the "repair boot" cd

:confused:

e lets you edit the params grub passes to the kernel for this boot only, it'll read it's config again on reboot and reset.

---

### Post by brosville on 2012-04-12
*-display               
       description: VGA compatible controller
       product: C61 [GeForce 7025 / nForce 630a]
       vendor: nVidia Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:22 memory:de000000-deffffff memory:c0000000-cfffffff memory:dd000000-ddffffff memory:dffc0000-dffdffff

00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control

---

### Post by roelforg on 2012-04-12
Check if "Additional drivers" has some nvidia ones ready.

---

### Post by brosville on 2012-04-12
Yes, I've installed the Nvidia X-server setting thing, and I've tried to set it to 1440x900, but to no avail..........
Thanks very much for all the help - I've been flogging away at this for hours, and I'm nearly falling asleep, so will have a night's rest, and return to it tomorrow

---

### Post by roelforg on 2012-04-12
its 2am here, good idea to go sleep.

---

### Post by brosville on 2012-04-13
Where to now? - I've been doing some searches, and a great many people seem to have got nowhere fast trying to make 1440x900 work with Nvidia drivers - I haven't yet found an answer to the problem - just lots of frustration by those afflicted.

What is most frustrating is that it's been running fine until I "updated" my 11.04 install - I've changed no equipment at all - a couple of days ago it was fine.........

---

### Post by roelforg on 2012-04-13
> **brosville said:**
> Where to now? - I've been doing some searches, and a great many people seem to have got nowhere fast trying to make 1440x900 work with Nvidia drivers - I haven't yet found an answer to the problem - just lots of frustration by those afflicted.
 
What is most frustrating is that it's been running fine until I "updated" my 11.04 install - I've changed no equipment at all - a couple of days ago it was fine.........
 
Wait...
Try upgrading to 11.10...
My desktop has nvidia, ubuntu 11.10 and an even bigger resolution,
nvidia has newer ones for 11.10.

---

### Post by brosville on 2012-04-13
Ok, will try it - I've nothing to lose - to be frank, I think I'll do that, and then probably remove all my data and migrate to Mint when I have the time (I loathe Unity with a passion!)

---

### Post by roelforg on 2012-04-13
> **brosville said:**
> Ok, will try it - I've nothing to lose - to be frank, I think I'll do that, and then probably remove all my data and migrate to Mint when I have the time (I loathe Unity with a passion!)
 
With a bit of tweaking, unity can run/look pretty good.
I like the 11.10 unity over the 11.04 unity.

---

### Post by brosville on 2012-04-13
Many thanks - I've started the upgrade process, and I'll let you know how I get on!

---

### Post by brosville on 2012-04-13
aaaaghhhhhhh! Now fully updated to the ghastly 11.10 with Unity -can't find a bally thing......... and it's STILL refusing to play ball - the best compromise is to set it to 1152x864, if I set it to 1440x900 it all "disappears off the edges"...........:confused:

First thing to do, try to find some alternative to this appalling desktop!

---

### Post by brosville on 2012-04-13
now got Xubunto or XFCE, still won't run on 1440x900 without falling over the edges (on either)....

---

### Post by brosville on 2012-04-13
Just installed Gnome, and have something remotely resembling a proper desktop, but am still stuck on the lower resolution (with squashed circles....)

---

### Post by brosville on 2012-04-13
interting, tried to tweak it, and got "/usr/bin/gnome-display-properties" (No such file or directory)"

---

### Post by brosville on 2012-04-13
I've now tried it with 3 different monitors, not one of them will give a properly-sized display  - I've also tried all the different Nvidia drivers available in the Nvidia server X thing..... all to no avail - I've found several threads on various fora discussing similar problems - noone seems to have an answer!

---

### Post by pneaveill on 2012-04-13
Am having a quite similar problem. Should I enter my stuff here or start a new thread?

Am heading to bed here and will try to look before work tomorrow.

Thanks in advance.

---

### Post by roelforg on 2012-04-14
I think your overscan is set to high,
i had the reverse where the screen wouldn't fill on it's native res once, i haxed overscan out in config to get it to fill,
maybe you need to lower it.

---

### Post by brosville on 2012-04-14
how do I do that? I've just spent the best part of an hour trying to get it usable - every time I reboot it takes a long time displaying "input signal out of range", and then starts up with a ludicrously large display (about twice as wide and high as it should be), so all I can see is a small portion of the screen at any one time. It's so bad I switched it off and am writing this from my "spare" laptop

---

### Post by roelforg on 2012-04-14
> **brosville said:**
> how do I do that? I've just spent the best part of an hour trying to get it usable - every time I reboot it takes a long time displaying "input signal out of range", and then starts up with a ludicrously large display (about twice as wide and high as it should be), so all I can see is a small portion of the screen at any one time. It's so bad I switched it off and am writing this from my "spare" laptop
 
You may need to play with it to make it work...
Overscan makes the video card compensate for differences in expected and physical size of the monitor.
Sometimes the card lowballs and sometimes it highballs...
My 2 laptops have ati cards, maybe nvidia has a differenct meaning for overscan?
 
Wikipedia: [http://en.wikipedia.org/wiki/Overscan](http://en.wikipedia.org/wiki/Overscan)
In vga signals, there can be timing problems and overscan can compensate for this by offsetting the timer.
In moders lcd panels no area is hidden, every pixel is assumed to be working and visible.
 
Sadly, that isn't always the case as some screens claim to have more pixels than they really have visible.

---

### Post by brosville on 2012-04-14
I think Nvidia may call it "panning"  -once you've installed the additional drivers you get an interface with lots of options, one of which is panning  -I've tried all sorts of settings.......
It's just crashed and I'm having to run the "boot repair" cd, and the interface of that is displaying perfectly

---

### Post by roelforg on 2012-04-14
> **brosville said:**
> I think Nvidia may call it "panning" -once you've installed the additional drivers you get an interface with lots of options, one of which is panning -I've tried all sorts of settings.......
It's just crashed and I'm having to run the "boot repair" cd, and the interface of that is displaying perfectly
 
Just rename /etc/X11/Xorg.conf to /etc/X11/Xorg.conf.broken
to reset any changes, this way Xorg will autodetect like the livecd does.

---

### Post by brosville on 2012-04-14
many thanks - will give it a try!

---

### Post by brosville on 2012-04-14
sorry to be so thick - I gather "Just rename /etc/X11/Xorg.conf to /etc/X11/Xorg.conf.broken" is a terminal job, and I don't have much of a clue how to do it - I found the file, but it won't allow alterations

---

### Post by roelforg on 2012-04-14
> **brosville said:**
> sorry to be so thick - I gather "Just rename /etc/X11/Xorg.conf to /etc/X11/Xorg.conf.broken" is a terminal job, and I don't have much of a clue how to do it - I found the file, but it won't allow alterations

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken

```
Type this in the terminal you get with ctrl-alt-f1 (do this when your gui freezes) exactly like this as it's case-sensitive.
And reboot afterwards.

---

### Post by brosville on 2012-04-14
I did so,and rebooted- it's now just about usable having set itself to 1024x768 - this lot appeared when I booted

"CRTC 434: trying mode 1024x768@50Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 800x600@51Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 800x600@52Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 800x600@53Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 680x384@54Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 680x384@55Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 640x480@56Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 576x432@57Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 512x384@58Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 400x300@59Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 400x300@60Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 400x300@61Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 320x240@62Hz with output at 1152x864@53Hz (pass 0)
CRTC 434: trying mode 1024x768@50Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 800x600@51Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 800x600@52Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 800x600@53Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 680x384@54Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 680x384@55Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 640x480@56Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 576x432@57Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 512x384@58Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 400x300@59Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 400x300@60Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 400x300@61Hz with output at 1152x864@53Hz (pass 1)
CRTC 434: trying mode 320x240@62Hz with output at 1152x864@53Hz (pass 1)"

---

### Post by brosville on 2012-04-14
Just found another thread with a similar problem, and the following suggestion was made - "I had a similar issue and what helped was deletion of ~/.config/monitors.xml" - but yet again am unsure how I do that using Terminal

---

### Post by roelforg on 2012-04-14
> **brosville said:**
> Just found another thread with a similar problem, and the following suggestion was made - "I had a similar issue and what helped was deletion of ~/.config/monitors.xml" - but yet again am unsure how I do that using Terminal

You want this:
```

mv ~/.config/monitors.xml ~/monitors.xml.bak

```
Also, you can try:
```

sudo nvidia-xconfig

```
and reboot.

---

### Post by brosville on 2012-04-14
Tried it, and now have 640x480 - to be frank, I've wasted enough time on this particular problem - I'm borrowing a suitable external hdd, will save all my work, and go for a fresh install of Mint.......
Many, many thanks for all the help!

---

