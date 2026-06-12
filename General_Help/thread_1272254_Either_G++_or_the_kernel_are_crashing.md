---
title: "Either G++ or the kernel are crashing"
date: 2009-09-21
forum: General Help
---

### Post by xen2001b on 2009-09-21
Hi

In a series of firsts, I bought the individual components to and assembled my first desktop, and I've made my first ubuntu installation.  This is my first post on the Ubuntu forums, too.

So: After getting all the wires connected and the OS installed, I tried to build the program I work with using scons and g++, but I can't make it through an entire build.  My system starts crashing on me (either a boring hanging, or a hanging with the kernel-panic flashing of the caps-lock and scroll-lock lights) not very long after the build crashes.

I've not found anything online that sounded very similar, which has me suspecting that I've got a hardware problem -- after all, my machine was built by a newb.  BUT I also have a lot of worrisome messages in my /var/log/syslog

Here's a small sample of the contents of that log:

<start log>

Sep 21 17:49:49 ice9 kernel: [  292.648833] general protection fault: 0000 [#1] SMP 
Sep 21 17:49:49 ice9 kernel: [  292.648838] last sysfs file: /sys/devices/virtual/net/pan0/statistics/collisions
Sep 21 17:49:49 ice9 kernel: [  292.648840] Dumping ftrace buffer:
Sep 21 17:49:49 ice9 kernel: [  292.648843]    (ftrace buffer empty)
Sep 21 17:49:49 ice9 kernel: [  292.648845] CPU 0 
Sep 21 17:49:49 ice9 kernel: [  292.648846] Modules linked in: binfmt_misc ppdev bridge stp bnep input_polldev video output ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_state ipt_addrtype ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables coretemp i2c_i801 lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device iTCO_wdt iTCO_vendor_support snd soundcore snd_page_alloc nvidia(P) psmouse serio_raw pcspkr ohci1394 ieee1394 r8169 mii floppy fbcon tileblit font bitblit softcursor
Sep 21 17:49:49 ice9 kernel: [  292.648885] Pid: 4727, comm: cc1plus Tainted: P           2.6.28-15-generic #49-Ubuntu
Sep 21 17:49:49 ice9 kernel: [  292.648887] RIP: 0010:[<ffffffff8022f559>]  [<ffffffff8022f559>] __ticket_spin_lock+0x9/0x20
Sep 21 17:49:49 ice9 kernel: [  292.648894] RSP: 0018:ffff8801994edbd8  EFLAGS: 00010082
Sep 21 17:49:49 ice9 kernel: [  292.648895] RAX: 0000000000000100 RBX: cccccccccccccccc RCX: 0000000000000420
Sep 21 17:49:49 ice9 kernel: [  292.648897] RDX: 000000000010a79a RSI: 0000000000000282 RDI: cccccccccccccccc
Sep 21 17:49:49 ice9 kernel: [  292.648899] RBP: ffff8801994edbd8 R08: 00000000ffffffd2 R09: ffff8801994ede28
Sep 21 17:49:49 ice9 kernel: [  292.648901] R10: 0000000000000002 R11: 0000000000000000 R12: 0000000000000282
Sep 21 17:49:49 ice9 kernel: [  292.648903] R13: 0000000000000000 R14: cccccccccccccccc R15: ffffffff80a01100
Sep 21 17:49:49 ice9 kernel: [  292.648905] FS:  0000000000000000(0000) GS:ffffffff80a9a000(0000) knlGS:0000000000000000
Sep 21 17:49:49 ice9 kernel: [  292.648907] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Sep 21 17:49:49 ice9 kernel: [  292.648909] CR2: 00007f2249870090 CR3: 0000000000201000 CR4: 00000000000006a0
Sep 21 17:49:49 ice9 kernel: [  292.648910] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Sep 21 17:49:49 ice9 kernel: [  292.648913] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Sep 21 17:49:49 ice9 kernel: [  292.648915] Process cc1plus (pid: 4727, threadinfo ffff8801994ec000, task ffff88011751c320)

<end log>

If I build with -j8, then all 8 processors will compile full throttle (100% utilization) for a minute or two, then the system will hiccup, and then utilization will fluctuate wildly.  Some cores end up at 0% utilization, others fluctuate between 10 and 50.  This always ends with the system hanging -- sometimes with the keyboard flashing.

After considerable effort, I've been able to rule out the possibility that my heat sink is faulty and that my CPU is getting too hot.  g++ will start flaking out on me when my processor is at 70 C.  I can run the mprime stress test from beginning to end and see the temperature hold stead at 82 C -- but that doesn't cause the instability that 2 minutes worth of compilation gives my computer.

What do I have?

I have an i7 920 on a Gigabyte GA-EX58-UD3R motherboard.  I have 6 GB RAM in 3 2GB sticks.  I have an EVGA 9500 GT GeForce -- my bug happens whether or not I've loaded the NVidia driver for the card.  I have a hard drive and a dvd burner.  I'm running the 64-bit version of Ubuntu 9.4.  I verified that the MD5 checksum for the Ubuntu .iso file matches the checksum posted online.

I don't know exactly what information I should post here.  If you'd like me to clarify anything, I'd be happy to.

Thanks in advance for any help you can offer.

PS:
 I have a screen shot of the system after g++ starts to flake out, and I have a screen shot while running mprime.

PPS:
I did try updating the kernel, but the nvidia drivers failed to install and then when I rebooted, I could no longer see most of the screen -- I was zoomed in to the very center -- and couldn't do anything, so I just started over from scratch.  I don't know what website whose instruction's I followed (otherwise I would post a link) since my firefox history was lost after I wiped my system to start again.

---

### Post by parul1234 on 2009-09-21
It could be the problem with general protection fault . Contact your system administrator he should be able to help you

---

### Post by xen2001b on 2009-09-23
It's not the hardware.

Last night, I downgraded the OS to Ubuntu 8.10 and now I can compile just fine.  9.4 was unusable.  My main purpose for the machine is to compile, so if I have to install an older OS to get g++ working, then that's what I'll do.

---

### Post by xen2001b on 2009-10-09
My problem has persisted with Ubuntu 8.10.

The computer will freeze most often when I'm using the integrated network card on my Gigabyte GA-EX58-UD3R motherboard.    It will freeze if I'm using firefox or if I'm using ssh or scp.  I can crash my computer within 5 minutes of turning it on if I go to [http://thechive.com](http://thechive.com) though I can also crash my computer if I'm only running ssh.  When I was running 9.4, I could crash my computer when running g++ alone.

I took my machine into a local computer store and they found nothing.  They booted the machine from a Windows hard drive and stress-tested it for 23 hours without finding anything wrong.  The memory passed 17 iterations of their memcheck benchmark.  My (linux) hard drive passed the manufacturer-provided benchmark.  Under Windows, my machine is a piece of gold.  This kills me.

Since getting my machine back, I downloaded the Fedora-11 Live CD and have successfully frozen it while navigating thechive.  The second time it froze on the chive -- firefox was frozen, but my mouse still responded -- a small window popped up in the lower right corner telling me I had a kernel error (an oops) and asked me to report the error.  I clicked "Yes", but nothing else happened.  Firefox never recovered.  I was unable to log-off from the live CD.  Within a minute, my mouse stopped responding.  The third time it froze, I was writing the first version of this post in Firefox; I made the mistake of trying to open a new tab and the system hung.

I have no idea what's wrong.  I would totally appreciate any suggestions.

Could the absence of drivers be my problem?  Is there something about linux kernel that's incompatible with the i7 or x58 chipset?  Does a newer kernel fix the problem?  Should I just install Windows?

Here is a better description of my system configuration than in my first post.

i7 920 processor.  I'm not overclocking.

Gigabyte GA-EX58-UD3R motherboard

6GB OCZ DDR3 PC3-10666 Memory

EVGA 512MB DDR2 GeForce 9500GT PCI-Express 2.0 graphics card (I have tried using the card with and without the nvidia-provided drivers, and the system freezes either way)

Sony AD-7240S-OB% DVD burner

500GB Seagate ST3500418AS hard drive

500W FSP ATX power supply

Antec 300 case.

---

### Post by xen2001b on 2009-10-09
I would love some suggestions.  Anyone? Anyone?

---

### Post by jamb on 2009-11-19
Hi there,
sorry to here about all issues. I scanned the forums, as usual for potential compatibility issues. I just purchased an identical board and will report my build story shortly.

---

