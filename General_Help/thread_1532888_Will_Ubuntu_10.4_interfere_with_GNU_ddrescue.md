---
title: "Will Ubuntu 10.4 interfere with GNU ddrescue?"
date: 2010-07-17
forum: General Help
---

### Post by cccmikey on 2010-07-17
G'day :)

[I]The TL;DR: Does Ubuntu try to access non-mounted drives in the background?
[/I] 
I have a sick hard drive to clone to a new one. 

The sick drive, when in it's own laptop won't allow Ubuntu live CD to boot. (Ubuntu hags during loading with the HDD repeatedly rattling.)

So, I have it attached to a USB to IDE cable on a system running 10.4

I have turned off auto-mounting so Ubuntu hopefully won't keep trying to see what's on this drive.

However, even when idle, I get messages in syslog like this:
```
Jul 17 18:17:48 ubuntu kernel: [ 1114.112047] usb 1-5: reset high speed USB device using ehci_hcd and address 4
Jul 17 18:18:20 ubuntu kernel: [ 1146.112030] usb 1-5: reset high speed USB device using ehci_hcd and address 4
Jul 17 18:18:51 ubuntu kernel: [ 1177.112675] usb 1-5: reset high speed USB device using ehci_hcd and address 4
```Does this mean Ubuntu is trying to constantly query the drive? (A bit like Windows does with System Restore, etc.)  If so, will it prevent ddrescue from working efficiently?

```
michael@ubuntu:~$ sudo ddrescue -d -v -r-1 /dev/sdc /dev/sdb logfile.log 
[sudo] password for michael: 


About to copy 60011 MBytes from /dev/sdc to /dev/sdb
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512  bytes
Direct: yes    Sparse: no    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:     2097 kB,  errsize:       0 B,  current rate:    10922 B/s
   ipos:     2097 kB,   errors:       0,    average rate:     2819 B/s
   opos:     2097 kB,     time from last successful read:       0 s
Copying non-tried blocks...

```SpinRite can read the first partition without incident (4GB) but then dies on the next data partition, so it seems a little strange that ddrescue can't seem to really get started.

---

