---
title: "making kernel changes"
date: 2011-02-08
forum: General Help
---

### Post by qwertyjjj on 2011-02-08
I have been given a potential solution to fixing my CPU lock issue ([http://ubuntuforums.org/showthread.php?p=10415826#post10415826](http://ubuntuforums.org/showthread.php?p=10415826#post10415826)).

> 
I had a similar problem back in 2007: [https://bugzilla.kernel.org/show_bug.cgi?id=9488](https://bugzilla.kernel.org/show_bug.cgi?id=9488) In my case a broken BIOS was the reason. As I could not get a newer (fixed) BIOS, I found two workarounds: a) using the processor.ignore_ppc flag, and b) (the "final" solution): using a kernel parameter acpi_osi="!Windows 2006" 

Are these kernel changes and if so, how can I make them?
I saw this as a possible solution for the 1st one:

> Please try creating the file /etc/modprobe.d/processor-ppc.conf
containing the text:

options processor ignore_ppc=1

and then reboot. 

Is that the correct way to do it or should it be loaded at bootup?
If I create that file, how is Ubuntu supposed to know to load it?

I tried using this in maverick meerkat: sudo gedit /boot/grub/menu.lst
but the file is empty!
Where can I add the acpi_osi line in meerkat? is it to grub.cgf or /etc/default/grub?

---

### Post by P4man on 2011-02-08
See the link in my signature for a detailed explanation how to add kernel parameters.

acpi_osi="**!**Windows 2006"  is an interesting one, I suspect it means Linux will respond to all OSI queries except for vista, IOW, it will pretend being any windows version other than vista. I never knew about that one, must add it to my howto :).  What machine do you have?

---

### Post by qwertyjjj on 2011-02-08
> **P4man said:**
> See the link in my signature for a detailed explanation how to add kernel parameters.

acpi_osi="**!**Windows 2006"  is an interesting one, I suspect it means Linux will respond to all OSI queries except for vista, IOW, it will pretend being any windows version other than vista. I never knew about that one, must add it to my howto :).  What machine do you have?

I have an Inspiron 9300 (DELL), which is limiting my CPU to 800 for some reason. We are not sure if it is a temperature sensor or the BIOS but the bios_limit starts at 1733000 and then throttles it to 800 somewhere between 15-45 mins afterwards and cpufreqd cannot increase it.

Is this the correct way?
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\\\"!Windows 2006\\\""

j@j-Inspiron-9300:~$ dmesg | grep ACPI | grep -i windows
[    0.113919] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug

---

### Post by P4man on 2011-02-08
Nope. See my link:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2006\""
```
And dont forget to run update-grub. But I would try the setting temporarily first, make sure it actually works, again see my howto.

---

### Post by qwertyjjj on 2011-02-08
> **P4man said:**
> Nope. See my link:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2006\""
```
And dont forget to run update-grub. But I would try the setting temporarily first, make sure it actually works, again see my howto.

Thanks.
Well, I tried that and on restart it still starts off at 1.73 on performance and then throttles down to 800.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2006\""

So, is it acpi or the BIOS or speedstep?

---

### Post by qwertyjjj on 2011-02-08
> **P4man said:**
> Nope. See my link:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2006\""
```
And dont forget to run update-grub. But I would try the setting temporarily first, make sure it actually works, again see my howto.

how come I have to use delimiters.
In the how to, you write: acpi_osi="Windows 2006"

So, shouldn;t mine be acpi_osi="!Windows 2006" instead of:
acpi_osi=\"!Windows 2006\""

---

### Post by P4man on 2011-02-08
> **qwertyjjj said:**
> Thanks.
Well, I tried that and on restart it still starts off at 1.73 on performance and then throttles down to 800.


Speedstep. It should do that. It will only ramp the clock up if the extra cpu speed is needed. You can add CPU frequency monitor to the taskbar (just right click it and add it) and manually change speed if you want, but the default is 'on demand' and its usually what you want.

> 
nd dont forget to run update-grub. But I would try the setting temporarily first, make sure it actually works, again see my howto.
how come I have to use delimiters.
In the how to, you write: acpi_osi="Windows 2006"

So, shouldn;t mine be acpi_osi="!Windows 2006" instead of:
acpi_osi=\"!Windows 2006\"" 

You need the escape character "\" if you put it in a text file, like the grub config file. If you type the option in the grub menu manually each boot, you can omit it.

---

### Post by qwertyjjj on 2011-02-08
> **P4man said:**
> Speedstep. It should do that. It will only ramp the clock up if the extra cpu speed is needed. You can add CPU frequency monitor to the taskbar (just right click it and add it) and manually change speed if you want, but the default is 'on demand' and its usually what you want.



You need the escape character "\" if you put it in a text file, like the grub config file. If you type the option in the grub menu manually each boot, you can omit it.

That's what I mean speedstep is bust or something else is.
It LOCKS the speed to 800 preventing any increase to 1.73.

---

### Post by dino99 on 2011-02-08
> **P4man said:**
> Nope. See my link:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2006\""
```
And dont forget to run update-grub. But I would try the setting temporarily first, make sure it actually works, again see my howto.

GRUB_CMDLINE_LINUX="acpi_osi=Linux"

---

### Post by P4man on 2011-02-08
Have you tried adding the acpi_osi parameter with the correct syntax? If you (think you)  have, can you post the output of
```
cat /proc/cmdline
``` ? It should be in there, without escape characters

---

### Post by P4man on 2011-02-08
> **dino99 said:**
> GRUB_CMDLINE_LINUX="acpi_osi=Linux"

Thats great if his bios has provisions for linux, but from what he linked, it doesnt seem like it. Excluding vista from the osi queries might be his best bet.

---

### Post by qwertyjjj on 2011-02-08
> **dino99 said:**
> GRUB_CMDLINE_LINUX="acpi_osi=Linux"

According to the developers of cpufreqd, it has to be !Windows as we are trying to bypass something in the bios.

BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=7c78da4b-a063-46b6-b567-91aecbbfc3fb ro acpi_osi=!Windows 2006 quiet splash

---

### Post by P4man on 2011-02-08
Looks like you got the syntax wrong, as there have to be "" marks around "!Windows 2006". Can you check or post your  /etc/default/grub ?

---

### Post by qwertyjjj on 2011-02-08
> **P4man said:**
> Looks like you got the syntax wrong, as there have to be "" marks around "!Windows 2006". Can you check or post your  /etc/default/grub ?

GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2006\""

---

### Post by P4man on 2011-02-08
that looks correct. I just checked on my machine, and indeed the quotation marks dont show up in cat /proc/cmdline, even though you will find them in /boot/grub/grub.cfg, so it is correct

I guess the parameter isnt working. Time to try some others? Like acpi_osi=Linux.

---

### Post by qwertyjjj on 2011-02-08
> **P4man said:**
> that looks correct. I just checked on my machine, and indeed the quotation marks dont show up in cat /proc/cmdline, even though you will find them in /boot/grub/grub.cfg, so it is correct

I guess the parameter isnt working. Time to try some others? Like acpi_osi=Linux.

I turned off speedstep in the BIOS and now the computer stays at 1.73.
Will cpufreqd be able to swap the states between 800 and 1.73 ?
I tried selecting ondemand but it does nothing.

---

### Post by P4man on 2011-02-08
With speedstep disabled in the bios, I dont think you will be able to vary speeds. But are you SURE it wasnt working properly? With speedstep enabled and working, your cpu should run at 800 MHz unless you are running something really cpu intensive, like 'stress'.

```
stress --cpu 2
```

---

### Post by qwertyjjj on 2011-02-08
> **P4man said:**
> With speedstep disabled in the bios, I dont think you will be able to vary speeds. But are you SURE it wasnt working properly? With speedstep enabled and working, your cpu should run at 800 MHz unless you are running something really cpu intensive, like 'stress'.

```
stress --cpu 2
```

No, it's more a case of I had the computer set to performance, it stays permanently on 1.73 then 30mins later, the BIOS steps in at limits it to 800, I mean fully locks it to 800.
It even changes the bios_limit file from 1733000 to 800000.
If it was working it would not step it down when on performance mode and lock it.
When it works properly, it flickers between 800 and 1.73 as needed.
It's definitely a hardware issue, either a dodgy BIOS or a dodgy temperature setting. The fan even came on at full when the temp was only 40 and then it just stays on despite the temp dropping to 30.
So, I've had to turn speedstep off and get i8kmon running to control the fans.

---

