---
title: "Bad Lenovo"
date: 2011-12-06
forum: General Help
---

### Post by Ted3929 on 2011-12-06
Tried posting this in Laptop area but couldn't access those pages.

Attempting to install Ubuntu 11.04 on Lenovo SL410 with Intel Dual Core.  In short, nothing special, just another laptop.

Ubuntu works fine in live mode but after I install it boot shows nothing but a black screen with a flashing cursor.  I can't access menus nor do I get a boot menu offering safe mode.  I just get zip even though the total installation process went as you might expect.

I have heard of problems with IBM/Lenovos before but Canonical states this unit works fine with this version so I did a little test.  I swapped my hard drive into a Fujitsu laptop and loaded Ubuntu there and then put the drive back in the Lenovo.

Although this does work you have the various hardware issues and the fact your computer is improperly identified.

Does anybody have a clue as to why Ubuntu 11.04 will not work on Lenovos?

---

### Post by mastablasta on 2011-12-06
perhaps it needs porprietary drivers instaleld. try installing it with alternate cd and then befor ereboot also isntall any proprietary drivers.

---

### Post by Matt__ on 2011-12-06
there IS a modified ubuntu 10.10 that shipped with this lenovo model in some regions, if you could find that it would solve all your probs.

However it does sound like an [ACPI]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface") problem
```


[LIST=1]
[*]Boot the machine.
[*]During the BIOS screen, press the shift key and hold it down. You should see the GRUB menu after the BIOS loads.
[*]Navigate to the kernel entry you want to boot, and press 'e'.
[*]Then remove the **quiet** and **splash** keywords (found in the line starting with linux)
[*]Press 'Ctrl+x' to boot.
[/LIST]

``` next try to pin down the problem by adding these options.
```


[LIST=1]
[*]Try booting with the "acpi=off" kernel parameter
[LIST]
[*]This will disable ACPI support.  If the error is the same with ACPI enabled and disabled, this may not be an ACPI issue.
[/LIST]
 
[*]If "acpi=off" allows the system to boot, try to isolate the ACPI issue with the following boot parameters
[LIST]
[*]Try booting with "acpi=ht"[COLOR=Red] 
[/COLOR]
[LIST]
[*]This  disables all of ACPI except just enough to enable Hyper Threading.  If  acpi=off works and acpi=ht fails, then the issue is in the ACPI table  parsing code itself, or perhaps the SMP code.
[/LIST]
 
[*]Try booting with "pci=noacpi"
[LIST]
[*]This disables ACPI for IRQ routing and PCI scanning.
[/LIST]
 
[*]Try booting with "acpi=noirq"
[LIST]
[*]This disables ACPI for IRQ routing.
[/LIST]
 
[*]Try booting with "pnpacpi=off"
[LIST]
[*]This disables the ACPI component of the Linux Plug and Play code.
[/LIST]
 
[*]Try booting with "noapic"
[LIST]
[*]Disables the IO-APIC for IRQ routing or PCI scanning.
[/LIST]
 
[*]Try booting with "nolapic"
[LIST]
[*]Disables the local APIC.
[/LIST]
 
[/LIST]
 
[/LIST]

```should keep you busy for a little while :P

//edit: I also found this option but relating to 10.10 install
append the quiet splash entry with ```
intel_idle. Max_cstate=0
```

---

### Post by Ted3929 on 2011-12-06
cripes, sounds like more than I want to fool with.  I did get Xfce to work without a hitch so maybe it's something with Gnome.

Guess I'll stick with Xfce for a while

---

### Post by Matt__ on 2011-12-06
It just looks scary, at least take a look, I'm sure you'll figure it out fine.
Or like I said, try and find the pre-install version from lenovo.

---

