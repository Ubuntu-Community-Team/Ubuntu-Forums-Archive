---
title: "Ubuntu sometimes crashes during boot"
date: 2010-12-28
forum: General Help
---

### Post by Borei on 2010-12-28
Hi,

I have a weird problem. Sometimes Ubuntu freezes when I'm booting up, sometimes not. I would say 2 out of 3 times it crashes, all other times it goes fine.

I alway get past the GRUB bootscreen, then it starts loading. Towards the end or so, all of a sudden all disk activity stops and the screen hangs. Ctrl+C, Ctrl+Z, Escape, whatever buttons I press, it doesn't do anything.

I removed the "quiet" and "splash" boot options in GRUB so I could see in detail what is loading, but this doesn't make any more sense then before. The lines of text are always a bit different every time it happens so I can't really pinpoint when it goes wrong. Anyway, I don't see anything wrong with the output on my screen, I guess the real problem is not displayed.

I also tried booting into recovery mode. Also here this is strange. Sometimes I make it to the recovery screen with the options (resume, clean, netroot, ...), sometimes it crashes before that. When I get the recovery screen I choose "resume", this usually works and then I use "startx" to go into graphical mode. However, at other times, when I choose "resume" it freezes even before I get a login prompt.

So please guys, tell me, what is the problem here? How do I find out where I should start looking. Ubuntu sometimes freezes and when it does it doesn't alway happen at the same place as before. I know only 1 thing for certain, once I'm fully booted I don't have any problems whatsoever, everything seems to work flawlessly.

I am running a dual boot system with Ubuntu 10.10 and Windows7/XP. I am running kernel 2.6.35-24 (also tried 2.6.35-23, but no difference). I have an i5 CPU, so 64 bits. If you need any more information, just ask.

---

### Post by tredegar on 2010-12-28
You are not alone.

I have 10.04LTS on 2 different laptops and 1 desktop (all 32 bit kernels), three very different users.

They all experience boot problems now and again, just like yours.

I tell the other users that when this happens they should press the power button until the system shuts down, and then try again.

This works, after a few attempts. There is no data loss.

> I removed the "quiet" and "splash" boot options in GRUB so I could see in detail what is loading, but this doesn't make any more sense then before. The lines of text are always a bit different every time it happens so I can't really pinpoint when it goes wrong.

I did the same, and am experiencing the same :(

The boot process seems to have become broken when ubuntu moved from SysV init scripts to "upstart", which seems to be a complete mess, although, when it works, the boot is indeed faster. But if you have to re-boot three times, the "time-saving" is negative, and can be very frustrating.

Now and again it says "I can't initialise the NVIDIA driver, what should I do?". I choose "Drop me to a root console", so I can sort it out. What does it do? It continues booting normally to my NVIDIA driven desktop. Crazy or what?

I don't think the 'buntu people know what they are doing any more.

Once I get to the desktop, applications that are supposed to start up at login, don't, unless I wrap them in scripts that have **sleep 60** as a start line, so everything else has a chance to be started before it is needed. Currently, 10.04 is trying to start up too fast, and not doing it at all properly.

Once it boots, if it boots, it mostly works. But why can't it boot reliably, or tell us why it has failed to boot, so we can attempt to fix it?

If they can't fix 10.04LTS in the next few months then I'm moving my users to another disto. "Debian Stable" maybe. Or fedora. Who knows?

For me, "ubuntu" currently = too much eye candy, and zero reliability. 

Ubuntu should ignore the teenager's "3-D cubic desktops", and it's "wobbly" and it goes "woooosh", it's "pretty" and instead, bring back the old-timers "It's not *that* elegant, but most things work, always, every time, all the time".

Mandrake linux used to be good, they fouled up in 2006 or thereabouts (a bit like ubuntu now). Look what happened to them (o)

Sorry if this has not given you the answers you'd liked, but maybe you'll understand why.

Here endeth the Rant.

---

### Post by Borei on 2010-12-28
Hi tredegar,

Nice to know I'm not alone. Altough you would think that with so many problems in 10.04, they would fix this in 10.10, but this doesn't seem to be the case then.

Anyway, I do understand a bit what you are saying. Myself, I have noticed that Ubuntu is more and more moving away from "mainstream" linux, if there even is such a thing, and moving further and further away from the other distro's. I don't know if this is a good thing, but if it continues to lead to problems like these then they should slow down and just make something that works. 

I mean, it's not a race, they don't have to upstage anybody. As long as it works like it should and people can use their computer for what it's meant to do, it should be good enough.

Hopefully they will get their act together, because I do like Ubuntu a lot. I have tried quite a number of distro's over the years, but in the end I always come back to Ubuntu. Would be a shame to abandon it again because of this.

---

### Post by Mark Phelps on 2010-12-29
I have similar problems in 10.10 -- more often than not, a routine boot ends in a black screen.

What I have done to "fix" this (I have "fix" in quotes because it's not permanent) is the following:
1) Boot into Ubuntu using Recovery Mode
2) Select the option to repair broken packages
3) When done, and the prompt is back, enter "startx"
4) This gets me the normal desktop -- where I do a normal shutdown.

This works fine for a few days -- until suddenly, it starts again.

I made the mistake of complaining about this on this forum, and the abuse I got in return was so bad that I had to have the thread moved to the Testimonials section to avoid the daily "bashing".  So, I have not brought it up since.

And, BTW, I have been using Ubuntu (and other distros) on my PCs daily for over 4 years now -- and Ubuntu 10.10 is the first (and only) distro and version to behave like this.

---

### Post by cetoka on 2010-12-29
I have dual boot with Ubuntu 10.04 LTS and windows XP.But ubuntu is my main distro.I have the same problems at boot sometimes once in a week sometimes once in a month.I simply press the shut-down button and restart as normal.But since I moved from Windows to Ubuntu last year I always fear that Ubuntu will not start as normal.

---

### Post by bergqvistjl on 2010-12-29
I have this same problem as well, its extremely annoying. Even the Ubuntu live CD (which wasnt using proprietory drivers) crashes in the same way every now and then. It usually happens once every 2 or 3 bootups. I thought it was my USB webcam being plugged in, but it wasnt. Someone should mark this as a bug of very high importance. I don't think its a problem with X though, as ive had it happen way before X is scheduled to start-up. There are no errors in the  Kernel either, just (i presume) the last operation during boot-up that worked and then a freeze. Memtest gives me no errors. I dont think its my hardware that's an issue tbh. Unless of course its my USB keyboard and mouse, but I can't do without them obviously lol

---

### Post by bergqvistjl on 2010-12-29
bump. any ideas/solutions?

---

### Post by Borei on 2010-12-30
Damn, I had no idea it was this serious. I was looking on the internet if somebody had the same problem as mine, but I couldn't find an exact match (well, I did found some reports, but they were not for 10.10).

So can anybody confirm if Upstart is the problem? Or if somebody knows a good work-around.

I suppose it's not possible to switch back to System-V init. :cry: bummer.

---

### Post by bergqvistjl on 2010-12-30
> **Borei said:**
> Damn, I had no idea it was this serious. I was looking on the internet if somebody had the same problem as mine, but I couldn't find an exact match (well, I did found some reports, but they were not for 10.10).

So can anybody confirm if Upstart is the problem? Or if somebody knows a good work-around.

I suppose it's not possible to switch back to System-V init. :cry: bummer.

I think it is upstart, along with a combination of USB devices somehow crashing the kernel. Has anyone launched a proper bug request in Launchpad? Also, I use a USB keyboard and Mouse, I can't simply stop using them as a workaround. This is an extremely major bug in my opinion. Worthy of delaying a release if it was found.

---

### Post by bergqvistjl on 2010-12-30
I've noticed that it freezes now always just BEFORE the fsck appears and you get the 
* starting process [OK] *
Messages coming up. I have 2 PCI tuner cards in my system, both of which i use for mythtv, I also have a USB Cherry Keyboard and USB MS Mouse, and a USB Infrared remote reciever for a windows media centre remote. The Infrared remote reciever has nothing to do with it, as the system still does this when its unplugged. The experimental driver warnings on the screen are also irrelevant as the system did this before I had those drivers installed (I need them to use my tuner cards in Mythtv). I've attached a pic (easier than typing it all out by hand) of the last things to come on the screen. I Dont think the display is completely frozen as the cursor is still flashing, yet there is no response from the keyboard at all, and the HDD light never flashes. I'm sure its something to do with the USB devices being plugged in. Still, it needs to be fixed ASAP. Occasionally i've also noticed it crashes just after X has started, (im using Xfce as the Desktop environment), the end result is usually the top panel has appeared, but the background image hasnt.

---

### Post by bergqvistjl on 2010-12-30
New low. 5 Goddam times! 3 it froze before the *starting [OK] * should appear, the other two were just after X had started so I had a blank screen with a non-moving mouse cursor. This is ridiculous. I will gladly give the devs etc. logs of my system etc. if anyone would listen

---

### Post by bergqvistjl on 2010-12-31
Any updates? I'm not letting this drop, its a serious bug.

---

### Post by bergqvistjl on 2010-12-31
Any updates? I'm not letting this drop, its a serious bug.

---

### Post by bergqvistjl on 2010-12-31
Any updates? I'm not letting this drop, its a serious bug.

---

### Post by bergqvistjl on 2010-12-31
Any updates? I'm not letting this drop, its a serious bug.

---

### Post by bergqvistjl on 2011-01-01
Sorry about the quadruple post.

---

### Post by bergqvistjl on 2011-01-02
OK well i've solved my problem I think. It actually was my tuner cards. (Strange as they work in windows all the time, no idea why they should only work in ubuntu some of the time). Oh well, next time im getting a PCI-E one instead of PCI tuners lol.

---

### Post by Borei on 2011-01-03
I have a TV tuner card as well, but I have no issues with it. Works fine in Ubuntu & Windows. How did you solve the problem? You just ripped the card out of your PC, or did you just unload the driver?

If it's a USB problem then I'm screwed. I have lots of USB devices connected. Mouse, keyboard, hub, printer, scanner, ...

---

### Post by greybot on 2011-01-15
My ubuntu 10.10 freezes during startup if I have the USB mouse plugged into my laptop. Will just hang with a cursor blinking top left, but as soon as I remove the USB mouse, it's as if the laptop is allowed to breathe again and the harddrive starts working and it boots up properly.

---

### Post by Borei on 2011-01-17
OK, problem sorta got solved. I installed a new kernel and update for the ATI graphics driver (fglrx).

On the plus side, my computer no longer freezes. On the other side, my tuner card no longer works in Linux.

So now I just have to figure out how to get my tuner card working again and hope the freezes don't start over again.

---

