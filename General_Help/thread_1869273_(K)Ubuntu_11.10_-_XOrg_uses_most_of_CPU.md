---
title: "(K)Ubuntu 11.10 - XOrg uses most of CPU"
date: 2011-10-25
forum: General Help
---

### Post by denisk on 2011-10-25
This is really a problem for me with Oneiric...
I installed Ubuntu 11.10 on my new machine at work a couple of days ago. What I noticed that after a while XOrg process would start to eat 50-60% of CPU cycles, thus, making the system significantly slower. This wouldn't happen immediately - maybe in a few minutes after system starts, maybe in an hour - but this would happen anyway. I tried to work with Gnome Classic desktop - the same thing. After a while, I uninstalled Ubuntu 11.10 and installed Kubuntu 11.10. Surprisingly enough, the situation appeared to be the same - after a while the windows would become hardly-draggable and browser would become hardly-scrollable, which would wean that XOrg took the most of the CPU.
I noticed that there are many similar threads  (
[http://ubuntuforums.org/showthread.php?t=1861454,]("http://ubuntuforums.org/showthread.php?t=1861454")
[http://ubuntuforums.org/showthread.php?t=1856618, ]("http://ubuntuforums.org/showthread.php?t=1856618")
[http://askubuntu.com/questions/69120/100-cpu-usage-with-on-demand-setting-due-to-xorg)]("http://askubuntu.com/questions/69120/100-cpu-usage-with-on-demand-setting-due-to-xorg"), 
and there are actually bugs with Sandy Bridge processors in Kernel (I have intel core I7 2600k):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/834037](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/834037)

What I want to know is the following: How do I traverse what causes XOrg to eat so much of CPU? It is just a server, which responses to client's requests, so I would like to know what process (if any) disturbs it so hardly. Are there any logs of XOrg which can be investigated? If there's a bug in XOrg, I would like to submit it with all necessary proves. If there is some program causing the problem, I would like to get rid of the program.
I have same hardware configuration at home, except videocard (at work, where the problem occurs, I have GeForce 550 GTX, while at home I have GeForce 450 GTS), and I have Kubuntu 11.10 there (upgraded from 11.04), and there is no problem at home. I assume the issue is related to the videocard, but I can't prove it without help.
Any suggestions will be highly appreciated.

---

### Post by dtwomley on 2011-10-26
Remove google-desktop

---

### Post by denisk on 2011-10-27
> **dtwomley said:**
> Remove google-desktop
I don't have one...

---

### Post by aneeszaki on 2011-10-27
I have the same problem..Xorg eats much cpu (30-40%) and caused the cpu fan to work harder.

The happened after I update the system(apt-get update&&apt-get upgrade)..any help?

Kubuntu 11.10 Hp Probook 4520s core i5 Intel.

thx.

---

### Post by abedayyad on 2011-10-28
I had an incredibly similar problem with an older version of Ubuntu, and I found the solution by changing the default workspace from netbook to desktop. I gather, though, that there is only one workspace with these later versions of Ubuntu? This is one more reason why I am going to continue being stubborn with Meerkat.

---

### Post by denisk on 2011-10-28
Update: Every time the XOrg starts to eat compute cycles aggressively, the following messages appears in the kernel log:
```
10/27/11 05:09:35 PM irq 16 nobody cared (try booting with the "irqpoll" option)
10/27/11 05:09:35 PM Pid 0, comm: swapper Tainted: P C 3.0.0-12-generic #20-Ubuntu
10/27/11 05:09:35 PM Call Trace 
10/27/11 05:09:35 PM <IRQ> [<ffffffff810cf8ad>] __report_bad_irq+0x3d/0xe0
10/27/11 05:09:35 PM [<ffffffff810cfcd5>] note_interrupt+0x135/0x180
10/27/11 05:09:35 PM [<ffffffff810cdcc9>] handle_irq_event_percpu+0xa9/0x220
10/27/11 05:09:35 PM [<ffffffff810cde8e>] handle_irq_event+0x4e/0x80
10/27/11 05:09:35 PM [<ffffffff810d0604>] handle_fasteoi_irq+0x64/0xf0
10/27/11 05:09:35 PM [<ffffffff8100c252>] handle_irq+0x22/0x40
10/27/11 05:09:35 PM [<ffffffff815f3d2a>] do_IRQ+0x5a/0xe0
10/27/11 05:09:35 PM [<ffffffff815ea413>] common_interrupt+0x13/0x13
10/27/11 05:09:35 PM <EOI> [<ffffffff814aad81>] ? poll_idle+0x41/0x80
10/27/11 05:09:35 PM [<ffffffff814aad53>] ? poll_idle+0x13/0x80
10/27/11 05:09:35 PM [<ffffffff814ab062>] cpuidle_idle_call+0xa2/0x1d0
10/27/11 05:09:35 PM [<ffffffff8100920b>] cpu_idle+0xab/0x100
10/27/11 05:09:35 PM [<ffffffff815b803e>] rest_init+0x72/0x74
10/27/11 05:09:35 PM [<ffffffff81ad0c2b>] start_kernel+0x3d4/0x3df
10/27/11 05:09:35 PM [<ffffffff81ad0388>] x86_64_start_reservations+0x132/0x136
10/27/11 05:09:35 PM [<ffffffff81ad0140>] ? early_idt_handlers+0x140/0x140
10/27/11 05:09:35 PM [<ffffffff81ad0459>] x86_64_start_kernel+0xcd/0xdc
10/27/11 05:09:35 PM handlers 
10/27/11 05:09:35 PM [<ffffffffa008c2a0>] rtl8169_interrupt
10/27/11 05:09:35 PM [<ffffffffa08a1380>] nv_kern_isr
10/27/11 05:09:35 PM Disabling IRQ #16

```

Can can anyone with similar symptoms verify it by checking the log immediately after issue occurs?
```
 cat /var/log/kern.log
```

Can anyone interpret the message? Can it be a chance of hardware corruption (bad memory etc)?.

---

### Post by aneeszaki on 2011-10-29
update: Now the cpu usage spikes high just when i move the cursor!!!....If i move the cursor faster the cpu usage increases!!

weird...any idea?

---

### Post by oldtimer7777 on 2011-10-29
> **aneeszaki said:**
> update: Now the cpu usage spikes high just when i move the cursor!!!....If i move the cursor faster the cpu usage increases!!

weird...any idea?

Rollback to a version of Kubuntu that doesn't do this for now..  That what I would suggest.

Kubuntu has always been a notorious resource hog too.

---

### Post by denisk on 2011-11-20
I have solved the problem by examining interrupts a bit.
Basically, the message below, 'irq 16 nobody cared', means that some events happen on interruptions interface 16 that were not handled by anybody. I found this link useful when learning what IRQ is:
[http://www.mjmwired.net/kernel/Documentation/IRQ.txt](http://www.mjmwired.net/kernel/Documentation/IRQ.txt)
So, I needed to figure out what hardware deals with IRQ 16 to start with. Found that using
```

cat /proc/interrupts

```...which gave me something like
```

  0:         95          0          0          0          0          0          0          0   IO-APIC-edge      timer
  1:         10          0          0          0          0          0          0          0   IO-APIC-edge      i8042
  8:          1          0          0          0          0          0          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   acpi
 16:      10426    1083058          0          0          0          0          0          0   IO-APIC-fasteoi   eth1, nvidia
 17:        183          0        126          0          0          0          0          0   IO-APIC-fasteoi   hda_intel
...
41:      61762          0          0          0          0          0          0          0   PCI-MSI-edge      eth0

```I have 2 network interfaces, eth0 and eth1, and have used eth1 all the time. It happened that eth1 resided on one IRQ with nvidia. Googling 'irq  nobody cared' gave tons of useful solutions, such as starting kernel with various options like
```

acpi=routeirq
noirqdebug
irqpoll 
irqfixup
pci=msi

```and more. I decided to start with simple - plugged my network cable into eth0 instead of eth1, thus moving all network-related interrupts to separate IRQ. This helped actually, I haven's seen the issue since then.
I have no idea what caused the issue. From reading all the posts about similar issues I concluded that kernel does't like some hardware for some reason. Fedora discussion is probably the most thorough:
[https://bugzilla.redhat.com/show_bug.cgi?id=474624](https://bugzilla.redhat.com/show_bug.cgi?id=474624)
Different people seem to have this problem with complete different kernels and different hardware, one solutions help some folks but are useless for others. There are things to try if you've got this kind of issue, but try to split your devices by different IRQs somehow first, as I did.

---

