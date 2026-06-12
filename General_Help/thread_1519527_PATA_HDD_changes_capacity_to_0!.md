---
title: "PATA HDD changes capacity to 0!?"
date: 2010-06-28
forum: General Help
---

### Post by revered on 2010-06-28
I have a secondary PATA HDD with XP installed and NTFS filesystem. Normally if I go to Administration > Disk Utility, I see the hdd under PATA host adapter, and if I select it I can see the partition.

The problem is that sometimes the hdd disappear, it shows up on Disk Utility but if i select it it shows no size like not being partitioned.

Here's the syslog

```
Jun 28 10:39:43 desktop kernel: [  100.816028] ata1: lost interrupt (Status 0x50)
Jun 28 10:40:14 desktop kernel: [  131.816059] ata1: lost interrupt (Status 0x51)
Jun 28 10:40:19 desktop kernel: [  136.816073] ata1.01: qc timeout (cmd 0xa0)
Jun 28 10:40:19 desktop kernel: [  136.816089] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jun 28 10:40:19 desktop kernel: [  136.816096] sr 0:0:1:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Jun 28 10:40:19 desktop kernel: [  136.816116] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jun 28 10:40:19 desktop kernel: [  136.816118]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Jun 28 10:40:19 desktop kernel: [  136.816123] ata1.01: status: { DRDY ERR }
Jun 28 10:40:19 desktop kernel: [  136.816163] ata1: soft resetting link
Jun 28 10:40:25 desktop kernel: [  142.172042] ata1.00: qc timeout (cmd 0xf8)
Jun 28 10:40:25 desktop kernel: [  142.172053] ata1.00: failed to read native max address (err_mask=0x4)
Jun 28 10:40:25 desktop kernel: [  142.172059] ata1.00: revalidation failed (errno=-5)
Jun 28 10:40:25 desktop kernel: [  142.172100] ata1: soft resetting link
Jun 28 10:40:35 desktop kernel: [  152.528042] ata1.00: qc timeout (cmd 0xf8)
Jun 28 10:40:35 desktop kernel: [  152.528053] ata1.00: failed to read native max address (err_mask=0x4)
Jun 28 10:40:35 desktop kernel: [  152.528059] ata1.00: revalidation failed (errno=-5)
Jun 28 10:40:35 desktop kernel: [  152.528100] ata1: soft resetting link
Jun 28 10:40:45 desktop kernel: [  162.884041] ata1.00: qc timeout (cmd 0xf8)
Jun 28 10:40:45 desktop kernel: [  162.884053] ata1.00: failed to read native max address (err_mask=0x4)
Jun 28 10:40:45 desktop kernel: [  162.884058] ata1.00: revalidation failed (errno=-5)
Jun 28 10:40:45 desktop kernel: [  162.884064] ata1.00: disabled
Jun 28 10:40:45 desktop kernel: [  162.884077] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc6c50000) ACPI=0x1f01f (20:30:0x15)
Jun 28 10:40:45 desktop kernel: [  162.884082] ata1.01: limited to UDMA/33 due to 40-wire cable
Jun 28 10:40:45 desktop kernel: [  162.884109] ata1.01: failed to set xfermode (err_mask=0x40)
Jun 28 10:40:45 desktop kernel: [  162.884142] ata1: soft resetting link
Jun 28 10:40:46 desktop kernel: [  163.232517] ata1: nv_mode_filter: 0x739f&0x1f39f->0x739f, BIOS=0x1f000 (0xc6c50000) ACPI=0x1f01f (20:30:0x15)
Jun 28 10:40:46 desktop kernel: [  163.264437] ata1.01: configured for UDMA/33
Jun 28 10:40:51 desktop kernel: [  168.264038] ata1.01: qc timeout (cmd 0xa0)
Jun 28 10:40:51 desktop kernel: [  168.264049] ata1.01: TEST_UNIT_READY failed (err_mask=0x5)
Jun 28 10:40:51 desktop kernel: [  168.264056] ata1.01: limiting speed to UDMA/33:PIO3
Jun 28 10:40:51 desktop kernel: [  168.264093] ata1: soft resetting link
Jun 28 10:40:51 desktop kernel: [  168.612506] ata1: nv_mode_filter: 0x738f&0x1f39f->0x738f, BIOS=0x1f000 (0xc6c50000) ACPI=0x1f01f (20:30:0x15)
Jun 28 10:40:51 desktop kernel: [  168.644439] ata1.01: configured for UDMA/33
Jun 28 10:40:56 desktop kernel: [  173.644037] ata1.01: qc timeout (cmd 0xa0)
Jun 28 10:40:56 desktop kernel: [  173.644048] ata1.01: TEST_UNIT_READY failed (err_mask=0x5)
Jun 28 10:40:56 desktop kernel: [  173.644053] ata1.01: disabled
Jun 28 10:40:56 desktop kernel: [  173.644103] ata1: soft resetting link
Jun 28 10:40:56 desktop kernel: [  173.968116] ata1: EH complete
Jun 28 10:40:56 desktop kernel: [  173.968352] sd 0:0:0:0: [sda] READ CAPACITY(16) failed
Jun 28 10:40:56 desktop kernel: [  173.968357] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 28 10:40:56 desktop kernel: [  173.968364] sd 0:0:0:0: [sda] Sense not available.
Jun 28 10:40:56 desktop kernel: [  173.968480] sd 0:0:0:0: [sda] READ CAPACITY failed
Jun 28 10:40:56 desktop kernel: [  173.968484] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 28 10:40:56 desktop kernel: [  173.968490] sd 0:0:0:0: [sda] Sense not available.
Jun 28 10:40:56 desktop kernel: [  173.968632] sd 0:0:0:0: [sda] Write Protect is on
Jun 28 10:40:56 desktop kernel: [  173.968637] sd 0:0:0:0: [sda] Mode Sense: d8 fe eb f1
Jun 28 10:40:56 desktop kernel: [  173.968661] sd 0:0:0:0: [sda] Asking for cache data failed
Jun 28 10:40:56 desktop kernel: [  173.968666] sd 0:0:0:0: [sda] Assuming drive cache: write through
Jun 28 10:40:56 desktop kernel: [  173.968676] sda: detected capacity change from 40020664320 to 0
```What could be happening? any solution? I really need that disk up and stable because I want to use the XP installation from that disk into a virtual machine.

---

### Post by oldfred on 2010-06-28
Have you run chkdsk on the NTFS partition(s)?

My NTFS partition was working and I could mount it in Ubuntu but when using gparted to edit some things it took forever to load that drive. And it did not load once or twice. There were a bunch of errors reported. I ran chkdsk on the NTFS partition and then the drive immediately loaded in gparted.

---

### Post by revered on 2010-06-28
I did a chkdsk /r /f and it fixed some stuff, but I still got the same problem (once so far).

Today I rebooted, and I was reading the syslog and I saw that log I pasted, and the hdd partition was "lost", I rebooted and it was working again, I booted the partition on a virtual machine with virtualbox, and used it for like an hour, algo mounted and unmounted the partition, and is still working. 

So I have no idea what could be triggering the problem, when it happened today I was only reading logs after a reboot so there wasn't many apps running.

On the disk utility I still see "SMART status: disk has a few bad sectors", and if I click SMART Data I see 1 bad sector, this was there before the chkdsk and is still there.

Any other chkdsk utility I could try? I downloaded partition magic but it only allow me to run chkdsk and defrag from windows because that partition is in use for win (I dont have any other win currently).

---

### Post by oldfred on 2010-06-28
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Run chkdsk repeatly until you get no errors. It does not fix them all each time.

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by revered on 2010-06-28
I have XP in that machine, I will try running chkdsk /r /f again then to see if it still need to fix something. Will update results later.

---

### Post by RJARRRPCGP on 2010-06-28
> **revered said:**
> I have a secondary PATA HDD with XP installed and NTFS filesystem. Normally if I go to Administration > Disk Utility, I see the hdd under PATA host adapter, and if I select it I can see the partition.

The problem is that sometimes the hdd disappear, it shows up on Disk Utility but if i select it it shows no size like not being partitioned.

Here's the syslog

```
Jun 28 10:39:43 desktop kernel: [  100.816028] ata1: lost interrupt (Status 0x50)
Jun 28 10:40:14 desktop kernel: [  131.816059] ata1: lost interrupt (Status 0x51)
Jun 28 10:40:19 desktop kernel: [  136.816073] ata1.01: qc timeout (cmd 0xa0)
Jun 28 10:40:19 desktop kernel: [  136.816089] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jun 28 10:40:19 desktop kernel: [  136.816096] sr 0:0:1:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Jun 28 10:40:19 desktop kernel: [  136.816116] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jun 28 10:40:19 desktop kernel: [  136.816118]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Jun 28 10:40:19 desktop kernel: [  136.816123] ata1.01: status: { DRDY ERR }
Jun 28 10:40:19 desktop kernel: [  136.816163] ata1: soft resetting link
Jun 28 10:40:25 desktop kernel: [  142.172042] ata1.00: qc timeout (cmd 0xf8)
Jun 28 10:40:25 desktop kernel: [  142.172053] ata1.00: failed to read native max address (err_mask=0x4)
Jun 28 10:40:25 desktop kernel: [  142.172059] ata1.00: revalidation failed (errno=-5)
Jun 28 10:40:25 desktop kernel: [  142.172100] ata1: soft resetting link
Jun 28 10:40:35 desktop kernel: [  152.528042] ata1.00: qc timeout (cmd 0xf8)
Jun 28 10:40:35 desktop kernel: [  152.528053] ata1.00: failed to read native max address (err_mask=0x4)
Jun 28 10:40:35 desktop kernel: [  152.528059] ata1.00: revalidation failed (errno=-5)
Jun 28 10:40:35 desktop kernel: [  152.528100] ata1: soft resetting link
Jun 28 10:40:45 desktop kernel: [  162.884041] ata1.00: qc timeout (cmd 0xf8)
Jun 28 10:40:45 desktop kernel: [  162.884053] ata1.00: failed to read native max address (err_mask=0x4)
Jun 28 10:40:45 desktop kernel: [  162.884058] ata1.00: revalidation failed (errno=-5)
Jun 28 10:40:45 desktop kernel: [  162.884064] ata1.00: disabled
Jun 28 10:40:45 desktop kernel: [  162.884077] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc6c50000) ACPI=0x1f01f (20:30:0x15)
Jun 28 10:40:45 desktop kernel: [  162.884082] ata1.01: limited to UDMA/33 due to 40-wire cable
Jun 28 10:40:45 desktop kernel: [  162.884109] ata1.01: failed to set xfermode (err_mask=0x40)
Jun 28 10:40:45 desktop kernel: [  162.884142] ata1: soft resetting link
Jun 28 10:40:46 desktop kernel: [  163.232517] ata1: nv_mode_filter: 0x739f&0x1f39f->0x739f, BIOS=0x1f000 (0xc6c50000) ACPI=0x1f01f (20:30:0x15)
Jun 28 10:40:46 desktop kernel: [  163.264437] ata1.01: configured for UDMA/33
Jun 28 10:40:51 desktop kernel: [  168.264038] ata1.01: qc timeout (cmd 0xa0)
Jun 28 10:40:51 desktop kernel: [  168.264049] ata1.01: TEST_UNIT_READY failed (err_mask=0x5)
Jun 28 10:40:51 desktop kernel: [  168.264056] ata1.01: limiting speed to UDMA/33:PIO3
Jun 28 10:40:51 desktop kernel: [  168.264093] ata1: soft resetting link
Jun 28 10:40:51 desktop kernel: [  168.612506] ata1: nv_mode_filter: 0x738f&0x1f39f->0x738f, BIOS=0x1f000 (0xc6c50000) ACPI=0x1f01f (20:30:0x15)
Jun 28 10:40:51 desktop kernel: [  168.644439] ata1.01: configured for UDMA/33
Jun 28 10:40:56 desktop kernel: [  173.644037] ata1.01: qc timeout (cmd 0xa0)
Jun 28 10:40:56 desktop kernel: [  173.644048] ata1.01: TEST_UNIT_READY failed (err_mask=0x5)
Jun 28 10:40:56 desktop kernel: [  173.644053] ata1.01: disabled
Jun 28 10:40:56 desktop kernel: [  173.644103] ata1: soft resetting link
Jun 28 10:40:56 desktop kernel: [  173.968116] ata1: EH complete
Jun 28 10:40:56 desktop kernel: [  173.968352] sd 0:0:0:0: [sda] READ CAPACITY(16) failed
Jun 28 10:40:56 desktop kernel: [  173.968357] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 28 10:40:56 desktop kernel: [  173.968364] sd 0:0:0:0: [sda] Sense not available.
Jun 28 10:40:56 desktop kernel: [  173.968480] sd 0:0:0:0: [sda] READ CAPACITY failed
Jun 28 10:40:56 desktop kernel: [  173.968484] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 28 10:40:56 desktop kernel: [  173.968490] sd 0:0:0:0: [sda] Sense not available.
Jun 28 10:40:56 desktop kernel: [  173.968632] sd 0:0:0:0: [sda] Write Protect is on
Jun 28 10:40:56 desktop kernel: [  173.968637] sd 0:0:0:0: [sda] Mode Sense: d8 fe eb f1
Jun 28 10:40:56 desktop kernel: [  173.968661] sd 0:0:0:0: [sda] Asking for cache data failed
Jun 28 10:40:56 desktop kernel: [  173.968666] sd 0:0:0:0: [sda] Assuming drive cache: write through
Jun 28 10:40:56 desktop kernel: [  173.968676] sda: detected capacity change from 40020664320 to 0
```What could be happening? any solution? I really need that disk up and stable because I want to use the XP installation from that disk into a virtual machine.

Sounds like the bug that was only reported for later Seagate Barracuda HDDs, mostly the Barracuda 7200.11, which was reported to have a firmware bug that causes the HDD to report 0 LBA!

If you have a Seagate Barracuda, it usually means the HDD got bricked!

I'm praying that my Barracuda 7200.12 don't do that!

---

### Post by revered on 2010-06-28
I tought it was barracuda but I checked the model (ST340810A) and it doesn't say anything about barracuda there -> [http://www.seagate.com/ww/v/index.jsp?vgnextoid=fffb5a802efbd010VgnVCM100000dd04090aRCRD&locale=en-US&reqPage=Legacy](http://www.seagate.com/ww/v/index.jsp?vgnextoid=fffb5a802efbd010VgnVCM100000dd04090aRCRD&locale=en-US&reqPage=Legacy)

---

### Post by RJARRRPCGP on 2010-06-29
> **revered said:**
> I tought it was barracuda but I checked the model (ST340810A) and it doesn't say anything about barracuda there -> [http://www.seagate.com/ww/v/index.jsp?vgnextoid=fffb5a802efbd010VgnVCM100000dd04090aRCRD&locale=en-US&reqPage=Legacy](http://www.seagate.com/ww/v/index.jsp?vgnextoid=fffb5a802efbd010VgnVCM100000dd04090aRCRD&locale=en-US&reqPage=Legacy)

I never heard of the U-series being affected with the 0 LBA bug.

But I have had a problem with a U-series becoming slow on me, with sectors slow to read. :( 
The symptom of that was a laggy OS. The OS just felt slllloooowwww!

And those were way before the Barracuda 7200.11.

---

