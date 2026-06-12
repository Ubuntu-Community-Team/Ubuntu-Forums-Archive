---
title: "Fail in evaluating the _REG object of EC device. Broken bios is suspected.  Debian"
date: 2011-06-16
forum: General Help
---

### Post by Shpongle on 2011-06-16
Hi all , I recently got a new laptop (a hp pavillion g6-1000) and installed debian squeeze x64 and kde on it.

I am getting the error listed in the title when booting , I can still use the OS as expected but the error is bugging me. Some searches reveal it may be something to do with hp as I have seen others with similar hp models listing the same issue.




 A dmesg |grep -i "fail" produces

[    1.912128] ACPI Error (psargs-0359): [\_PR_.CPU0._PPC] Namespace lookup failure, AE_NOT_FOUND
[    1.912144] ACPI Error (psparse-0537): Method parse/execution failed [\CPUT] (Node ffff880157a50d00), AE_NOT_FOUND
[    1.912229] ACPI Error (psparse-0537): Method parse/execution failed [\PSSC] (Node ffff880157a50d20), AE_NOT_FOUND
[    1.912312] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._REG] (Node ffff880157a41000), AE_NOT_FOUND
[    1.912500] Fail in evaluating the _REG object of EC device. Broken bios is suspected.
[    3.094458] PM: Resume from disk failed.
[    3.162978] ACPI Error (psargs-0359): [\_PR_.CPU0._PPC] Namespace lookup failure, AE_NOT_FOUND
[    3.162994] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.TZ01.OTHD] (Node ffff880157a50b60), AE_NOT_FOUND
[    3.163119] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.TZ01._TMP] (Node ffff880157a50a80), AE_NOT_FOUND
[    4.079185] PM: Resume from disk failed.
[    8.708298] [drm] MTRR allocation failed.  Graphics performance may suffer.



If anyone could help me to fix these errors it would be greatly appreciated .

---

### Post by theburrus1 on 2011-08-12
Hi Shpongle. It doesn't appear to be HP specific as I just installed Fedora on my Toshiba Satellite and experienced the exact same issue. I am currently searching for a cause and fix in forums so I will followup with more info. Also, interestingly, before I installed Fedora, I ran Ubuntu 11.04 with no problems like that. So I am going to install Kubuntu over Fedora now and see if perhaps it a RedHat issue on laptops.

---

### Post by mikejonesey on 2011-10-03
me too... hp g6, i did not have this problem on my hp g56 though...

---

### Post by matt_symes on 2011-10-03
Hi

@mikejonesey. Out of interest could you post the output of this command.
[FONT=monospace]
[/FONT]```
dmesg | grep DSDT
```

A custom dsdt may fix it but is it worth all that trouble ?

Kind regards

---

### Post by mikejonesey on 2011-10-04
@matt

Hi I'm not too sure what this particular error is... My first guess was a bad driver / missing kernal module...

> [    0.000000] ACPI: DSDT 000000009b7e8000 105A5 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.542774] ACPI: EC: Look up EC in DSDT


I know the acpi controls battery and processors... but not sure what is wrong... there is no fan within the acpi so my best guess is I need a driver / patch to support either the fan or the pci bridge it's connected to... but I'm not sure...

can you shed any light / additional info on this matt?

cheers,
Mike

---

### Post by matt_symes on 2011-10-04
Hi

> **mikejonesey said:**
> @matt

Hi I'm not too sure what this particular error is... My first guess was a bad driver / missing kernal module...
> 
[    0.000000] ACPI: DSDT 000000009b7e8000 105A5 (v01 HPQOEM SLIC-MPC 00000001 [COLOR=Red]MSFT[/COLOR] 01000013)
[    0.542774] ACPI: EC: Look up EC in DSDT                      I know the acpi controls battery and processors... but not sure what is wrong... there is no fan within the acpi so my best guess is I need a driver / patch to support either the fan or the pci bridge it's connected to... but I'm not sure...

can you shed any light / additional info on this matt?

cheers,
Mike

Your DSDT was compiled with Microsoft's ASL complier (highlighted in [COLOR=Red]red[/COLOR] above). This does not adhere to the ACPI specification as strictly as other ASL compliers - such as Intels - and Linux decodes the AML strictly.

This is why you are getting the error.

A dsdt that is strictly compiled will work fine under Linux.

Windows, on the other hand, is far more forgiving in how it decodes AML generated from the Microsoft ASL complier, but it can break Linux which expect a strict compilation.

To get around this you have to decompile the dsdt, fix the dsdt, recompile the dsdt and finally build a custom kernel that includes the dsdt.

That's a lot of work and each time you get a kernel upgrade.......

EDIT for clarification: That is not to say that all dsdts compiled with the Microsoft compiler are buggy. I am only saying that a dsdt can be compiled to aml that does not adhere to the specification if it is written that way.

For the exercise you can get the dsdt, decompile it and recompile it and see the errors (deviations from the specification) using a different complier than Microsofts.

The compiled dsdt is at

```
/proc/acpi/dsdt
```EDIT 2: That should have been AML and not ASL. This post is edit accordingly.

Kind regards

---

### Post by mikejonesey on 2011-10-04
great stuff matt, much apreciated... I'll probably be recompiling again anyway for my wifi modules...

anyway many thanks

---

