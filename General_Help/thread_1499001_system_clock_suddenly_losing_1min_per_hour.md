---
title: "system clock suddenly losing 1min per hour"
date: 2010-06-01
forum: General Help
---

### Post by eval- on 2010-06-01
Today I updated a bunch of packages, rebooted.  I run lucid 10.04 x86_64, originally Xubuntu but now gnome since I cannot make xfce4-panel tasklist behave with compiz.  Anyway, by the end of the day my clock was 10min off.  If I use ntpdate at about 10min intervals I see things like:

$ sudo ntpdate time.xxx.xxx.de
 1 Jun 18:37:02 ntpdate[9734]: step time server xxx.xxx.xxx.xxx offset 10.043055 sec

I have deleted /etc/adjtime and touch'd a blank file to no avail.

Is this problem serious?  Is it likely software or hardware?  Is running an ntp daemon the right solution or would it be masking a new software or hardware problem that appeared today?

---

### Post by drpjkurian on 2010-06-01
hi 
I remember having the same problem whem I was having desktop. It was attributed to weak battery fixed inside CPU (Mother board may be) So please consider this option too when everything else fails.

---

### Post by JustinR on 2010-06-01
Check your CMOS battery, it keeps system time and if it is dying time will slowly progress down.

---

### Post by eval- on 2010-06-01
> **JustinR said:**
> Check your CMOS battery, it keeps system time and if it is dying time will slowly progress down.

OK it is a brand new Quad-Core i7, but I should not rule out the possibility of a battery failure.  What I will do is check both "date" and "hwclock" tomorrow morning to see if the hardware clock is keeping pace although the system suddenly started drifting.

Do you know whether ntpdate sets the RTC/hardware clock or just the system (does any software at all set the HW clock or just in BIOS?)

Is the system clock synchronized to the HW clock only on boot?

---

### Post by jobix on 2010-06-01
ntpdate sets the system clock. To set the hardware clock, you'll need to use the hwclock command. Whether the system clock is synchronized to hardware clock on boot up or boot down depends on the scripts which are executed. Typically, they are in the /etc/rcX.d folders but with the new upstart stuff, this might have changed.

Typically adjustment takes about half an hour for each second drifted. But if you have ntpd running, it will keep sync'ing regularly and your system won't drift so much. ntpd is definitely recommended.

---

### Post by eval- on 2010-06-02
So the system clock is definitely to blame, and this never happened to me before the latest apt-get update (... or at least, I never noticed it??  See end)

$ date
Wed Jun  2 10:55:44 CEST 2010
$ sudo hwclock
Wed 02 Jun 2010 11:06:05 AM CEST  -0.635305 seconds

My hardware clock is not losing seconds.  I run:

2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

with a quad-core hyperthreaded (so 8 virtual CPUs):
 Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz

Is there anything I should do to help the developers debug this?  In my /var/log/messages I see something suspicious:

Jun  1 11:49:30 i860isbr-328 kernel: [    1.773132] WARNING: at /build/buildd/linux-2.6.32/arch/x86/kernel/hpet.c:392 hpet_next_event+0x7a/0x90()
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773134] Hardware name: System Product Name
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773135] Modules linked in:
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773137] Pid: 0, comm: swapper Not tainted 2.6.32-22-generic #33-Ubuntu
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773138] Call Trace:
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773143]  [<ffffffff81066d0b>] warn_slowpath_common+0x7b/0xc0
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773146]  [<ffffffff81066d64>] warn_slowpath_null+0x14/0x20
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773148]  [<ffffffff810375ca>] hpet_next_event+0x7a/0x90
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773150]  [<ffffffff81037610>] hpet_legacy_next_event+0x10/0x20
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773154]  [<ffffffff81092e24>] clockevents_program_event+0x54/0xa0
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773156]  [<ffffffff81094378>] tick_dev_program_event+0x68/0xd0
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773159]  [<ffffffff81093cae>] tick_broadcast_oneshot_control+0x11e/0x120
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773161]  [<ffffffff810934c0>] tick_notify+0x130/0x200
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773165]  [<ffffffff81543b16>] notifier_call_chain+0x56/0x80
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773168]  [<ffffffff8108a366>] raw_notifier_call_chain+0x16/0x20
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773170]  [<ffffffff81092c47>] clockevents_notify+0x37/0x160
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773173]  [<ffffffff8130ccc5>] lapic_timer_state_broadcast+0x46/0x48
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773175]  [<ffffffff8130d234>] acpi_idle_enter_bm+0x187/0x2be
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773178]  [<ffffffff81543ad6>] ? notifier_call_chain+0x16/0x80
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773181]  [<ffffffff81437507>] cpuidle_idle_call+0xa7/0x140
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773185]  [<ffffffff81011e73>] cpu_idle+0xb3/0x110
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773187]  [<ffffffff8153ad4b>] start_secondary+0xa8/0xaa
Jun  1 11:49:30 i860isbr-328 kernel: [    1.773191] ---[ end trace eac882e79f716dcf ]---
Jun  1 11:49:30 i860isbr-328 kernel: [    1.775535] registered taskstats version 1
Jun  1 11:49:30 i860isbr-328 kernel: [    1.776124]   Magic number: 14:27:832
Jun  1 11:49:30 i860isbr-328 kernel: [    1.776435] rtc_cmos 00:03: setting system clock to 2010-06-01 11:48:53 UTC (1275392933)

It also seems this error has been happening before:

$ zgrep warn_slowpath /var/log/messages* | awk '{print $1 " " $2}' | sed -e 's/mess.*://g' | uniq

Jun 1
May 17
May 20
May 21
May 9
May 10
May 3
May 4
May 6
May 7
May 8

... and yet I never lost time until recently?  Could the CPU governor matter, whether I am in 'Performance' or 'Ondemand?'

Could the xfce4 time applet use hardware, not system clock?  (I recently switched to gnome because I could not make the xfce4-panel tasklist behave with compiz)  I just don't understand why I'm suddenly seeing this problem now... and I don't know how to isolate the cause to help the Ubuntu developers...

Sure, I will run ntpd until this is fixed.  But there's a new bug here somewhere, that someone should look into...

---

### Post by eval- on 2010-06-03
> **eval- said:**
> 
Sure, I will run ntpd until this is fixed.  But there's a new bug here somewhere, that someone should look into...

OK, the hpet.c bug on boot has been reported several times (on i7s) and AFAIK it has not been resolved in any recent kernel.

[http://dunedin.lug.net.nz/forums/showthread.php?t=451783](http://dunedin.lug.net.nz/forums/showthread.php?t=451783)
[https://lists.linux-foundation.org/pipermail/bugme-new/2010-February/024289.html](https://lists.linux-foundation.org/pipermail/bugme-new/2010-February/024289.html)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549841](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549841)

HOWEVER, no one seems to be describing a concurrent loss in kernel timekeeping... with system clock falling behind hardware clock...

I wonder if these are related or a coincidence?

---

