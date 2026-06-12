---
title: "Can't start Ubuntu at all - black screen after boot process"
date: 2006-03-13
forum: General Help
---

### Post by MatthewD on 2006-03-13
I seem to be having a problem getting Ubuntu to work for me, and I was wondering if anyone could help.

My problem is that I can't seem to boot any form of Ubuntu at all. I've been trying several different versions, including the latest one, one or two older ones - both Ubuntu and Kubuntu, but none make any difference.
 
Whenever I try to boot the live CDs for each of these, and even when I tried doing a full install once, I always just get stuck on a black screen, often with a little line like a command prompt-type thing in the corner (which isn't blinking, just static). 
Most of the time, the keyboard doesn't work (pressing something like Caps Lock doesn't make the light come on) nor the mouse, it's just totally unresponsive and nothing happens. I'm not sure if that's been the case recently or not (about the keyboard and mouse being unresponsive), I think it was just the display.

This always happens after i've got past the first screen with the boot options, after it's booting up, when a load of text has gone by. 
With the latest version i've tried, it got to *Starting GNOME display manager...*, then came to the black screen again.

I'm sure I remember someone I know (Seth, think he's a member of this forum actually.) saying to me that it might be because I have two graphics cards on the system i'm trying it on. One is an Intel Integrated one, and the other - the one I use - is a nVidia PCI one which was installed.
I can't remember if that's what was said or not exactly, but i'm sure I wasn't imaging it, as it sounds like it could have something to do with it :p
I've tried switching the monitor from one card to another, but that makes no difference either.

So it's basically starting up, getting to the options screen right at the start, trying to boot, then it gets stuck at this black screen, most recently after it says it's starting the display manager.

I'm not sure what other bits of information I could give to help, so sorry if i've missed something. 
You'll also have to excuse me, since while i'm not totally new to Linux, it does confuse me a little.
It's also a bit late at night, so sorry if that post made no sense :neutral: 

So anyway, I was wondering if anyone at all could help, it would be appreciated. It doesn't matter too much if it doesn't work, but I would like to try it out. Thanks in advance for any responses on this :)

**Edit:** Oh, and sorry if this was in the wrong forum, wasn't too sure what to put it under.

---

### Post by Teroedni on 2006-03-13
So do you need to use booth cards

If not go into bios and disable the onboard graphics card.

---

### Post by MatthewD on 2006-03-14
[QUOTE=Teroedni]So do you need to use booth cards

If not go into bios and disable the onboard graphics card.[/QUOTE]
No, I think it should be fine without the built-in one.

I'll try disabling it in the BIOS as you said then, never thought of that before.

---

### Post by followme on 2006-03-14
you can also try this.  after the screen goes black, plug the vga connector to the other video port.  If you still don't see anything, then it must be your video wasn't configured properly during the setup.  Most likely the bootup is on your onboard card, but then switches to your regular video card for the main display.  After you try to disable one of them in the bios, try to configure your video again.

---

### Post by ElBarto87 on 2007-02-16
I have the exact same problem. But, I don't have any onboard graphic card. Just a Radeon X800XT. Does anybody know a solution to this problem?

---

### Post by larrywho on 2007-02-16
I have a similar problem, but have found a way to boot. I boot using the safe graphics mode and after all of the configuration is complete, I enter "init 2" at the prompt. This starts up GNOME. If I boot using the non-safe graphics mode, I eventually end up at the blank screen with a cursor flashing in the upper left corner of the screen. I am trying to figure out the difference between going into single user mode (via safe graphics mode selection) and then into multi-user mode via init 2, and just booting into multi-user mode directly.

---

### Post by ElBarto87 on 2007-02-18
Anyone?

---

### Post by chinese_ys on 2007-02-18
I am not sure what is the exact reason you can not bootup. But there must be something wrong on you graphic confugeration during the procedure of bootup. So try to install again use alternative version again, hope problem will be solved.

---

### Post by ElBarto87 on 2007-02-22
I don't know how to change my grafic configuration.
I can't boot up, neither from the dvd or after I've installed Ubuntu in text mode (or something).

How can I solve this problem?
Could it help with a Geforce card instead?
I'm gonna borrow one from a friend tomorrow.
Is it possible to install drivers for my present grafic card later if it works witht the other one?

---

### Post by DaEarl on 2007-10-28
I can't believe what is happening ! Everything went fine until the first restart. Before I updated a few programs in linux (firefox etc.) and downloaded a few (some kind of pdf reader)
I downloaded also an ati driver package or what and switched to default radeon because I thoght that that would be ok. I haven't noticed anything after the switch. So I tried to boot into vista.
Everything vent fine. So I wanted to go/boot back to linux, BUT (!) it's only booting until the "kernel is ok" tipe message. I only get a black screen and no activity. I can't even switch to console mode by pressing ctrl+alt+F2 F3. The only thing that works is the crtl alt del combination sad.gif So I thought that vista overwrited the boot so I tried to boot in linux recovery mode. It boots without problem. So I thought that I've made wrong by the graphical things, so I reconfigured the xserver-xorg. After booting nothing new, just the inactive black screen. So I managed with help of a friend to download the ati driver for the hd 2000 series somevere and run the install. It said that it installed succesfuly but after restart no changes just the black screen. So I put the live cd back and boot from it. It runs ok, it sees even a few files from the installed linux f.e. the desktop files of my account in the installed linux and stuff like that. So my question is what is the problem? Why doesn't it want to work? I don't even know if I made a mistake, or something else happened... is by linux something like a reinstall? I don't even know what problem causes this error. Or where should i search for some kind of a log file. Please help. Is there something like a repair option?

---

### Post by DaEarl on 2007-10-28
It boots until it writes: Kernel alive
<something> @ 80000000000000 <-or something like this I'm not sure

This is the last line on the screen , then everything disappears and the black screen comes out. (In live cd version ubuntu loading bar comes after it)

---

### Post by the_virus on 2007-11-12
I have a problem with my Medianix live CD. After the boot process, I can't see anything, the screen is blank. I don't know what is the problem because i boot from the same CD but from another computer with similar configuration (my video card ATI RADEON 9550 128Mb/128 bits, the other 256 MB/128 bits) and is working perfectly. Does any one know what I have to do? 
PS : I've wrote on the MEdianix (morphix) forum but no ne answer to me...so I will be verry gatefull to those who have a solution for my problem!
 Regards, the_virus

---

