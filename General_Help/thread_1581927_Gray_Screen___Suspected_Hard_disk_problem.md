---
title: "Gray Screen  / Suspected Hard disk problem?"
date: 2010-09-25
forum: General Help
---

### Post by martin.devlin on 2010-09-25
Hi,
I recently bought a new desktop machine and installed Ubuntu 9.04 on it. Evertyhing was great except one day when I logged in, my desktop wouldn't show up. The error message complained about some gnome configuration files were missing or corrupted. I could use Ctrl+Alt+F1 to go to terminal and the machine was generally respsonive when using the terminal.

Eventually, I wiped the machine and installed Ubuntu 10.04. Sorry but this is why I can't quote the error messages... I should've made a note of them before wiping it... 

Now Everthing is working and 10.04 is great, but frequently several apps (firefox, transmission and audacious) will suddently stall, the application window goes gray, then after a few momements the application becomes responsive again.

I suspect that maybe the hard disk is dodgy - maybe reads and writes are just suddently slow, then it kinda fixes itself.  I don't think its a problem with ubuntu as such. When I switched off Transmission which uses the hard disk a lot, the stalling is now much less frequent whereas when Transmission was running is was happening every few minutes.

My question: How can I determine if my suspicion is correct? Which log files should I look at to see if the problem is indeed with the hard disk?

I want to confirm that the hard disk is the problem before I buy a new one so if anyone can guide me in the right direction it would be much appreciated.

thanks,
Martin

---

### Post by mrhhug on 2010-09-25
how i normally test hard drive is : run a fitness test - will have to boot into the "hard drive fitness test" software there might be a fitness test cd included in your big box o disks that they give you when u buy a new computer - if not its easy enough to google "hard drive fitness test"

memory - memtest (included on ubuntu cd)

try both of these (thorough fitness test - not just quick) and a few passes on memtest

then go from there - hdd and ram go bad all the time (you asked about hdd but i figured i would enlighten you on both)

---

### Post by mr clark25 on 2010-09-25
how much RAM do you have? sounds like it may be using swap space a lot more than it should be.

---

### Post by martin.devlin on 2010-09-25
Thanks everyone for your help.

I checked the memory using the free command:
```
$ free -mt
             total       used       free     shared    buffers     cached
Mem:          7995       1957       6038          0         36       1158
-/+ buffers/cache:        762       7233
Swap:         1906          0       1906
Total:        9901       1957       7944
```

So it looks like I have 8G memory and there is plenty free. I think I need to reboot to run the memtest from the grub menu so I haven't done that yet - will do soon.


Also, I found out how to run some tests on my harddisk using the smartctl command:

```
# install smartctl
sudo apt-get install smartmontools

# get general info
smartctl -a /dev/sda

# run the tests
sudo smartctl -t short /dev/sda
sudo smartctl -t long /dev/sda

# check the results of the tests
sudo smartctl -l selftest /dev/sda
```

The long tests take several hours to run so I'll post the results when they are done. BTW I found out about smartctl from here:
[http://www.linuxjournal.com/magazine/monitoring-hard-disks-smart?page=0,0]("http://www.linuxjournal.com/magazine/monitoring-hard-disks-smart?page=0,0")

---

### Post by martin.devlin on 2010-09-25
I just found some strange looking messages in the /var/log/kern.log file - it is attached but here is one section:

```
Sep 25 11:45:58 marty-desktop kernel: [  983.239801] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Sep 25 11:45:58 marty-desktop kernel: [  983.239810] ata1.00: irq_stat 0x40000008
Sep 25 11:45:58 marty-desktop kernel: [  983.239819] ata1.00: failed command: READ FPDMA QUEUED
Sep 25 11:45:58 marty-desktop kernel: [  983.239833] ata1.00: cmd 60/40:00:43:c6:41/00:00:25:00:00/40 tag 0 ncq 32768 in
Sep 25 11:45:58 marty-desktop kernel: [  983.239836]          res 41/40:00:65:c6:41/00:00:25:00:00/40 Emask 0x409 (media error) <F>
Sep 25 11:45:58 marty-desktop kernel: [  983.239843] ata1.00: status: { DRDY ERR }
Sep 25 11:45:58 marty-desktop kernel: [  983.239848] ata1.00: error: { UNC }
Sep 25 11:45:58 marty-desktop kernel: [  983.241217] ata1.00: configured for UDMA/133
Sep 25 11:45:58 marty-desktop kernel: [  983.241240] ata1: EH complete
Sep 25 11:46:01 marty-desktop kernel: [  985.873139] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Sep 25 11:46:01 marty-desktop kernel: [  985.873148] ata1.00: irq_stat 0x40000008
Sep 25 11:46:01 marty-desktop kernel: [  985.873156] ata1.00: failed command: READ FPDMA QUEUED
Sep 25 11:46:01 marty-desktop kernel: [  985.873170] ata1.00: cmd 60/40:00:43:c6:41/00:00:25:00:00/40 tag 0 ncq 32768 in
Sep 25 11:46:01 marty-desktop kernel: [  985.873173]          res 41/40:00:64:c6:41/00:00:25:00:00/40 Emask 0x409 (media error) <F>
Sep 25 11:46:01 marty-desktop kernel: [  985.873180] ata1.00: status: { DRDY ERR }
Sep 25 11:46:01 marty-desktop kernel: [  985.873185] ata1.00: error: { UNC }
Sep 25 11:46:01 marty-desktop kernel: [  985.874572] ata1.00: configured for UDMA/133
Sep 25 11:46:01 marty-desktop kernel: [  985.874592] ata1: EH complete
Sep 25 11:46:10 marty-desktop kernel: [  995.495455] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
Sep 25 11:46:10 marty-desktop kernel: [  995.495465] ata1.00: irq_stat 0x40000008
Sep 25 11:46:10 marty-desktop kernel: [  995.495473] ata1.00: failed command: READ FPDMA QUEUED
Sep 25 11:46:10 marty-desktop kernel: [  995.495487] ata1.00: cmd 60/20:00:93:c5:41/00:00:25:00:00/40 tag 0 ncq 16384 in
Sep 25 11:46:10 marty-desktop kernel: [  995.495491]          res 41/40:00:a3:c5:41/00:00:25:00:00/40 Emask 0x409 (media error) <F>
Sep 25 11:46:10 marty-desktop kernel: [  995.495498] ata1.00: status: { DRDY ERR }
Sep 25 11:46:10 marty-desktop kernel: [  995.495503] ata1.00: error: { UNC }
Sep 25 11:46:10 marty-desktop kernel: [  995.496829] ata1.00: configured for UDMA/133
Sep 25 11:46:10 marty-desktop kernel: [  995.496850] ata1: EH complete
Sep 25 11:46:13 marty-desktop kernel: [  998.169259] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
Sep 25 11:46:13 marty-desktop kernel: [  998.169269] ata1.00: irq_stat 0x40000008
Sep 25 11:46:13 marty-desktop kernel: [  998.169277] ata1.00: failed command: READ FPDMA QUEUED
Sep 25 11:46:13 marty-desktop kernel: [  998.169291] ata1.00: cmd 60/20:08:93:c5:41/00:00:25:00:00/40 tag 1 ncq 16384 in
Sep 25 11:46:13 marty-desktop kernel: [  998.169294]          res 41/40:00:a3:c5:41/00:00:25:00:00/40 Emask 0x409 (media error) <F>
Sep 25 11:46:13 marty-desktop kernel: [  998.169301] ata1.00: status: { DRDY ERR }
Sep 25 11:46:13 marty-desktop kernel: [  998.169306] ata1.00: error: { UNC }
Sep 25 11:46:13 marty-desktop kernel: [  998.171058] ata1.00: configured for UDMA/133
Sep 25 11:46:13 marty-desktop kernel: [  998.171078] ata1: EH complete
```

I don't understand this log file much but these error messages are associated with the disk drive - right?

---

### Post by martin.devlin on 2010-09-25
I just got the results from the smartctl test:

```
sudo smartctl -l selftest /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       80%       231         398575766
# 2  Short offline       Completed without error       00%         0         -

```

So there was read failure on the long test.  Does anyone know if this means the hard disk is permanently hosed and I should buy a new one or is there a way to repair it?

---

