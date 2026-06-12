---
title: "stability problems"
date: 2009-08-06
forum: General Help
---

### Post by groundnut on 2009-08-06
In general I like Ubuntu very much.

The problem is however that my Ubuntu computer crashes to often.
The computer totally freezes. I have to restart the machine in order to continue.

What could be the cause of the crash/freeze?

---

### Post by ajgreeny on 2009-08-06
Tell us more about your hardware or you stand no chance of an answer.
Laptop? desktop?  In particular how much ram, and what graphics card?  Also which version of ubuntu?

---

### Post by dlmarti on 2009-08-06
Please run the memtest program on the install disk.
Its been my experience that stability problems like this are almost always hardware related.

If the memtest program passes (after at least an hour of running), then please detail your hardware to this topic.

---

### Post by groundnut on 2009-08-06
It's a Pentium 4 desktop computer with 512 MB RAM.
MSI NX6200AX-TD graphics card (nVIDIA GeForce NX6200AX)

I have Ubuntu 9.04 (jaunty jackalope).

My Ubuntu 9.04 install disk is only an ISO image.
I think I can not run a memtest from that disk.

Maybe you meant the memtest from the site below.

[http://www.memtest86.com/]("http://www.memtest86.com/")

---

### Post by dlmarti on 2009-08-06
you can run memtest86 from the boot menu on the iso, just boot from the disk, and select memory test.

either that, or install memtest86 on your system and it will add it too the grub menu

---

### Post by fennec_fox on 2009-08-06
I would say it's a hardware issue. 
What type of freeze does it do? 
Does the screen just lock up? 
Does it drop into a command line screen when it freezes? 
Does the graphic interface crash? 
Does it crash when running a screensaver or coming back from a screensaver?

Basically, what is going on when it crashes? 

Hope you find some help!

---

### Post by groundnut on 2009-08-06
In the meantime I've run memtest86 once. It completed in 18 minutes without crashing.

**It's an instant keyboard and mouse freeze. Accompanied by a continuous sound.**
The screen remains visible (GUI), but it just fixates.

The system can crash in many different situations.
So it's difficult for me to so a systematic cause.

I listen a lot to streaming music via Firefox. Also I watch many videos online (I think it doesn't crash very often during watching online videos). I use Synfig 2D animation software,which crashes more than averige. But I always play streaming audio along with Synfig.




Basically, what is going on when it crashes?

Hope you find some help!
__________________
~Ren

---

### Post by hal8000 on 2009-08-06
Next system freeze make a note of the date and time.
Next reboot check through /var/log/messages for clues, something may have written to  the sytem log before the crash.

Easier still, with Jaunty, System, Admin. Log File viewer allows you to peruse all log files easily.

---

### Post by fennec_fox on 2009-08-06
> **groundnut said:**
> 

I listen a lot to streaming music via Firefox. Also I watch many videos online (I think it doesn't crash very often during watching online videos). I use Synfig 2D animation software,which crashes more than averige. But I always play streaming audio along with Synfig.



I'm not sure without seeing logs or something. Do you happened to remember if it crashed while you were just running music through firefox or while you were just using synfig? I was hoping to narrow it down to an application. If it's sound, it's possible it could be a sound card error. If it's synfig it's very possible it's a graphics card problem. I wouldn't be too surprised if it locked up because of graphics card issue during animations. If you could narrow it down, it could be a driver issue or a physical graphics card issue.

Try to do what hal8000 said and check logs. Even if you have a rough idea of when the last one was you can try to go through /var/log/messages and like hal said the system log in system - admin - system log is a nice tool. 

If you don't want to use the gui, don't want to download one or don't have it then for some reason try
cat /var/log/messages | tail -50         for the last 50 results
or
cat /var/log/messages | more           to go through pages.

---

### Post by reprobus on 2009-08-06
I would almost bet that your ram is going bad. I had this happen on an older machine, replaced the ram and that fixed it.

---

### Post by groundnut on 2009-08-07
@fennec_fox

When the system crashes I will follow hal8000's advise and see what it brings.

@reprobus

I keep in mind that I might have to replace the RAM.
The machine is 6 years old.
Now It has 512 MB RAM. Maybe I could replace it by 1024 MB.

---

### Post by groundnut on 2009-08-07
Today August 7, 14.48 hours Ubuntu crashed again.
I was only listening to streaming music of Jango.com. So the only application running was Firefox.

I have attached the log file. Shortly after the crash, I rebooted the computer.

Hopefully you can find something useful in the logfile.

---

### Post by groundnut on 2009-08-07
The log file was above the maximum size for a txt file.

So now I will upload only part of it.

---

### Post by fennec_fox on 2009-08-07
Aug  7 14:43:32 xp kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.

Reprobus may be right. Your ram might be going bad. It might also be the bios though. It might be setup incorrectly or the chipset isn't handling it right.

How much ram does Ubuntu report? use the command 
free -mt

or just use the system monitor tool to see memory and swap


[http://ubuntuforums.org/archive/index.php/t-1125470.html](http://ubuntuforums.org/archive/index.php/t-1125470.html)

---

### Post by martinbaselier on 2009-08-07
If you run memtest, keep it running for a long time (like a whole night), to get a trustworthy result. If it's been running for hours, you can be pretty sure your memory is ok. Memory errors do not have to occur constantly. 

You could also use -noacpi on your kernel to test if that's a problem. Press esc to enter grub while booting, then e to edit the options, go the kernel line, press e again, and then add -noacpi, enter, press b (to boot)

I believe -noacpi is the name of the option. I'm not 100% sure though.

---

### Post by fennec_fox on 2009-08-07
I don't remember a - being necessary. I think the command is just 
noacpi 
or 
acpi=off

I'm still thinking it's a bios thing and he might need to update or change something. He should at least check how much ram ubuntu is reporting but, trying noacpi might solve the issue.

---

### Post by groundnut on 2009-08-07
I don't understand wat the "npacpi" test is. En what output it gives.
I got to the kernel line and entered e then I got some response and then I tried both -noacpi and noacpi. But I got no result!

Yesterday the memtest86 has been running for about an hour. What should be the output of this test?
This night I will run memtest again. While I'm sleeping.



tony@xp:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:           497        456         40          0         15        200
-/+ buffers/cache:        239        257
Swap:         1458          0       1458
Total:        1956        456       1499
tony@xp:~$ You could also use -noacpi on your kernel to test if that's a problem

---

### Post by fennec_fox on 2009-08-07
Ubuntu is reporting that you only have 497mb of ram (it's probably 512 but that's how it's displaying) according to that command.

Do you actually have 512mb of ram or is it reporting the wrong number? 

acpi is just power management. Advanced Configuration and Power Interface.
It lets the OS control system states, memory, processors, etc. All noacpi does is turns off. There won't be any output but, the system may actually start working in some cases because the kernel will no longer be controlling those things as much.

---

### Post by groundnut on 2009-08-07
There must be 512 MB RAM.
497 MB would be very exotic.

---

### Post by ajgreeny on 2009-08-07
> **groundnut said:**
> There must be 512 MB RAM.
497 MB would be very exotic.
That seems about right.  The way ram sizes are sold tends to give slightly less than there should be eg I have 2GB ram but only 2013MB shows in free, instead of the 2048MB that should actually be there.

---

### Post by fennec_fox on 2009-08-07
> **groundnut said:**
> There must be 512 MB RAM.
497 MB would be very exotic.

What I meant is, is that close to the real number you have? Do you theoretically have 512mb of ram installed? What I was looking for is, does ubuntu report 497(512) when your computer actually has 2gb installed? If ubuntu is reporting the wrong amount of ram that would indicate a problem.

---

### Post by martinbaselier on 2009-08-07
> Yesterday the memtest86 has been running for about an hour. What should be the output of this test?

If there are errors, memtest will report them. So basically you don't want to see any errors. 

btw, have you tried to turn off visual effects. (desktop settings, no visual effects) This is just a general thing, just like the noacpi which might cause the problem, just to test if the system will be more stable afterwards. Random hang ups is one of the hardest things to solve, because it's just so hard to find the cause.

---

### Post by groundnut on 2009-08-08
Last night Memtest86 halted after running for 6 hours.

It reported zero errors.

It also stated: Unexpected interrups halting cpu0.

---

### Post by groundnut on 2009-08-08
Hello guys,

Are you convinced that the stability problems are caused by malfunctioning hardware?

---

### Post by lethalfang on 2009-08-08
I'm looking around the forum because I also have sudden freezing problems. 
One thing I've noticed about Jaunty is that it reports "weird" numbers in "free -m."

On my office desktop which does not have any freezing problem, the "free -m" reports 994 total RAM, although in the previous version (i.e. 8.10) it was more like 1024. 
On my laptop, "free -m" reports 3894, even though in 8.10 it reported something like 4000+. I've briefly installed Debian on this laptop after 9.04, and the reporting was back to 4000+. 

So I doubt the strange reporting of "free" is an indication of memory problem........ I'm still looking for the cause of my freezing problem.

For a while I thought it was compiz related, but it has happened when I've turned off compiz. 

I didn't have freezing problems in 8.10. One difference is that I'm using ext4 on 9.04....... don't know how likely it is the cause of freezing.

---

### Post by groundnut on 2009-08-08
I started using Linux / Ubuntu a little over a year ago.

I started with 8.04. I think I did not have freezing problems at that time.

Later I changed to 8.10. I definitely remember I had freezing problems at that time.

Now I use 9.04. The frequency of the freezes has increased over time.
At this time it happens to often.

---

### Post by hubertofliege on 2009-08-08
I switched to Ubuntu several weeks ago and have experienced something similar.  Overall, the system is very polished, except sometimes I experience crashes.

I too am running on old hardware.  I'm using a four year old Dell Latitude D610.

 The next time I have a problem, I'll check the error log.  I'm also going to run a memory test soon.  Although, I can already think of several actions which causes problems.

I won't go into the details, 'cause there is nothing to suggest that my problems are the same as groundnut's problems, but I'm going to try out some of this advice too, and if anyone wants me to try anything for comparison, I'd be glad to try.

If the problem is that my hardware is obsolete, I wouldn't be so upset, I'd work around it, I just want to know what my system is and is not capable of so I don't lose work in the middle of a project.

---

### Post by fennec_fox on 2009-08-08
> **groundnut said:**
> Hello guys,

Are you convinced that the stability problems are caused by malfunctioning hardware?

No, I am questioning if it is on Ubuntu. That's why I wanted to know if ubuntu was reporting the real amount of memory you have. 

Do you know if your computer physically has more memory than ubuntu reports?

---

### Post by groundnut on 2009-08-09
I know my computer has 512 MB RAM.

---

### Post by lethalfang on 2009-08-09
> **fennec_fox said:**
> No, I am questioning if it is on Ubuntu. That's why I wanted to know if ubuntu was reporting the real amount of memory you have. 

Do you know if your computer physically has more memory than ubuntu reports?

Jaunty reports RAM slightly less than other versions of Ubuntu and other distros, in all 3 of my computers, but only one of them (laptop, ATI video card, ext4) has freezing problems. 
I've also heard that some wireless card driver causes the freeze, considering that my laptop is my only computer that has wireless card.

---

### Post by groundnut on 2009-08-09
My computer is also on a wireless connection.

However I did not have to install a driver for my WiFi stick (adapter). It's included in Ubuntu already.

---

### Post by Barafu Albino Cheetah on 2009-08-09
most surely hardware problem, do thorough checks. May be overclocking? On some mainboards BIOS settings default to light overclocking. 
Another possible source is pulseaudio. try disabling it. set autospawn = no in /etc/pulse/client.conf

---

### Post by groundnut on 2009-08-09
I just disabled pulseradio.

Hopefully this solves the my problem.

---

### Post by groundnut on 2009-08-09
It didn't help.

The system froze again.

---

### Post by Loosewheel on 2009-08-09
If you are running 2.6.28-14-generic kernel, try 2.6.28-13-generic kernel.
I had similar problem, system freeze with the -14 kernel, and this is the third day running -13 kernel with no lockups....

---

### Post by lethalfang on 2009-08-10
> **Loosewheel said:**
> If you are running 2.6.28-14-generic kernel, try 2.6.28-13-generic kernel.
I had similar problem, system freeze with the -14 kernel, and this is the third day running -13 kernel with no lockups....

My freezing problems also seem to have started after I've upgraded the kernal. 
I've installed linux-backports-modules-jaunty (from what I understand, it includes the backported wireless driver for my wireless card) yesterday, and I haven't yet experienced a freeze yet, but it's only been a day so I don't know .....

---

### Post by P4man on 2009-08-10
> **groundnut said:**
> Last night Memtest86 halted after running for 6 hours.

It reported zero errors.

**[COLOR="Red"]It also stated: Unexpected interrups halting cpu0.[/COLOR]**

Seems like no one noticed that!
Still looks like bad ram, or another hardware issue to me. You shouldn't get errors like that. You could try removing 1 memory stick and run the test again (assuming you have 2 sticks), then try the other to find out which of both is failing. It could also be another hardware issue though, perhaps cpu overheating?

---

### Post by groundnut on 2009-08-10
I have decided to replace the computer for a new one since it seems to be a hardware problem. 
I know, that just replacing the RAM memory also would have been enough probably.

Before I started this thread, I thought it was a software issue.

---

### Post by lethalfang on 2009-08-11
This is the entry in /var/log/messages before the freeze. Any ideas what it means?
By the way, glmatrix is my screensaver GLMatrix. 

/var/log/messages
--------------------------------------------------------------------------------------------------


Aug 11 22:31:03 GOBEARS kernel: [18747.610414] Dumping ftrace buffer:
Aug 11 22:31:03 GOBEARS kernel: [18747.610416]    (ftrace buffer empty)
Aug 11 22:31:03 GOBEARS kernel: [18747.610418] CPU 1 
Aug 11 22:31:03 GOBEARS kernel: [18747.610420] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat binfmt_misc fglrx(P) ppdev bridge stp bnep input_polldev joydev lp parport arc4 ecb snd_hda_intel snd_seq_dummy snd_seq_oss snd_pcm_oss snd_mixer_oss snd_seq_midi snd_rawmidi psmouse snd_seq_midi_event iwlagn video uvcvideo snd_seq snd_seq_device iwlcore lbm_cw_mac80211 led_class snd_pcm output usb_storage compat_ioctl32 videodev v4l1_compat serio_raw pcspkr iTCO_wdt iTCO_vendor_support snd_timer snd soundcore snd_page_alloc intel_agp usbhid lbm_cw_cfg80211 r8169 mii fbcon tileblit font bitblit softcursor
Aug 11 22:31:03 GOBEARS kernel: [18747.610459] Pid: 17445, comm: glmatrix Tainted: P           2.6.28-14-generic #47-Ubuntu
Aug 11 22:31:03 GOBEARS kernel: [18747.610461] RIP: 0010:[<ffffffffa03b9584>]  [<ffffffffa03b9584>] _ZN15CMMSurface_CORE20setSurfaceAttributesEP16MSF_SURF_ATTRIBSj+0x64/0xe0 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610533] RSP: 0018:ffff8800bb563a80  EFLAGS: 00010246
Aug 11 22:31:03 GOBEARS kernel: [18747.610534] RAX: 0000000000000100 RBX: 0000000000003308 RCX: 0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610537] RDX: 0000000000000000 RSI: ffff8800bb563c38 RDI: ffffc20010ebfe20
Aug 11 22:31:03 GOBEARS kernel: [18747.610538] RBP: ffffc20010ebfe20 R08: 0000000000000001 R09: 0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610540] R10: 0000000000000000 R11: 0000000000000001 R12: ffff8800bb563c38
Aug 11 22:31:03 GOBEARS kernel: [18747.610542] R13: ffff8800bb563b48 R14: ffffc20010ababa0 R15: ffffc20010ee3aa0
Aug 11 22:31:03 GOBEARS kernel: [18747.610545] FS:  00007fc60223d7f0(0000) GS:ffff88013f803c00(0000) knlGS:0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610547] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 11 22:31:03 GOBEARS kernel: [18747.610548] CR2: 00007fc5fd7b40d8 CR3: 00000000bd526000 CR4: 00000000000006a0
Aug 11 22:31:03 GOBEARS kernel: [18747.610551] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610553] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 11 22:31:03 GOBEARS kernel: [18747.610555] Process glmatrix (pid: 17445, threadinfo ffff8800bb562000, task ffff8800b7505980)
Aug 11 22:31:03 GOBEARS kernel: [18747.610558]  ffffffffa03a7e17 0000000100000001 ffffc20010ababa0 ffffffffa043d390
Aug 11 22:31:03 GOBEARS kernel: [18747.611196]  RSP <ffff8800bb563a80>
Aug 11 22:31:03 GOBEARS kernel: [18747.611199] ---[ end trace b914a036e852a118 ]---


--------------------------------------------------------------------------------------------------


syslog:
-----------------------------------------------------------------------
Aug 11 22:31:03 GOBEARS kernel: [18747.610406] divide error: 0000 [#1] SMP 
Aug 11 22:31:03 GOBEARS kernel: [18747.610410] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/AC/online
Aug 11 22:31:03 GOBEARS kernel: [18747.610414] Dumping ftrace buffer:
Aug 11 22:31:03 GOBEARS kernel: [18747.610416]    (ftrace buffer empty)
Aug 11 22:31:03 GOBEARS kernel: [18747.610418] CPU 1 
Aug 11 22:31:03 GOBEARS kernel: [18747.610420] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat binfmt_misc fglrx(P) ppdev bridge stp bnep input_polldev joydev lp parport arc4 ecb snd_hda_intel snd_seq_dummy snd_seq_oss snd_pcm_oss snd_mixer_oss snd_seq_midi snd_rawmidi psmouse snd_seq_midi_event iwlagn video uvcvideo snd_seq snd_seq_device iwlcore lbm_cw_mac80211 led_class snd_pcm output usb_storage compat_ioctl32 videodev v4l1_compat serio_raw pcspkr iTCO_wdt iTCO_vendor_support snd_timer snd soundcore snd_page_alloc intel_agp usbhid lbm_cw_cfg80211 r8169 mii fbcon tileblit font bitblit softcursor
Aug 11 22:31:03 GOBEARS kernel: [18747.610459] Pid: 17445, comm: glmatrix Tainted: P           2.6.28-14-generic #47-Ubuntu
Aug 11 22:31:03 GOBEARS kernel: [18747.610461] RIP: 0010:[<ffffffffa03b9584>]  [<ffffffffa03b9584>] _ZN15CMMSurface_CORE20setSurfaceAttributesEP16MSF_SURF_ATTRIBSj+0x64/0xe0 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610533] RSP: 0018:ffff8800bb563a80  EFLAGS: 00010246
Aug 11 22:31:03 GOBEARS kernel: [18747.610534] RAX: 0000000000000100 RBX: 0000000000003308 RCX: 0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610537] RDX: 0000000000000000 RSI: ffff8800bb563c38 RDI: ffffc20010ebfe20
Aug 11 22:31:03 GOBEARS kernel: [18747.610538] RBP: ffffc20010ebfe20 R08: 0000000000000001 R09: 0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610540] R10: 0000000000000000 R11: 0000000000000001 R12: ffff8800bb563c38
Aug 11 22:31:03 GOBEARS kernel: [18747.610542] R13: ffff8800bb563b48 R14: ffffc20010ababa0 R15: ffffc20010ee3aa0
Aug 11 22:31:03 GOBEARS kernel: [18747.610545] FS:  00007fc60223d7f0(0000) GS:ffff88013f803c00(0000) knlGS:0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610547] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 11 22:31:03 GOBEARS kernel: [18747.610548] CR2: 00007fc5fd7b40d8 CR3: 00000000bd526000 CR4: 00000000000006a0
Aug 11 22:31:03 GOBEARS kernel: [18747.610551] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610553] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 11 22:31:03 GOBEARS kernel: [18747.610555] Process glmatrix (pid: 17445, threadinfo ffff8800bb562000, task ffff8800b7505980)
Aug 11 22:31:03 GOBEARS kernel: [18747.610557] Stack:
Aug 11 22:31:03 GOBEARS kernel: [18747.610558]  ffffffffa03a7e17 0000000100000001 ffffc20010ababa0 ffffffffa043d390
Aug 11 22:31:03 GOBEARS kernel: [18747.610562]  ffff8800bb563c38 ffffc20010ee4840 ffff8800bb563b48 ffff8800bb563c6c
Aug 11 22:31:03 GOBEARS kernel: [18747.610566]  ffffffffa03a8469 0000000000000001 ffffffffa03d06c7 0100000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610571] Call Trace:
Aug 11 22:31:03 GOBEARS kernel: [18747.610572]  [<ffffffffa03a7e17>] ? _ZN3MSF11create_surfEP9CMMClientP9CMMDriverPvRA4_K14CMM_ALLOCATIONP16MSF_SURF_ATTRIBS+0x97/0x1c0 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610628]  [<ffffffffa03a8469>] ? _ZN3MSF10alloc_surfEP9CMMClientP9CMMDriverP21MEMHEAP_ADDR_RESTRICTjP16MSF_SURF_ATTRIBSP15_CMM_RETURNCODE+0x529/0x570 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610683]  [<ffffffffa03d06c7>] ? _ZN8AsicR60025getOffsetAlignmentAndSizeEP16MSF_SURF_ATTRIBSjj+0x197/0x340 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610745]  [<ffffffffa03a352a>] ? CMMAllocSurface_WA+0x7fa/0x980 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610797]  [<ffffffff805a8c0f>] ? skb_dequeue+0x5f/0x80
Aug 11 22:31:03 GOBEARS kernel: [18747.610803]  [<ffffffffa035de42>] ? firegl_trace+0x72/0x1e0 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610843]  [<ffffffffa03b3e80>] ? _Z8uCWDDEQCmjjPvjS_+0xa80/0x10c0 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610900]  [<ffffffffa0360248>] ? firegl_cmmqs_CWDDE_32+0x348/0x410 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610940]  [<ffffffffa035ece0>] ? firegl_cmmqs_CWDDE32+0x70/0x100 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610980]  [<ffffffff803f5bbc>] ? apparmor_capable+0x1c/0x70
Aug 11 22:31:03 GOBEARS kernel: [18747.610985]  [<ffffffffa035ec70>] ? firegl_cmmqs_CWDDE32+0x0/0x100 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.611024]  [<ffffffffa033f03a>] ? firegl_ioctl+0x1ea/0x250 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.611058]  [<ffffffffa0334341>] ? ip_firegl_ioctl+0x11/0x20 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.611089]  [<ffffffff802f650d>] ? vfs_ioctl+0x7d/0xa0
Aug 11 22:31:03 GOBEARS kernel: [18747.611093]  [<ffffffff802f6875>] ? do_vfs_ioctl+0x75/0x230
Aug 11 22:31:03 GOBEARS kernel: [18747.611097]  [<ffffffff802f6ac9>] ? sys_ioctl+0x99/0xa0
Aug 11 22:31:03 GOBEARS kernel: [18747.611100]  [<ffffffff8069bf99>] ? do_device_not_available+0x9/0x10
Aug 11 22:31:03 GOBEARS kernel: [18747.611104]  [<ffffffff8021253a>] ? system_call_fastpath+0x16/0x1b
Aug 11 22:31:03 GOBEARS kernel: [18747.611108] Code: 4c 89 97 e0 00 00 00 44 8b 4e 20 44 89 8f e8 00 00 00 48 8b 56 28 48 89 97 f0 00 00 00 31 d2 8b 46 24 c1 e8 03 89 c1 48 8b 46 28 <48> f7 f1 48 89 87 d0 00 00 00 44 8b 5e 30 44 89 9f f8 00 00 00 
Aug 11 22:31:03 GOBEARS kernel: [18747.611140] RIP  [<ffffffffa03b9584>] _ZN15CMMSurface_CORE20setSurfaceAttributesEP16MSF_SURF_ATTRIBSj+0x64/0xe0 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.611196]  RSP <ffff8800bb563a80>
Aug 11 22:31:03 GOBEARS kernel: [18747.611199] ---[ end trace b914a036e852a118 ]---
-----------------------------------------------------------------------



kern.log:
-----------------------------------------------------------------------
Aug 11 22:30:56 GOBEARS kernel: [18740.558618] wlan0: beacon loss from AP ffff88013f1d6ac0 - sending probe request
Aug 11 22:31:03 GOBEARS kernel: [18747.610406] divide error: 0000 [#1] SMP 
Aug 11 22:31:03 GOBEARS kernel: [18747.610410] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/AC/online
Aug 11 22:31:03 GOBEARS kernel: [18747.610414] Dumping ftrace buffer:
Aug 11 22:31:03 GOBEARS kernel: [18747.610416]    (ftrace buffer empty)
Aug 11 22:31:03 GOBEARS kernel: [18747.610418] CPU 1 
Aug 11 22:31:03 GOBEARS kernel: [18747.610420] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat binfmt_misc fglrx(P) ppdev bridge stp bnep input_polldev joydev lp parport arc4 ecb snd_hda_intel snd_seq_dummy snd_seq_oss snd_pcm_oss snd_mixer_oss snd_seq_midi snd_rawmidi psmouse snd_seq_midi_event iwlagn video uvcvideo snd_seq snd_seq_device iwlcore lbm_cw_mac80211 led_class snd_pcm output usb_storage compat_ioctl32 videodev v4l1_compat serio_raw pcspkr iTCO_wdt iTCO_vendor_support snd_timer snd soundcore snd_page_alloc intel_agp usbhid lbm_cw_cfg80211 r8169 mii fbcon tileblit font bitblit softcursor
Aug 11 22:31:03 GOBEARS kernel: [18747.610459] Pid: 17445, comm: glmatrix Tainted: P           2.6.28-14-generic #47-Ubuntu
Aug 11 22:31:03 GOBEARS kernel: [18747.610461] RIP: 0010:[<ffffffffa03b9584>]  [<ffffffffa03b9584>] _ZN15CMMSurface_CORE20setSurfaceAttributesEP16MSF_SURF_ATTRIBSj+0x64/0xe0 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610533] RSP: 0018:ffff8800bb563a80  EFLAGS: 00010246
Aug 11 22:31:03 GOBEARS kernel: [18747.610534] RAX: 0000000000000100 RBX: 0000000000003308 RCX: 0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610537] RDX: 0000000000000000 RSI: ffff8800bb563c38 RDI: ffffc20010ebfe20
Aug 11 22:31:03 GOBEARS kernel: [18747.610538] RBP: ffffc20010ebfe20 R08: 0000000000000001 R09: 0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610540] R10: 0000000000000000 R11: 0000000000000001 R12: ffff8800bb563c38
Aug 11 22:31:03 GOBEARS kernel: [18747.610542] R13: ffff8800bb563b48 R14: ffffc20010ababa0 R15: ffffc20010ee3aa0
Aug 11 22:31:03 GOBEARS kernel: [18747.610545] FS:  00007fc60223d7f0(0000) GS:ffff88013f803c00(0000) knlGS:0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610547] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 11 22:31:03 GOBEARS kernel: [18747.610548] CR2: 00007fc5fd7b40d8 CR3: 00000000bd526000 CR4: 00000000000006a0
Aug 11 22:31:03 GOBEARS kernel: [18747.610551] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610553] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 11 22:31:03 GOBEARS kernel: [18747.610555] Process glmatrix (pid: 17445, threadinfo ffff8800bb562000, task ffff8800b7505980)
Aug 11 22:31:03 GOBEARS kernel: [18747.610557] Stack:
Aug 11 22:31:03 GOBEARS kernel: [18747.610558]  ffffffffa03a7e17 0000000100000001 ffffc20010ababa0 ffffffffa043d390
Aug 11 22:31:03 GOBEARS kernel: [18747.610562]  ffff8800bb563c38 ffffc20010ee4840 ffff8800bb563b48 ffff8800bb563c6c
Aug 11 22:31:03 GOBEARS kernel: [18747.610566]  ffffffffa03a8469 0000000000000001 ffffffffa03d06c7 0100000000000000
Aug 11 22:31:03 GOBEARS kernel: [18747.610571] Call Trace:
Aug 11 22:31:03 GOBEARS kernel: [18747.610572]  [<ffffffffa03a7e17>] ? _ZN3MSF11create_surfEP9CMMClientP9CMMDriverPvRA4_K14CMM_ALLOCATIONP16MSF_SURF_ATTRIBS+0x97/0x1c0 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610628]  [<ffffffffa03a8469>] ? _ZN3MSF10alloc_surfEP9CMMClientP9CMMDriverP21MEMHEAP_ADDR_RESTRICTjP16MSF_SURF_ATTRIBSP15_CMM_RETURNCODE+0x529/0x570 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610683]  [<ffffffffa03d06c7>] ? _ZN8AsicR60025getOffsetAlignmentAndSizeEP16MSF_SURF_ATTRIBSjj+0x197/0x340 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610745]  [<ffffffffa03a352a>] ? CMMAllocSurface_WA+0x7fa/0x980 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610797]  [<ffffffff805a8c0f>] ? skb_dequeue+0x5f/0x80
Aug 11 22:31:03 GOBEARS kernel: [18747.610803]  [<ffffffffa035de42>] ? firegl_trace+0x72/0x1e0 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610843]  [<ffffffffa03b3e80>] ? _Z8uCWDDEQCmjjPvjS_+0xa80/0x10c0 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610900]  [<ffffffffa0360248>] ? firegl_cmmqs_CWDDE_32+0x348/0x410 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610940]  [<ffffffffa035ece0>] ? firegl_cmmqs_CWDDE32+0x70/0x100 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.610980]  [<ffffffff803f5bbc>] ? apparmor_capable+0x1c/0x70
Aug 11 22:31:03 GOBEARS kernel: [18747.610985]  [<ffffffffa035ec70>] ? firegl_cmmqs_CWDDE32+0x0/0x100 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.611024]  [<ffffffffa033f03a>] ? firegl_ioctl+0x1ea/0x250 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.611058]  [<ffffffffa0334341>] ? ip_firegl_ioctl+0x11/0x20 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.611089]  [<ffffffff802f650d>] ? vfs_ioctl+0x7d/0xa0
Aug 11 22:31:03 GOBEARS kernel: [18747.611093]  [<ffffffff802f6875>] ? do_vfs_ioctl+0x75/0x230
Aug 11 22:31:03 GOBEARS kernel: [18747.611097]  [<ffffffff802f6ac9>] ? sys_ioctl+0x99/0xa0
Aug 11 22:31:03 GOBEARS kernel: [18747.611100]  [<ffffffff8069bf99>] ? do_device_not_available+0x9/0x10
Aug 11 22:31:03 GOBEARS kernel: [18747.611104]  [<ffffffff8021253a>] ? system_call_fastpath+0x16/0x1b
Aug 11 22:31:03 GOBEARS kernel: [18747.611108] Code: 4c 89 97 e0 00 00 00 44 8b 4e 20 44 89 8f e8 00 00 00 48 8b 56 28 48 89 97 f0 00 00 00 31 d2 8b 46 24 c1 e8 03 89 c1 48 8b 46 28 <48> f7 f1 48 89 87 d0 00 00 00 44 8b 5e 30 44 89 9f f8 00 00 00 
Aug 11 22:31:03 GOBEARS kernel: [18747.611140] RIP  [<ffffffffa03b9584>] _ZN15CMMSurface_CORE20setSurfaceAttributesEP16MSF_SURF_ATTRIBSj+0x64/0xe0 [fglrx]
Aug 11 22:31:03 GOBEARS kernel: [18747.611196]  RSP <ffff8800bb563a80>
Aug 11 22:31:03 GOBEARS kernel: [18747.611199] ---[ end trace b914a036e852a118 ]---

-----------------------------------------------------------------------


Both kern.log and syslog have entires after that event and before the restart (poweroff), so somehow the computer is still doing stuff, but entirely unresponsive (e.g., cap key not working, screen was black as it was probably in screensaver mode when the freeze happened).

---

