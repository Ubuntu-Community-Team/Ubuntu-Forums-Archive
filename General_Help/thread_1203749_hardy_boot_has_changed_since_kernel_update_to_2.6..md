---
title: "hardy boot has changed since kernel update to 2.6.24.24"
date: 2009-07-03
forum: General Help
---

### Post by charonred on 2009-07-03
(Update: problem not there when booting previous kernel - see 2nd post page 2)

A day or two ago, one of the normal updates included some kernel bits; currently its 2.6.24.24 generic; and my Hardy is now 8.04.3 (last time I noticed the version it was 8.04.2).

Ever since then my Hardy boot has changed; it used to go from progress bar to background screen (human colour), then to desktop. 

Now it goes from progress bar, to script, to background, and finally to desktop; has something gone wrong, can I fix it?

I took some snapshots with my camera during boot this morning;

[IMG]http://charonred.com/photos/ubuntu/desktop.jpg[/IMG] [IMG]http://charonred.com/photos/ubuntu/desktop1.jpg[/IMG] [IMG]http://charonred.com/photos/ubuntu/desktop2.jpg[/IMG] [IMG]http://charonred.com/photos/ubuntu/desktop3.jpg[/IMG] [IMG]http://charonred.com/photos/ubuntu/desktop4.jpg[/IMG]

---

### Post by dcstar on 2009-07-03
> **charonred said:**
> A day or two ago, one of the normal updates included some kernel bits; currently its 2.6.24.24 generic; and my Hardy is now 8.04.3 (last time I noticed the version it was 8.04.2).

Ever since then my Hardy boot has changed; it used to go from progress bar to background screen (human colour), then to desktop. 

Now it goes from progress bar, to script, to background, and finally to desktop; has something gone wrong, can I fix it?
........

When things take too long to load, or there are errors that you need to be notified about, then you will be shown the errors.

Take note of those error messages and address them.

---

### Post by charonred on 2009-07-03
is there a way to access these 'error messages' once it's finished booting, cause I don't have any chance of taking note of them, they flash by so quickly.

---

### Post by aesis05401 on 2009-07-04
> **charonred said:**
> is there a way to access these 'error messages' once it's finished booting, cause I don't have any chance of taking note of them, they flash by so quickly.

```

# Explanation
man dmesg

# Generate text file named boot.messages
dmesg > boot.messages

```

---

### Post by charonred on 2009-07-04
thanks, but I still need step by step instructions when using Terminal; what do I do to generate a text file named boot.messages and where does it get saved.

---

### Post by jocko on 2009-07-04
> **charonred said:**
> thanks, but I still need step by step instructions when using Terminal; what do I do to generate a text file named boot.messages and where does it get saved.
Exactly what aesis05401 said: Open up a terminal and type:
```
dmesg > boot.messages
```That will make a file named boot.messages in the current directory (which would be your home directory unless you have navigated your terminal anywhere else).
If you want it on your desktop instead:
```
dmesg > ~/Desktop/boot.messages
```Or if you want the file to have another name:
```
dmesg > [COLOR=Red]filename[/COLOR]
```

---

### Post by hyperdude111 on 2009-07-04
Install start-up-manager then Set usplash to ubuntu and it shoiuld work.

---

### Post by aesis05401 on 2009-07-04
charonred:

The '>' and '>>' symbols are very helpful from the terminal.  You can add these symbols after pretty much any command to redirect the output of the command.

> = write/overwrite
>> = append

Another example - Typing 'ifconfig' from a terminal will display the current settings for your network interfaces.  

```

# display settings to 'standard output' (your screen in this case)
ifconfig

# write current settings to 'filename'/will overwrite if file exists 
ifconfig > filename

# append current settings to end of 'filename'
ifconfig >> filename

# I use the 'less' command to view read only copies/'nano' to modify

# display a file read only
less filename

# open file for modification
nano filename

```

Terminal operations are actually much more direct and simple if you know where to research their operations.  Typing 'man' before pretty much any command will give a good starting place for research.

Good luck.

---

### Post by charonred on 2009-07-04
thanks peeps, will keep this info to one side for future reference as well.

---

### Post by charonred on 2009-07-05
**_start-up-manager_**
I installed start-up-manager; and when I ran it, it was already set to usplash-theme-ubuntu - so nothing has changed, and I still get this screen full of text between the progress bar and the (Human) background colour before finally loading desktop.

Would altering the **Timeout** in bootloader menu fix this; currently set to 3 seconds 

---------------------------

**_boot.messages_**
I generated the file, then did a search/find for  - error, fail, not & disabled; which returned the following, is there anything to be concerned about or needs addressing ?

> ERROR
[   30.417335] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.


FAIL
[   30.174685] Failure registering capabilities with primary security module.
[   43.946816] PM: Resume from disk failed.
[   32.214865] 0000:00:13.2 OHCI: BIOS handoff failed (BIOS bug ?) 00000184


NOT
[   30.697530] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   30.838583] system 00:02: ioport range 0xb00-0xb1f could not be reserved
[   30.838591] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[   30.838597] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[   30.838598] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[   30.838600] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[   30.838602] system 00:0e: iomem range 0x7fee0000-0x7fefffff could not be reserved
[   30.838604] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
[   30.838606] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   30.838608] system 00:0e: iomem range 0x100000-0x7fedffff could not be reserved
[   30.838610] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[   30.838612] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[   30.838614] system 00:0e: iomem range 0xfff80000-0xfffeffff could not be reserved
[   32.663926] Cannot allocate resource for EISA slot 4
[   32.664167] EDD information not available.
[   33.811338] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.811346] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   61.658473] apm: disabled - APM is not SMP safe.


DISABLED
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[   30.174672] SELinux:  Disabled at boot.
[   30.694435] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.694522] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.694620] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.694706] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.694791] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.694878] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.694964] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.695049] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.697400] PnPBIOS: Disabled by ACPI PNP
[   31.358152] audit: initializing netlink socket (disabled)
[   42.560566] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   42.676658] ACPI: PCI interrupt for device 0000:03:00.1 disabled
[   42.676701] ACPI: PCI interrupt for device 0000:04:00.1 disabled
[   61.658473] apm: disabled - APM is not SMP safe.
[   90.354806] lo: Disabled Privacy Extensions

---

### Post by charonred on 2009-07-05
further to the above, the text being displayed during boot seems to be different than what is being displayed in boot.messages

The screen shows something about Network something failing; though I have no problem with accessing the router, modem and internet once system has finished booting - yet when I do a search in  boot.messages the word Network isn't even found ??

During boot, the progress bar gets to about 3 panels/blocks from end, hangs for about 7 seconds, quickly spits up a couple of screens of text, displays the background colour, then finishes booting to desktop - the boot.messages don't seem to be displaying the text that appears during the 'break' in boot process.

---

### Post by charonred on 2009-07-06
Decided to boot using previous kernel 2.6.24-23-generic instead of current 2.6.24-24-generic and boot was normal as before; Ubuntu progress bar, background colour and then desktop.

generated messages as per previous post with search for error, fail, not & disabled; and compared with messages for 2.6.24-24-generic; both list the same - so problem appears to be with latest kernel, would this be correct assumption?

Do I fix this by  setting default boot to 2.6.24-23-generic, or should I continue using current kernel with changed boot  - what's the recommendation, is there any harm done using previous kernel ?

Is this something I should report to Launchpad, or elsewhere?

> ERROR
[   47.593046] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

FAIL
[   47.107046] Failure registering capabilities with primary security module.
[   50.162888] 0000:00:13.3 OHCI: BIOS handoff failed (BIOS bug ?) 00000184
[   62.409805] PM: Resume from disk failed.


NOT
[   47.593046] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   47.871721] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   48.010908] system 00:02: ioport range 0xb00-0xb1f could not be reserved
[   48.010916] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[   48.010921] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[   48.010923] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[   48.010925] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[   48.010927] system 00:0e: iomem range 0x7fee0000-0x7fefffff could not be reserved
[   48.010929] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
[   48.010931] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   48.010933] system 00:0e: iomem range 0x100000-0x7fedffff could not be reserved
[   48.010935] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[   48.010936] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[   48.010938] system 00:0e: iomem range 0xfff80000-0xfffeffff could not be reserved
[   50.583956] Cannot allocate resource for EISA slot 4
[   50.584192] EDD information not available.
[   51.739434] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   51.739442] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   77.794199] apm: disabled - APM is not SMP safe.

DISABLED
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[   47.107033] SELinux:  Disabled at boot.
[   47.868956] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   47.869030] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   47.869103] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   47.869175] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   47.869248] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   47.869322] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   47.869396] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   47.869468] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   47.871592] PnPBIOS: Disabled by ACPI PNP
[   48.773550] audit: initializing netlink socket (disabled)
[   60.904661] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   60.904709] ACPI: PCI interrupt for device 0000:03:00.1 disabled
[   60.904755] ACPI: PCI interrupt for device 0000:04:00.1 disabled
[   87.498216] lo: Disabled Privacy Extensions




---

### Post by mc4man on 2009-07-06
Whether or not any of the messages you're seeing represent any 'real' problem you;d have to search out, though it sounds like you've noticed none in your usage.

An ex.
> ERROR
[ 47.593046] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

Here's a short info on that, again if you're having no boot or suspend, ect. issues... (if you even use suspend


> The purpose of this optional kernel feature, enabled by "CONFIG_ACPI_CUSTOM_DSDT_INITRD=y" in the kernel .config at build-time, is to allow the user to replace the BIOS Advanced Configuration & Power Interface (ACPI) Differentiated System Description Table (DSDT) with one that has been modified to solve problems in the BIOS shipped by manufacturers.

The message you see is correct. As far as the kernel is concerned it is an error because it is told to expect to find a replacement DSDT.aml and it isn't there. However the message could be altered somewhat to make it sound less harsh.

The only difference in your boots is ...23 is booting with quiet splash and ...24 isn't, even though the boot parameters for ...24 probably include quiet splash

I've seen this many times on our various machines, though usually with the ones that have 2 or more ubuntu installs

sometimes you can get it to go back to the quiet boot, sometimes not, there doesn't appear to be any rhyme or reason to how or why.

Ex.'s

on a laptop with only 8.04 -        quiet

desktop w/ 8.04 and 8.10 -         'non quiet' for both

desktop w/8.04, 8.10, 8.04 - first installed 8.04 - 'non quiet
                             2nd installed  8.10 - 'non quiet'
                             last installed 8.04 - quiet

                             '
In the last ex. the 8.10 could be switched back to quiet, the first installed 8.04 no way.

In the end it doesn't matter much, actually gives you a small opurtunity to view potential issues 
(in other words the boots are the same, with quiet you don't see the message output, when quiet isn't used you do

---

### Post by charonred on 2009-07-06
thanks mc4man for explanations; you're right I don't use suspend, PC is either on or off, and I have no problems with BIOS.

I only have 8.04.3 installed on this drive; any other OS's I use I either have installed on separate drives, or in VirtualBox in 8.04, or in another PC (again with multiple drives) - I got sick of the hassles with multi-boot partitions. 

So what I'm experiencing with -24 is just a 'luck of the draw' random 'non-quiet' splash ... using start-up-manager I've set it to default boot -23; no harm in that is there, maybe it'll correct itself when  -25 is released.

---

