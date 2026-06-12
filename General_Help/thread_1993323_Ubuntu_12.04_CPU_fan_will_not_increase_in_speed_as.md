---
title: "Ubuntu 12.04: CPU fan will not increase in speed as cpu temp increases."
date: 2012-06-01
forum: General Help
---

### Post by PlastikSpork on 2012-06-01
I have Ubuntu 12.04 installed within Windows 7. I noticed that my Laptop (Toshiba Satellite L305D-S5934) is running unusually hot in Ubuntu compared to Windows 7. I decided to run a CPU stress test (Prime95) in Windows 7 and in Ubuntu to see what the highest temperature would be.

Windows 7 = 161F or 72C

Ubuntu 12.04 = 203F or 95C

I did notice that as the temperature increased in Windows 7 so did the fan speed, but in Ubuntu the fan speed does not increase with temperature. Any suggestions on how to fix this?

---

### Post by Redblade20XX on 2012-06-01
Did you get the cpu temps from linux? Can you install lm-sensors and see what temps you get?

-Red

---

### Post by athampan on 2012-06-02
I too have this problem. Mine is a dell inspiron N5010 with an i5 cpu @ 2.67 GHz.   Right now, I make do with using the indicator-cpufreq applet and underclock the cpu to the minimum possible level of 1.20 GHz ... this keeps my cpu temp at about 78 C (two other applets that are useful are the psensor applet and jupiter).

---

### Post by LinGNUbie on 2012-06-02
There is a boot option that may be added to grub that could help solve the issue:

In /etc/default/grub add the additional option acpi.power_nocheck=1 OR acpi_osi=linux, save and run update-grub, reboot and recheck the issue.

This did the trick on one of my machines, albeit an older one.

---

### Post by PlastikSpork on 2012-06-02
> **LinGNUbie said:**
> There is a boot option that may be added to grub that could help solve the issue:

In /etc/default/grub add the additional option acpi.power_nocheck=1 OR acpi_osi=linux, save and run update-grub, reboot and recheck the issue.

This did the trick on one of my machines, albeit an older one.

I updated Grub with acpi_osi=linux and acpi.power_nocheck=1 and ran the stress test again with each setting.

acpi.power_nocheck=1 = 88 C or 190 F

acpi_osi=linux = 91 C or 196 F

So 190 F is an improvement over 203 F, but it is still way hotter compared to Windows 7 @ 161 F.


I used Psensor to get the temp readings.

---

### Post by LinGNUbie on 2012-06-02
The extra may be due to the GUI, as I know its creates a good load on processes.

---

### Post by Mark Phelps on 2012-06-03
> **LinGNUbie said:**
> The extra may be due to the GUI, as I know its creates a good load on processes.

And what do you think they're using in Win7 -- command line?

Linux has known kernel bugs for some time that cause it to not throttle back the processor when idle.  This causes some PCs, especially laptops, to overheat when running Ubuntu.

To the OP:  you can try installing Jupiter to see if that helps:

[http://ubuntuforums.org/showthread.php?t=1854019]("http://ubuntuforums.org/showthread.php?t=1854019")

---

### Post by LinGNUbie on 2012-06-03
> **Mark Phelps said:**
> And what do you think they're using in Win7 -- command line?

How about reading with the flow of what has been posted instead of just making smarty comments., then posting essentially the same comment as I made. May be the reason support is getting hard to come by from the forums. Nice heads up on the Jupitor, though, why not just say that.

---

