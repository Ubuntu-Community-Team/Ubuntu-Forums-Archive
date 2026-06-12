---
title: "shut down problem"
date: 2011-05-23
forum: General Help
---

### Post by acovuxsasa on 2011-05-23
I installed ubuntu 11.04 and everything is working great only when I go to shut down, my pc just do restart. I can shut down it only with the shut down button. Just to say, I have dual boot - win7 and 11.04 and on the win7 there is no such problem.

---

### Post by matt_symes on 2011-05-23
Hi

Open a terminal and type

```
sudo shutdown -h now
```

Enter your password. It will not be echoed to the screen. This is normal.

Does the PC restart if you do that ?

Kind regards

---

### Post by acovuxsasa on 2011-05-23
i did that and my PC restarts again

---

### Post by matt_symes on 2011-05-23
Hi

> **acovuxsasa said:**
> i did that and my PC restarts again

That sounds like it may be a BIOS or ACPI issue.

In the first instance check your BIOS settings. Make sure there are no options to restart.

What BIOS do you have ? It should flash up on the screen when you first boot your computer.

Either that or you can type (at a terminal).

```
sudo dmidecode --type BIOS
```to get BIOS information. If you post that back here, that might help facilitate a search to fix the problem.

The other thing you can do is to disable ACPI for 1 boot and try to shutdown. If it shuts down then you know it's something to do with ACPI and that can be used as a place to start debugging any issues. If you need instruction on how to edit the kernel line to disable ACPI then post back.

Kind regards

---

### Post by acovuxsasa on 2011-05-23
This is the bios information:

# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies, LTD
	Version: 6.00 PG
	Release Date: 05/10/2007
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

Handle 0x001C, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1

Just to know, i restarted bios and cmos but there was no change.
I use ubuntu from 8.10 on the same PC and I didn`t had such problem, only with 11.04.
I dont know how to turn of ACPI
Thanx for helping me

---

### Post by matt_symes on 2011-05-23
Hi

> I use ubuntu from 8.10 on the same PC and I didn`t had such problem, only with 11.04.Don't you just hate that ? That makes it more interesting.

Some things to check in the BIOS. Make sure Wake on Lan is disabled. Make sure there are not options to reboot where shutdown is applicable.

Try shutting down your PC this way 

Press and hold right ALT + sysctl and keep those two keys depressed while hitting these keys one after another: R E I S U O

Leave a three second gap between hitting each REISUO key. That is the magic combination to shut down the PC. See if that works.

To disable acpi reboot your PC. At the grub prompt where you select your kernel press the e key to edit the kernel command line. scroll to the end of the line that looks something similar to (I'm posting this from Lucid. Yours will look slightly different)

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-31-generic root=UUID=07b36494-6676-4567-998f-7d18bdf62d63 ro quiet splash
```and add at the end of the line 

```
apci=off
```Press ctrl and x together to continue booting. When you have logged in, try to shut down normally.

Kind regards

---

### Post by acovuxsasa on 2011-05-23
sorry I don`t understand, you said to press and hold ALT + sysctl, what is that sysctl key?

---

### Post by matt_symes on 2011-05-23
Hi

> **acovuxsasa said:**
> sorry I don`t understand, you said to press and hold ALT + sysctl, what is that sysctl key?

Sorry. That should have been_ ALT + SysRq _and not sysctl.

Kin regards

---

