---
title: "random reboot shutdown in Karmic 9.10"
date: 2010-01-19
forum: General Help
---

### Post by charonred on 2010-01-19
I recently migrated from Hardy 8.04 LTS (32) to Karmic 9.10 (32) so that the restricted ATI drivers and CCC would work correctly - that part is basically fine.

The problem for the past couple of weeks has been Karmic randomly shutting down, and rebooting the system after 1 or 2 hours up-time. 

Why would this be happening, it was fine for the first few weeks after installing Karmic.

My system currently consists of the following;
Gigabyte MA790FX-DS5 mainboard - Jan '08
AMD 3.0Ghz Phenom II X4 945 CPU - Oct '09
4GB DDR2 Kingston HyperX RAM (1066 MHz) - Jul '09
Sapphire ATI HD5770 1GB GDDR5 video - Dec '09
Cooler Master Extreme Power Plus 640 watt power supply - Nov '09
Cooler Master Centurion 5 CAC-T05 case - Jan '08
1 pata 500 GB, 3 sata 500 GB & 1 sata 640 GB drives
2 DVD burners (Pioneer and LG)
2 x 19" (4:3) Samsung SyncMaster 943N LCD monitors

 
I used to have lmsensors working with the Athlon 2.8GHz dual core in Hardy, but they wouldn't work with the new Phenom 3.0 GHz 945 CPU in Hardy (and they still won't work in Karmic). 

Th upshot is that I don't have cpu, system, or graphics temps; nor do I have any fan speeds, so I don't know what temps or fan speeds my system is running without rebooting into BIOS (which isn't much good as I really need to know what's happening when I'm using the OS itself).

Does anyone know what could be causing this random shut-down/reboot problem?

---

### Post by charonred on 2010-01-19
bump

---

### Post by charonred on 2010-01-20
double bump

---

### Post by charonred on 2010-01-22
one more bump

---

### Post by charonred on 2010-01-27
another bump

has anyone got any idea why my system is randomly rebooting; it's only been doing it in Karmic 9.10, never did this in Hardy 8.04 using the same hardware.

---

### Post by raktarok on 2010-01-28
Hi,

Did you check the file /var/log/messages ? Open the file in a text editor, look for the time when the reboot happens, and see if there's something useful that indicates what went wrong.

Other than that, I don't have any input for this one, sorry!

---

### Post by dearingj on 2010-01-28
Odd. Have you installed all the available software updates?
I'd also recommend checking your dmesg log. Here's how:
1) Open a terminal (Applications->Accessories->Terminal)
2) Put in ```
dmesg > messages.txt
``` This will save a copy of the log to a text file in your home directory.
3) Open messages.txt in a text editor, and try searching it for things such as "shutdown", "reboot", or "error", or whatever else you can think of that might be applicable.

---

### Post by charonred on 2010-01-28
latest update was this morning at 7.00am; ran fine all morning, then at 12.02 it rebooted for no apparent reason

this is a snip from /var/log/messages 

Jan 28 07:08:41 karmic32 kernel: [ 3939.802797] type=1505 audit(1264633721.776:29): operation="profile_replace" pid=23863 name=/usr/lib/connman/scripts/dhclient-script

Jan 28 12:02:00 karmic32 kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.


did the ```
dmesg > messages.txt
```
looked for shutdown, reboot, restart ... nothing; 
only found one error 
[COLOR="Blue"][    8.947163] piix4_smbus: probe of 0000:00:14.0 failed with error -16[/COLOR] no idea what that means, but without a timestamp of 12.01 I don't know whether it would cause a reboot or not.

got me stumped ???

---

### Post by charonred on 2010-02-17
Bump again, 
this random shutdown has only been happening since I installed Karmic - there's no warning, I'm in the middle of doing something (anything), or out of the room, and the next thing the PC is rebooting ???

---

### Post by dearingj on 2010-02-18
Sorry, I'm stumped. A Google search for "piix4_smbus: probe of 0000:00:14.0 failed with error -16" did point me to some bugs on launchpad.net, but none of the bugs I saw mentioned anything about computers randomly shutting down.

---

### Post by charonred on 2010-02-18
Yeah, got me bamboozled; it runs fine for days without a problem, then out of the blue it might reboot 3 or 4 times in one day - It shouldn't be due to power spikes or similar as the PC runs through a surge protected UPS. 

The only thing that comes to mind, and I'm slightly suspicious of, is overheating; but without lmsensors working I really can't keep an eye on temps - lmsensors worked fine with this mainboard and the previous Athlon dualcore in Hardy, but ceased working once I installed the new Phenom 945 quadcore; even the fresh install of Karmic failed to get lmsensors working with this CPU. 

Despite the lack of functional lmsensors to indicate a problem, there really shouldn't be any cooling probs; the PC is in an air-conditioned room (23C/74F), the case is a CoolerMaster Centurion with mesh front and air intakes on side over CPU and graphics card. It has a 8cm intake fan at front, a 12cm exhaust fan at rear, a CoolerMaster 650w Extreme power supply with 12cm fan, and the Sapphire HD5770 1GB graphics has a huge fan and ducting as well. The PC case also has 3 removal drive bays each with an exhaust fan at rear (the 2 sata bays also have front intake fans), so all up there is plenty of air flow through the case and around the board/components in general.

I just never had this random shutdown/reboot problem with Hardy.

---

### Post by raktarok on 2010-02-19
Don't the logs in the directory /var/log/ register anything? If you have not checked the files like /var/log/kern.log, please do so. Other than that, I don't have any suggestions. I don't know what's causing this problem... 
and does it happen with all the kernels?

---

### Post by charonred on 2010-02-19
The logs don't show anything that makes any sense tome, I really don't know what I'm looking for. 

But to clarify what happens; the PC simply reboots, there is no warning, no shutdown or restart sequence - it simply powers off and then back on, just like hitting the 'reset' button or pulling the power from the wall- PC is suddenly off, and then restarting.

And it happens in all Karmic kernels so far; 2.6.31-16, 2.6.31-17, and 2.6.31-19

---

### Post by charonred on 2010-02-22
On Friday disk utilities reported one of my drives was failing (bad sectors); so I bought a new 1TB sata drive and spent the best part of the weekend copying all my accumulated data from the failing 500GB pata over to the new 1TB sata drive - it was reporting 62 bad sectors, by the end of the weekend after copying everything across it had grown to 128; drive is still under warranty till Nov '10, so it's gone back to WD.

On Monday my PC was up for 13 hours before I shut it down for the day; so I was hoping that it may have been the cause of these random shutdown/reboots. But today (Tues) my PC had been on for just over an hour, I left the room to get another cuppa, and when I came back it had rebooted ... damn !

.

---

### Post by dtmonterrey on 2010-03-23
Hi

I think I have the same problem has you, what is strange is that my computer only restarts when I'm out (screen locked). I have a Core 2 Duo 3.16GHz + 4GiB DDR2 + NVIDIA GeForce 9400 GT + 300GB Sata Disk + 2x20" LCD monitors

Can this be a problem with the screen saver? Right now I have the "Helios", but I will change to the "Cosmos".

I'll report back in a week if I don't get anymore problems, or before if my computer restarts...

---

### Post by charonred on 2010-03-23
Mine doesn't appear to be screensaver related, shut-downs happen whether I'm out of the room, or in the middle of a document

---

### Post by dtmonterrey on 2010-04-09
Well, I think my problem was related to the graphic card overeating or something, because since I change my screensaver I never had another unexpected restart

---

### Post by charonred on 2010-04-09
A friends PC has been running Karmic for a few months without a problem, then last week it started occasional random reboots (much like how mine started)

---

### Post by funfrank on 2010-04-22
me too. just started 2-3 weeks ago.

---

### Post by charonred on 2010-04-22
It's starting to sound like an oddball random Karmic problem, though there is nothing in the logs to show this as it does just simply reboot without warning.

No real problem as Lucid is out in a week, and I'll be migrating over to it - LTS versions just seem to be more stable

---

### Post by Gatewest on 2010-06-24
I have been experiencing the exact same issue on two of my servers.

One is running 9.10 and the other is running 10.04. Both are running identical hardware right down to the last bolt.

One machine (message):
Jun 24 10:55:06 internal kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 24 10:55:06 internal rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="985" x-info="http://www.rsyslog.com"] (re)start
Jun 24 10:55:06 internal rsyslogd: rsyslogd's groupid changed to 103
Jun 24 10:55:06 internal rsyslogd: rsyslogd's userid changed to 101
Jun 24 10:55:06 internal kernel: [ 0.000000] Initializing cgroup subsys cpuset
Jun 24 10:55:06 internal kernel: [ 0.000000] Initializing cgroup subsys cpu

(kern)
Jun 24 10:55:06 internal kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 24 10:55:06 internal kernel: [ 0.000000] Initializing cgroup subsys cpuset
Jun 24 10:55:06 internal kernel: [ 0.000000] Initializing cgroup subsys cpu
Jun 24 10:55:06 internal kernel: [ 0.000000] Linux version 2.6.32-21-server (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 (Ubuntu 2.6.32-21.32-serv
er 2.6.32.11+drm33.2)
Jun 24 10:55:06 internal kernel: [ 0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.32-21-server root=/dev/mapper/internal-root ro quiet
Jun 24 10:55:06 internal kernel: [ 0.000000] KERNEL supported cpus:
Jun 24 10:55:06 internal kernel: [ 0.000000] Intel GenuineIntel
Jun 24 10:55:06 internal kernel: [ 0.000000] AMD AuthenticAMD


The other (message):
Jun 24 11:01:54 130 syslogd 1.5.0#5ubuntu3: restart.
Jun 24 11:01:54 130 kernel: Inspecting /boot/System.map-2.6.28-19-server
Jun 24 11:01:54 130 kernel: Cannot find map file.
Jun 24 11:01:54 130 kernel: Loaded 49159 symbols from 22 modules.
Jun 24 11:01:54 130 kernel: [ 0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Jun 24 11:01:54 130 kernel: [ 0.000000] Initializing cgroup subsys cpuset
Jun 24 11:01:54 130 kernel: [ 0.000000] Initializing cgroup subsys cpu
Jun 24 11:01:54 130 kernel: [ 0.000000] Linux version 2.6.28-19-server (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #61-Ubuntu SMP Thu May 27 00:22:27 UTC 2010 (Ubuntu 2.6.28-19.61-server)
Jun 24 11:01:54 130 kernel: [ 0.000000] Command line: root=/dev/mapper/130-root ro quiet splash 
Jun 24 11:01:54 130 kernel: [ 0.000000] KERNEL supported cpus:

(kern):
Jun 24 11:01:54 130 kernel: Inspecting /boot/System.map-2.6.28-19-server
Jun 24 11:01:54 130 kernel: Cannot find map file.
Jun 24 11:01:54 130 kernel: Loaded 49159 symbols from 22 modules.
Jun 24 11:01:54 130 kernel: [ 0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Jun 24 11:01:54 130 kernel: [ 0.000000] Initializing cgroup subsys cpuset
Jun 24 11:01:54 130 kernel: [ 0.000000] Initializing cgroup subsys cpu

The strange thing is I had experienced the "130" machine rebooting previously but thought it was hardware. Now I have that machine AND "internal" rebooting at nearly the same instant. Both are hooked up to different UPS and circuit. The hardware is identical on both:

- OCZ Titanium XTC PC2-6400 4GB 2X2GB DDR2-800 CL4-4-4-15 DDR2 240PIN Dual Channel Memory Kit
- ASUS P5QPL-VM Epu Uatx LGA775 G41 DDR2 1PCI-E16 1PCI-E1 2PCI HDMI Video Sound GBLAN Motherboard
- Intel Core 2 Duo E6300 Dual Core Processor LGA775 2.8GHZ 1066FSB 2MB Retail Box
- Intel PRO/1000 GT Gigabit Ethernet PCI Network Adapter Card NIC
- APC BACK-UPS RS 1500VA 865W UPS 8 Outlet 340J LCD Display RJ-45 Protection (Part#: BR1500LCD)

There are definitely no heat-associated problems. The computers are in a climate-controlled vault, at 20'C (68'F). One has been in use offset by 6 months from the other, both bought at the same time, from the same batch of manufactured components. Both have identical BIOS (not sure of the version). One is accessible from the internet, one is behind redundant firewall (no chance of the second being compromised).

Any advice? This seems like a Ubuntu bug to me.

I've cross-posted to another message of similar nature:
[http://ubuntuforums.org/showthread.php?p=9507617#post9507617](http://ubuntuforums.org/showthread.php?p=9507617#post9507617)

Update:
They both rebooted at the same instant (the clock was off by a few minutes on one machine, which is why the log entries don't match time-wise, but they both rebooted at the same instant). I'm not sure what the lowmem entry is about, either.

There is literally no heat generated by the machines. They have very little load, and run at only 1.6 out of the clocked 2.8 GHz. The machines each draw a total of 17 - 20 watts of electricity each according to power measurements which indicates very little load. I'm using Antec power supplies, so nothing el cheapo there. CPU usage usually is around 7-10 %. Generally speaking these are low-load systems, so there's no problems with heat, load, etc.

Like I said earlier, they are both identical hardware, one with 9.10 and one with 10.04. The 10.04 machine is Server with the GUI installed on top. The 9.10 is Server cli only. I'm going to see tomorrow about disabling ACPI on them to see if it makes a difference. I'm thinking about setting up a third machine to see if all 3 reboot at the same time next time.

Any help you can provide would be greatly appreciated. I'm not a computer nooB, but I'm a bit new to Ubuntu and it's fickle nature, so it seems. I've used OS X as a server OS since 2000 (yes, public beta). I'm trying to migrate my company's dependence off of OS X towards Linux so that we can use generic cheap hardware.

Thanks.

Cameron
Gatewest

---

### Post by charonred on 2010-06-24
I'm running Lucid 10.04 64bit now and still having these random power reboots. I did eventually get lmsensors working - hard drive temp (3 sata, 1 pata), fan speed (cpu,front & rear case), CPU & System temp, and voltages (in0 to in6).

Everything runs fine and cool; the only thing is one of the voltages in0 sits on 0.96v and every so often spikes to 1.36v and then goes back to 0.96v, but I have no idea what in0 is, or if that is the cause of the reboot problem.

---

### Post by Thund3rstruck on 2010-09-11
Did you ever find a solution to this? I've been tearing my hair out for weeks with a Ubuntu 9.10 Ubuntu server running VMWare GSX server. I couldn't explain why my virtual machines were all being turned off instantly for no apparant reason. After hours of trouble shooting VMWare I was able to ascertain that VMWare was fine, the Linux server itself was rebooting for no apparant reason at random times. 

I'm also not seeing anything in the logs that gives me any indication as to why this machine is rebooting and random reboots are absolutely unacceptible for servers.

---

### Post by charonred on 2010-09-11
No answer yet - I'm now using 10.04 Desktop and still getting occasional random reboots. Might be hardware in my case ... don't know.

---

### Post by Gatewest on 2010-09-14
Hi,

Here is an update to my situation.

On the machine which was rebooting constantly, I swapped out the hardware with another machine (all identical hardware).  I've also switched to Debian 5.0.5 in case you're wondering.

I now get 1 reboot every 7 days.  The reboots are either at 9:38 minutes prior to midnight, or 10:22 minutes prior to midnight.  Always on either a Saturday or Sunday, depending on whether it was 9:38 or 10:22 minutes prior to midnight.   There is no software scheduled to run at these specific times.  The server is behind a firewall, and is idle during these reboot times.

It is constantly every 7 days now.  The hardware which was running this machine was removed, and had other software re-installed.  It has been running for 45 days without a single reboot.  Prior to swapping the hardware on this problematic machine, I had it running for about 30 days without any incident.

I am very convinced it is somehow software related.  The hardware is identical.  Ubuntu reboots FAR more frequently than Debian.  Debian still reboots, but far less frequently, and seemingly on a more routine schedule.

I have not tried any software fixes as suggested, I don't want to break anything on a machine which is our primary internal database server.  It would not look good.

As for the reboots, they now happen on Saturdays or Sundays, and no one is using them, so when they go offline and come back, no one notices, so I don't really care at this point.  I am sure, though, that others do care, and I wonder if maybe this is somehow kernel-related.

Just my thoughts.

Cameron

---

### Post by cyberseth on 2010-09-17
I too have 9.10 (mythbuntu though) with random reboots.  It's been going on for about 8 months now.  Early on it was really heavy (about twice a day) but as of late it seems the machine will only reboot once per 5-7 days.  I suspect its hardware related but i'm not certain.  Some events seemed to slightly increase the frequency of reboots - namely the capture card beginning a recording, or putting load on the nvidia gpu.  It also seems to happen when the machine is nearly idle.

The box reboots in like 45s, and with how i have it configured to use as a media center - not to big a deal (a little annoying if it happens while using it but no data loss per say).  What troubled me most was the lack of log events *NOTHING* was getting registered about the crash that i could see.  Just a couple days ago i stumbled into some documentation watchdog / NMI (non-maskable interrupts) and how the kernel handles oops/crashes.  I think the default behavior is to instantly reboot which might explain why i never seen an error message, but i suspect even in those cases the kernel should still write the crash out to printk's and show up in the dmesg/kern/etc. logs.

If anyone else experiencing similiar behavior wants to try out an experiment also - modify the following files to enable additional crash/logging behavior from the kernel:

$ sudo su -
# vi /etc/sysctl.conf
- or emacs or nano or whatever editor you like and add the following parameters (you can likely skip the nmi ones, but the kernel.panic i think defaults to 0 which means instant reboot):
kernel.panic = 21600
kernel.unknown_nmi_panic = 1
kernel.panic_on_unrecovered_nmi = 1
# vi /etc/sysctl.d/10-console-messages.conf
- You should find the printk message there, you can tweak the value and see if it makes a difference

With luck i'm hoping i can catch the next reboot and have a nice pretty kernel callstack and at least an estimate on what might be causing the reboots, and worse case (and sadly the more likely case) i'll probably have nothing different occur and it will still continue randomly rebooting.

---

