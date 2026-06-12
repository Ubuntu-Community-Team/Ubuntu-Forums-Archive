---
title: "Cannot shutdown when 'acpi=off' is set in grub"
date: 2010-10-27
forum: General Help
---

### Post by 98cwitr on 2010-10-27
from etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off apm.power_off=1"
```

from /etc/modules
```

apm power_off=1
coretemp
it87

```


I have acpi turned off because if I don't I cant OC over 3.2GHz and Im completely fine and stable @ 3.6GHz. 

Problem is, when I try to shutdown, the system halts but doesn't power off. 

I have mulled over this documentation: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and none of the settings help, I apparently _have_ to have acpi turned completely off for the system to register the actual clock speed, and the catch22 is when it does work...I can't shut down.

also changed the syntax around as suggested in [this thread](http://ubuntuforums.org/showthread.php?t=414585)...still doesn't work

---

### Post by 98cwitr on 2010-10-28
bump

---

### Post by 98cwitr on 2010-10-29
x2

---

### Post by 98cwitr on 2010-10-31
x3 anyone?

---

### Post by gradinaruvasile on 2010-10-31
Do you really really need that OC (other than to just have it working on Linux)?
ACPI is very convenient to have.

---

### Post by 98cwitr on 2010-10-31
> **gradinaruvasile said:**
> Do you really really need that OC (other than to just have it working on Linux)?
ACPI is very convenient to have.

I'd really like to have the OC, but no I don't need it. I would at least like the OC to register correctly instead of being 3.2 all the time. Can anyone help me?

---

### Post by 98cwitr on 2010-11-02
x4

---

### Post by 98cwitr on 2010-11-05
I will never stop pursuing ;)

---

### Post by 98cwitr on 2010-11-08
weeeeeeeeeeeeeee:-\":-({|=[-o<

---

### Post by 98cwitr on 2010-11-10
bumpity

---

### Post by sreek_arc on 2010-11-11
Have you tried acpi_osi=linux or acpi_osi=!linux options?

---

### Post by 98cwitr on 2010-11-12
> **sreek_arc said:**
> Have you tried acpi_osi=linux or acpi_osi=!linux options?

the former yes, the latter no...I will when I get home though

---

### Post by 98cwitr on 2010-11-12
no joy...still halts and doesn't power off. I tried removing the apci=off string and leaving either option you posted and it still registers 3.2GHz for the clock speed.

---

### Post by 98cwitr on 2010-11-15
bump

---

### Post by 98cwitr on 2010-11-16
please dear God, let someone who is profoundly knowledgeable regarding APCI see this thread -Amen

---

### Post by 98cwitr on 2010-11-17
[img]http://i305.photobucket.com/albums/nn221/MREINLA/BUMP-2.jpg[/img]

---

### Post by 98cwitr on 2010-11-19
posted question in launchpad...

---

### Post by edward1978 on 2010-11-19
With ACPI off, the system can still shut down on its own?? I thought it could not.

---

### Post by Soul-Sing on 2010-11-19
maybe acpi=force will help you.
(And may the force be with ya.)

---

### Post by 98cwitr on 2010-11-19
> **edward1978 said:**
> With ACPI off, the system can still shut down on its own?? I thought it could not.

you're right and that's what im saying...it wont shutdown and if acpi=force is set the freq clock is still off.

---

### Post by 98cwitr on 2010-11-21
bump

---

### Post by 98cwitr on 2010-11-23
bump

---

### Post by 98cwitr on 2010-11-29
plz, bump

---

### Post by 98cwitr on 2010-12-01
if you view this...please bump it

---

### Post by happyhamster on 2010-12-01
I'm not sure I understand the issue: do you obtain a truly lower overclock when ACPI is enabled (system becomes unstable earlier), or is it a matter of frequencies that are reported wrong?

If it's the latter, then the reason is probably:
[http://codemonkey.org.uk/projects/cpufreq/common.php](http://codemonkey.org.uk/projects/cpufreq/common.php)

Also, is speedstep enabled in the BIOS (and if so, does disabling/enabling it make any difference?).

---

### Post by 98cwitr on 2010-12-06
no speedstep settings in BIOS :(

---

### Post by happyhamster on 2010-12-07
> **98cwitr said:**
> no speedstep settings in BIOS :(
On your board (GA-P35-DS3L) it's called the "CPU EIST Function" (EIST = Enhanced Intel SpeedStep Technology).

And let's bump my question: do you obtain a truly lower overclock when ACPI is enabled (system becomes unstable earlier), or is it only a matter of frequencies that are reported wrong? (Correct in the BIOS, wrong in Ubuntu.)

---

### Post by 98cwitr on 2010-12-09
> **happyhamster said:**
> On your board (GA-P35-DS3L) it's called the "CPU EIST Function" (EIST = Enhanced Intel SpeedStep Technology).

And let's bump my question: do you obtain a truly lower overclock when ACPI is enabled (system becomes unstable earlier), or is it only a matter of frequencies that are reported wrong? (Correct in the BIOS, wrong in Ubuntu.)

Ill turn EIST off and see what happens...thank you.

based on the temps I get under load, I think I am getting the correct OC, is there a way to actually verify that?

---

### Post by 98cwitr on 2010-12-10
> **happyhamster said:**
> On your board (GA-P35-DS3L) it's called the "CPU EIST Function" (EIST = Enhanced Intel SpeedStep Technology).

And let's bump my question: do you obtain a truly lower overclock when ACPI is enabled (system becomes unstable earlier), or is it only a matter of frequencies that are reported wrong? (Correct in the BIOS, wrong in Ubuntu.)

Turned it off...works perfect! You sir...are offically the man.  Thank you Thank you Thank you

---

