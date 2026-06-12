---
title: "oprofile: No sample file found"
date: 2011-09-15
forum: General Help
---

### Post by sliter on 2011-09-15
I run oprofile in my openwrt with kernel version 2.6.33.5, and always get this information "oprofile: No sample file found"

**My command:**
root@OpenWrt:/# opcontrol --init
oprofile: using arm/armv6
root@OpenWrt:/# opcontrol --no-vmlinux
root@OpenWrt:/# opcontrol --start     
test: 0: unknown operand
Using default event: CPU_CYCLES:100000:0:1:1
Using 2.6+ OProfile kernel interface.
Using log file /var/lib/oprofile/samples/oprofiled.log
Daemon started.
Profiler running.
root@OpenWrt:/# opcontrol --dump
root@OpenWrt:/# opreport -l
opreport error: No sample file found: try running opcontrol --dump
or specify a session containing sample files


**Result of "opcontrol --status":**
root@OpenWrt:/# opcontrol --status
Daemon running: pid 8380
Separate options: none
vmlinux file: none
Image filter: none
Call-graph depth: 0
CPU buffer size: 


**Result of "cat /dev/oprofile/cpu_buffer_size" **
8192

**My oprofiled.log:**
oprofiled started Thu Jan  1 00:04:02 1970
kernel pointer size: 4

Thu Jan  1 00:11:14 1970

Nr. sample dumps: 4
Nr. non-backtrace samples: 0
Nr. kernel samples: 0
Nr. lost samples (no kernel/user): 0
Nr. lost kernel samples: 0
Nr. incomplete code structs: 0
Nr. samples lost due to sample file open failure: 0
Nr. samples lost due to no permanent mapping: 0
Nr. event lost due to buffer overflow: 0
Nr. samples lost due to no mapping: 0
Nr. backtraces skipped due to no file mapping: 0
Nr. samples lost due to no mm: 0
Nr. samples lost cpu buffer overflow: 2747916
Nr. samples received: 2747916
Nr. backtrace aborted: 0
Nr. samples lost invalid pc: 0
oprofiled stopped Thu Jan  1 00:11:14 1970



After I start the profile, I transmit a 80M file from a CIFS client to the openwrt which has a Samba server. And then I tried the dump and has no sample results.
Help please~~~:confused:

---

