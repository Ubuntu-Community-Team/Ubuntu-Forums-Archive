---
title: "initramfs"
date: 2011-07-18
forum: General Help
---

### Post by accodata on 2011-07-18
Hi
I rebooted my pc which I have 10.4.2 installed, and it tells me that there is a problem with busybox.
so I put in the live cd, and thought oh I will reinstall ubuntu, (my system was ok before I rebooted). But to reinstall the installation wont go past the time installation page.
the complete message is
[2.23947] {<c1097ac>] ? syscall_call+0x7/0xb
[2.239347] Code: 00 55 89 e5 57 89 c7 56 53 e8 a3 af 25 00 8b 5f 04 b8 ff ff ff ff 8b 77 08 eb 1c 8d b6 00 00 00 00 8b 0c 85 e0 06 7e c0 8b 57 14 <8b> 14 0a 89 d1 c1 f9 1f 01 d3 11 ce 8d 48 01 a1 6c 01 5c c0 ba
[2.239347] EIP: [<c03672da>] --percpu_counter_sum+0x2a/0x70 SS:ESP 0068:f690dd6c
[2.239347] CR2: 000000000317booo
[2.243640] ---[ end trace 1e645d36ab07da55 ]---
killed
mount: mounting /dev on/root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootary.

BusyBox v1.13.3 (Ububtu 1:1.13.3-1ubuntu11) built-in shekk (ash)
Enter 'help' for a list of commands.

(initramfs)[       6.592703] usb-storage: device scan complete
[6.595399] scsi 6:0:0:0: Direct-Acess      Canon     MP490 series     0102 PQ: 0 ANSI: 2
[ 6.595764] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 6.601020] sd 6:0:0:0: [sdb] Attached SCSI removable disk

please if I can get some help I would be so greatful.

Tracey

---

### Post by dino99 on 2011-07-18
try first to boot into "recovery mode", then select "repair packages" and/or select netboot.

if the grub menu is hidden at boot time (default on single OS), hold "shift" key down at bios end process to see it.

---

### Post by accodata on 2011-07-18
Hi Dino99
Yes I only have ubuntu on my pc
I pressed the 'shift key' it goes into the recovery screen but I don't have netboot. 
If I choose the recovery mode, it goes back into the screen as I first described.

Tracet

---

### Post by dino99 on 2011-07-18
from the recovery menu, you need to select what to do, and you will see the options

---

### Post by DawieS on 2011-07-18
I recommend that you:
- Boot from the Live CD.
- Choose **Try Ubuntu**, then click on **System > Administration > Disk Utility**.
- Click on your Ubuntu drive, then click on every partition, then **Check Filesystem**.
- If all partitions report clean, then see if you can reboot from your hard disk.:smile:

---

### Post by psusi on 2011-07-18
There should be some more messages prior to what you posted.  You might use the dmesg command to review them:

dmesg | more

---

