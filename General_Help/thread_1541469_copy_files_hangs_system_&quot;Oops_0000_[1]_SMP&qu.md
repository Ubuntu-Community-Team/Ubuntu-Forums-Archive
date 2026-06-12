---
title: "copy files hangs system &quot;Oops 0000 [1] SMP&quot;"
date: 2010-07-29
forum: General Help
---

### Post by pumuckly on 2010-07-29
I'm using the latest Ubuntu 8.04.4 server x64 edition in my PC. I'm using a QuadCore CPU (2.4GHz) and 2GB of RAM in My PC.

I have 3 HDD:
- sda+sdb are in RAID1 and all partition are ext3 fs.
- the third sdc is single drive with ext3 fs.

While I copy files from one disk to another (I trying all cases, for example RAID1 to RAID1, sdc to sdc, sdc to RAID1, RAID1 to sdc and the results are the same) sometimes my system hangs up with message: "Oops 0000 [1] SMP" or "general protection fault: 0000 [1] SMP" when I copy large files.

I read lot of forums and some said that I must disable acpi in grub. I'm trying the acpi=off, noapic, nolapic parameters with all variants, but nothing helps.

When I copy small files the system works good. But If I copy large files (400-500MB) the system randomly hangs, and sometimes the ext3 filesystem crashes too and the disk where I copied the files go back the previous state, and the files which i copied are disappears.

May anybody can help me what can I do?

---

### Post by prodigy_ on 2010-07-29
When you copy large files, the OS probably uses more RAM. So this might be caused by a faulty memory stick.

---

### Post by pumuckly on 2010-07-29
> **prodigy_ said:**
> When you copy large files, the OS probably uses more RAM. So this might be caused by a faulty memory stick.

Thank you for your quick answer.
I think that too. I run a memory test for 24 hours yesterday, but no errors found. Unfortunately my motherboard can handle 2GB of RAM only, so I couldn't extend it.

I found two another reasons, but I not found exactly, what can I do:
- maybe the swap is not working correctly. The swap partition is working on the RAID1 array. I found that my system using 42-44 MByte swap memory (I checked that in the munin diagrams), and the system is not allocating more swap area when I copy files. Sometime I can copy 20-25GByte data from one partition to another, and sometimes a smaller 500MB data can hangs up my system. (Maybe the allocated ext3 inodes doesn't fit into the memory, while they not written phisically to the disk, or something simlilar happens.)
- the second reason, maybe the SMP is not working correctly while file copying.

I don't know how can I manage the memory allocation myself (specially for file copies), or how the SMP is working under file copying.

Sorry, I forgot to write:
The system hangs when writing data to the disk only. When I reading lot of datas from disk (such as make md5 checksums) everything works fine.

**UPDATED:**

This night I do some test.
I disabled hddtemp and smartctrl in munin, maybe this special disk access brings my system to hang up. But no! The hangs is continued without this munin plugins.

In this case I am in the following situation:
- I copied 28GB of data without any error.
- After that I'm trying to copy 80GB of data and when the copy is on the 24th GB, the system hangs. I restart computer and run some other test. Before test I delete file which is half copied.
- I check MD5 checksums for files which successfully copied, and I not found errors.
- I continue the test. I copied the 600MB files (totally 7 piece) from RAID1 array to /dev/sdc1, which not copied before the crash.
- After the copy finished I run MD5 checksum for the new files on sdc1
- I found that the 2nd copied file has different checksum!!!
- After that I copied this two file with samba to another computer where I would like to compare it.
- The first file copied correctly via samba.
- while the second file was copying I checked some files in another terminal used the command "cfv -C -fx.sfv *"
- the cfv read the files correctly I showed the results. But when the program finished with the reading it tried to write the x.sfv to the directory and this point the computer crashed (this file maybe 300 byte, so I think that no the large file size is the problem!!!)

**Update2:**
I'm trying the cfv command again without any other process or file copy. The system crashed totally when the cfv program trying to write results to the file!

The error result in dmesg:  
```

myserver kernel: [  521.231737] ------------[ cut here ]------------
myserver kernel: [  521.231889] invalid opcode: 0000 [1] SMP

```

In the last checks I run a "top" utility in another terminal, this is the results when the crashes occured:
```

top - 06:05:44 up 8 min,  3 users,  load average: 0.86, 0.45, 0.23
Tasks: 165 total,   2 running, 163 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.0%us,  0.0%sy,  0.0%ni, 83.3%id, 16.7%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2062492k total,  2045860k used,    16632k free,     9312k buffers
Swap:  3903672k total,    43344k used,  3860328k free,  1413908k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
15952 root      20   0 41104 4988 2304 R   10  0.2   0:05.39 cfv
15907 root      20   0 18992 1324  936 R    5  0.1   0:04.65 top
    1 root      20   0  4020  892  604 S    0  0.0   0:01.30 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      15  -5     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1
   17 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/2
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/3
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper
   54 root      15  -5     0    0    0 S    0  0.0   0:00.01 kblockd/0
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1
   56 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/2
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/3
   60 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid
   61 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify
  158 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod
  216 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  217 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  261 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  262 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1
  263 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/2
  264 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/3
 1582 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd
 1585 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd
 1604 root      15  -5     0    0    0 S    0  0.0   0:00.01 ata/0
 1605 root      15  -5     0    0    0 S    0  0.0   0:00.02 ata/1
 1606 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/2
 1607 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/3
 1608 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux
 2330 root      15  -5     0    0    0 S    0  0.0   0:00.03 scsi_eh_0
 2332 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
 2385 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2
 2386 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3
 2464 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4
 2465 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_5
 2766 root      15  -5     0    0    0 S    0  0.0   0:00.04 md0_raid1
 2781 root      15  -5     0    0    0 S    0  0.0   0:00.01 md1_raid1
 2787 root      15  -5     0    0    0 S    0  0.0   0:00.00 md2_raid1
 2793 root      15  -5     0    0    0 S    0  0.0   0:00.00 md3_raid1
 2799 root      15  -5     0    0    0 S    0  0.0   0:00.00 md4_raid1

```

another test error, when system crashed, but not hangs up:
```

glibc detected *** /usr/bin/python: double free or corruption (out): 0x00007f4dcada0020 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f4dca04a0ea]
/lib/libc.so.6(cfree+0x8c)[0x7f4dca04dc7c]
/usr/bin/python(PyDict_GetItemString+0x6a)[0x443d4a]
/usr/bin/python[0x4d6f9c]
/usr/bin/python[0x4d3f1a]
/usr/bin/python(PyEval_EvalFrameEx+0x5bfc)[0x488c2c]
/usr/bin/python(PyEval_EvalCodeEx+0x776)[0x48a406]
/usr/bin/python(PyEval_EvalFrameEx+0x5045)[0x488075]
/usr/bin/python(PyEval_EvalCodeEx+0x776)[0x48a406]
/usr/bin/python(PyEval_EvalFrameEx+0x5045)[0x488075]
/usr/bin/python(PyEval_EvalFrameEx+0x5bd7)[0x488c07]
/usr/bin/python(PyEval_EvalFrameEx+0x5bd7)[0x488c07]
/usr/bin/python(PyEval_EvalFrameEx+0x5bd7)[0x488c07]
/usr/bin/python(PyEval_EvalFrameEx+0x5bd7)[0x488c07]
/usr/bin/python(PyEval_EvalFrameEx+0x5bd7)[0x488c07]
/usr/bin/python(PyEval_EvalCodeEx+0x776)[0x48a406]
/usr/bin/python(PyEval_EvalFrameEx+0x5045)[0x488075]
/usr/bin/python(PyEval_EvalCodeEx+0x776)[0x48a406]
/usr/bin/python(PyEval_EvalCode+0x32)[0x48a522]
/usr/bin/python(PyRun_FileExFlags+0x10e)[0x4abe2e]
/usr/bin/python(PyRun_SimpleFileExFlags+0x1a9)[0x4ac0c9]
/usr/bin/python(Py_Main+0x8fd)[0x4145ad]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7f4dc9ff41c4]
/usr/bin/python[0x413b29]
======= Memory map: ========
00400000-00522000 r-xp 00000000 09:00 376315                             /usr/bin/python2.5
00721000-00753000 rw-p 00121000 09:00 376315                             /usr/bin/python2.5
00753000-00857000 rw-p 00753000 00:00 0                                  [heap]
7f4dc4000000-7f4dc4021000 rw-p 7f4dc4000000 00:00 0
7f4dc4021000-7f4dc8000000 ---p 7f4dc4021000 00:00 0
7f4dc85bc000-7f4dc85c9000 r-xp 00000000 09:00 81616                      /lib/libgcc_s.so.1
7f4dc85c9000-7f4dc87c9000 ---p 0000d000 09:00 81616                      /lib/libgcc_s.so.1
7f4dc87c9000-7f4dc87ca000 rw-p 0000d000 09:00 81616                      /lib/libgcc_s.so.1
7f4dc87ca000-7f4dc87ce000 r-xp 00000000 09:00 384003                     /usr/lib/python2.5/lib-dynload/zlib.so
7f4dc87ce000-7f4dc89ce000 ---p 00004000 09:00 384003                     /usr/lib/python2.5/lib-dynload/zlib.so
7f4dc89ce000-7f4dc89d0000 rw-p 00004000 09:00 384003                     /usr/lib/python2.5/lib-dynload/zlib.so
7f4dc89d0000-7f4dc89e6000 r-xp 00000000 09:00 377379                     /usr/lib/libz.so.1.2.3.3
7f4dc89e6000-7f4dc8be6000 ---p 00016000 09:00 377379                     /usr/lib/libz.so.1.2.3.3
7f4dc8be6000-7f4dc8be7000 rw-p 00016000 09:00 377379                     /usr/lib/libz.so.1.2.3.3
7f4dc8be7000-7f4dc8d42000 r-xp 00000000 09:00 375370                     /usr/lib/libcrypto.so.0.9.8
7f4dc8d42000-7f4dc8f41000 ---p 0015b000 09:00 375370                     /usr/lib/libcrypto.so.0.9.8
7f4dc8f41000-7f4dc8f64000 rw-p 0015a000 09:00 375370                     /usr/lib/libcrypto.so.0.9.8
7f4dc8f64000-7f4dc8f67000 rw-p 7f4dc8f64000 00:00 0
7f4dc8f67000-7f4dc8fab000 r-xp 00000000 09:00 375371                     /usr/lib/libssl.so.0.9.8
7f4dc8fab000-7f4dc91ab000 ---p 00044000 09:00 375371                     /usr/lib/libssl.so.0.9.8
7f4dc91ab000-7f4dc91b1000 rw-p 00044000 09:00 375371                     /usr/lib/libssl.so.0.9.8
7f4dc91b1000-7f4dc91b4000 r-xp 00000000 09:00 383963                     /usr/lib/python2.5/lib-dynload/_hashlib.so
7f4dc91b4000-7f4dc93b4000 ---p 00003000 09:00 383963                     /usr/lib/python2.5/lib-dynload/_hashlib.so
7f4dc93b4000-7f4dc93b5000 rw-p 00003000 09:00 383963                     /usr/lib/python2.5/lib-dynload/_hashlib.so
7f4dc93b5000-7f4dc93b9000 r-xp 00000000 09:00 383954                     /usr/lib/python2.5/lib-dynload/mmap.so
7f4dc93b9000-7f4dc95b9000 ---p 00004000 09:00 383954                     /usr/lib/python2.5/lib-dynload/mmap.so
7f4dc95b9000-7f4dc95ba000 rw-p 00004000 09:00 383954                     /usr/lib/python2.5/lib-dynload/mmap.so
7f4dc95ba000-7f4dc95bf000 r-xp 00000000 09:00 383990                     /usr/lib/python2.5/lib-dynload/binascii.so
7f4dc95bf000-7f4dc97be000 ---p 00005000 09:00 383990                     /usr/lib/python2.5/lib-dynload/binascii.so
7f4dc97be000-7f4dc97bf000 rw-p 00004000 09:00 383990                     /usr/lib/python2.5/lib-dynload/binascii.so
7f4dc97bf000-7f4dc97c3000 r-xp 00000000 09:00 383967                     /usr/lib/python2.5/lib-dynload/termios.so
7f4dc97c3000-7f4dc99c3000 ---p 00004000 09:00 383967                     /usr/lib/python2.5/lib-dynload/termios.so
7f4dc99c3000-7f4dc99c5000 rw-p 00004000 09:00 383967                     /usr/lib/python2.5/lib-dynload/termios.so
7f4dc99c5000-7f4dc99c8000 r-xp 00000000 09:00 383991                     /usr/lib/python2.5/lib-dynload/fcntl.so
7f4dc99c8000-7f4dc9bc7000 ---p 00003000 09:00 383991                     /usr/lib/python2.5/lib-dynload/fcntl.so
7f4dc9bc7000-7f4dc9bc9000 rw-p 00002000 09:00 383991                     /usr/lib/python2.5/lib-dynload/fcntl.so
7f4dc9bc9000-7f4dc9bcf000 r-xp 00000000 09:00 383703                     /usr/lib/python2.5/lib-dynload/_struct.so
7f4dc9bcf000-7f4dc9dcf000 ---p 00006000 09:00 383703                     /usr/lib/python2.5/lib-dynload/_struct.so
7f4dc9dcf000-7f4dc9dd1000 rw-p 00006000 09:00 383703                     /usr/lib/python2.5/lib-dynload/_struct.so
7f4dc9dd1000-7f4dc9dd5000 r-xp 00000000 09:00 384000                     /usr/lib/python2.5/lib-dynload/time.so
7f4dc9dd5000-7f4dc9fd4000 ---p 00004000 09:00 384000                     /usr/lib/python2.5/lib-dynload/time.so
7f4dc9fd4000-7f4dc9fd6000 rw-p 00003000 09:00 384000                     /usr/lib/python2.5/lib-dynload/time.so
7f4dc9fd6000-7f4dca12e000 r-xp 00000000 09:00 98658                      /lib/libc-2.7.so
7f4dca12e000-7f4dca32e000 ---p 00158000 09:00 98658                      /lib/libc-2.7.so
7f4dca32e000-7f4dca331000 r--p 00158000 09:00 98658                      /lib/libc-2.7.so
7f4dca331000-7f4dca333000 rw-p 0015b000 09:00 98658                      /lib/libc-2.7.so
7f4dca333000-7f4dca338000 rw-p 7f4dca333000 00:00 0
7f4dca338000-7f4dca3b8000 r-xp 00000000 09:00 98664                      /lib/libm-2.7.so
7f4dca3b8000-7f4dca5b7000 ---p 00080000 09:00 98664                      /lib/libm-2.7.so
7f4dca5b7000-7f4dca5b9000 rw-p 0007f000 09:00 98664                      /lib/libm-2.7.so
7f4dca5b9000-7f4dca5bb000 r-xp 00000000 09:00 98693                      /lib/libutil-2.7.so
7f4dca5bb000-7f4dca7ba000 ---p 00002000 09:00 98693                      /lib/libutil-2.7.so
7f4dca7ba000-7f4dca7bc000 rw-p 00001000 09:00 98693                      /lib/libutil-2.7.so
7f4dca7bc000-7f4dca7be000 r-xp 00000000 09:00 98661                      /lib/libdl-2.7.so
7f4dca7be000-7f4dca9be000 ---p 00002000 09:00 98661                      /lib/libdl-2.7.so
7f4dca9be000-7f4dca9c0000 rw-p 00002000 09:00 98661                      /lib/libdl-2.7.so
7f4dca9c0000-7f4dca9d6000 r-xp 00000000 09:00 98683                      /lib/libpthread-2.7.so
7f4dca9d6000-7f4dcabd6000 ---p 00016000 09:00 98683                      /lib/libpthread-2.7.so
7f4dcabd6000-7f4dcabd8000 rw-p 00016000 09:00 98683                      /lib/libpthread-2.7.so
7f4dcabd8000-7f4dcabdc000 rw-p 7f4dcabd8000 00:00 0
7f4dcabdc000-7f4dcabf9000 r-xp 00000000 09:00 98649                      /lib/ld-2.7.so
7f4dcac73000-7f4dcad26000 rw-p 7f4dcac73000 00:00 0
7f4dcad27000-7f4dcad2e000 r--s 00000000 09:00 378980                     /usr/lib/gconv/gconv-modules.cache
7f4dcad2e000-7f4dcad6d000 r--p 00000000 09:00 399865                     /usr/lib/locale/hu_HU.utf8/LC_CTYPE
7f4dcad6d000-7f4dcadf2000 rw-p 7f4dcad6d000 00:00 0
7f4dcadf4000-7f4dcadf9000 rw-p 7f4dcadf4000 00:00 0
7f4dcadf9000-7f4dcadfb000 rw-p 0001d000 09:00 98649                      /lib/ld-2.7.so
7fff7a9da000-7fff7a9ef000 rw-p 7ffffffea000 00:00 0                      [stack]
7fff7a9fe000-7fff7aa00000 r-xp 7fff7a9fe000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

```



The OS is:
Linux myserver 2.6.24-28-server #1 SMP Fri Jun 18 14:47:02 UTC 2010 x86_64 GNU/Linux

The CPU from dmesg:
Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b

The lspci output if it needed:
```

00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. Unknown device 7372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)
02:00.0 Multimedia controller: Philips Semiconductors Unknown device 7164 (rev 81)
03:04.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
03:06.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

```

Unfortunately In the syslog or dmesg I nothing to found.

---

### Post by pumuckly on 2010-08-02
I think I found something.

I installed the hddtemp utility some months ago because I would like to watch the HDD temperatures in munin.

While the hddtemp utility was working some bytes changed in copied files. (I found this error when I checked files with MD5 checksum).
I was found this situation with PATA hard disk in a Windows XP system some years ago, but I didn't think so that this situation is appears in Linux with SATA disk too.

The problem was on the PATA disk that the temperature datas came with file datas on databus. When the system read SMART values under copying (for example temperatures) the SMART datas mixed with the file contents. Just some bytes changed, and unfortunately the Windows XP not detected it.

I think the Linux detected some checksum error while the files copyied and maybe the OS tried to correct it and this cause the system hangs.

When I turn off the hddtemp (and smartctl) in munin, I can copy large files without any byte changes. And I can copy more than 20GB data without hangs. (I will do some test to sure that the files really don't change.)

Unfortunatyle sometimes still hangs up my system too. (but rarely than while the hddtemp was running.)

I check [_my motherboard_]("http://www.asrock.com/mb/overview.asp?Model=4COREDUAL-SATA2") BIOS and found an "Intel(R) Virtualization tech." options, something VMM (Virtual Machine Architecture). I disabled this option and I found that the system hangs more rarely. But sometimes still hangs the system when I copied files.

I will do some tests in the next days and I will write my results.

---

