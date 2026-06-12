---
title: "Ubuntu 10 is REALLY slow for me?"
date: 2010-05-04
forum: General Help
---

### Post by alunparry on 2010-05-04
Hi

Can anyone help.

I've just upgraded from Ubuntu 9.04 to Ubuntu 10.04

It's mega slow initially after it has booted.

Before the GRUB message I get a few I/O error messages that are too quick for me to read.

Then I log in with my password.

And then the lead time from click to action is absolutely ages once it's all up and running.

It takes a good 10 to 12 minutes for click to action time to settle down to normality.

Is there any reason for this that anyone knows. Please be gentle, I'm not really very techie with these things.

But thanks for your help,

Al

---

### Post by clhsharky on 2010-05-04
HI alunparry

How did you upgrade from 9.04 to 10.04?

Sharky

---

### Post by alunparry on 2010-05-04
hi sharky

thanks for the reply.

i used the update manager in the System / Administration menu.

thanks for your help

al

---

### Post by RevJSorrells on 2010-05-20
I downloaded and did a fresh install of Ubuntu 10 and it is really slow. Not to bad when playing around but especially when downloading.

---

### Post by Drybones5 on 2010-05-20
It might be the new ext4 filesystem.  I think ext4 isn't ready just yet.

---

### Post by soltanis on 2010-05-20
If he is using ext4, he would've been using it since the last install; upgrading via the package manager wouldn't have changed the filesystem. ext4 is also quite mature and has respectable performance, so I don't think that's it.

This sounds like some kind of other problem, possibly either a hardware misconfiguration, or less likely but still plausible, there is a pending hardware failure that coincided approximately with the distribution upgrade.

Can you please open up a terminal and post the output of the following commands typed exactly?

```

cat /proc/cpuinfo
lspci
dmesg | tail

```

That will give us information about your system hardware.

Also, if it's possible for you to read those error messages and tell us approximately what they are, that will also be very helpful in narrowing down the search.

---

### Post by lemort on 2010-05-26
I'm having the exact same problem... after upgrading from 9.04 to 10.04 through Update Manager. Its depressing me. I print what I got:

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 35
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping    : 2
cpu MHz        : 2200.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips    : 4422.70
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 35
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping    : 2
cpu MHz        : 2200.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips    : 4422.95
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp


00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)


[37472.911634] sd 8:0:0:0: Attached scsi generic sg2 type 0
[37473.092521] sd 8:0:0:0: [sdb] 15954944 512-byte logical blocks: (8.16 GB/7.60 GiB)
[37473.094111] sd 8:0:0:0: [sdb] Write Protect is off
[37473.094117] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[37473.094120] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[37473.098109] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[37473.098118]  sdb: sdb1
[37473.103104] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[37473.103113] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[42326.197466] usb 1-6: USB disconnect, address 6

---

### Post by lemort on 2010-05-27
Okay I got my problem solved:

Open:
$ ksudo gedit /etc/default/grub

Add line to the file:
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

Then run:
$ sudo update-grub

Reboot


Hope this helps you too
~lemort

---

