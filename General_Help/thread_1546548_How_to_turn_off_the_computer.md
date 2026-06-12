---
title: "How to turn off the computer?"
date: 2010-08-05
forum: General Help
---

### Post by saidbakr on 2010-08-05
Hi,
I currently use Ubuntu 10.04. I don't able make the computer to be turned off! The Shut Down option in the Ubuntu's menu, only, make the system to be Shut Down. In other word, I just see the Ubuntu Screen without turning off the monitor and stopping the computer. i.e the fan and the green power LED are remaining on.

I have another Computer using Ubuntu too, but it able to be turned off completely, so I wonder why my current computer does not able to be the same as the other computer.

I merely remember that I have seen an answer related to this question, it was some modifications to some config files, but I don't remeber how?!

Another related question, if there a modification to some system configs to allow the computer to be turned off, Does it dangerous to my computer, specially, Hard disk?

---

### Post by sydbat on 2010-08-05
> **saidbakr said:**
> Hi,
I currently use Ubuntu 10.04. I don't able make the computer to be turned off! The Shut Down option in the Ubuntu's menu, only, make the system to be Shut Down. In other word, I just see the Ubuntu Screen without turning off the monitor and stopping the computer. i.e the fan and the green power LED are remaining on.

I have another Computer using Ubuntu too, but it able to be turned off completely, so I wonder why my current computer does not able to be the same as the other computer.

I merely remember that I have seen an answer related to this question, it was some modifications to some config files, but I don't remeber how?!

Another related question, if there a modification to some system configs to allow the computer to be turned off, Does it dangerous to my computer, specially, Hard disk?I had this problem a number of years ago with XP. Turned out to be faulty hardware.

Also, found this easily - [http://ubuntuforums.org/showpost.php?p=9244282&postcount=2](http://ubuntuforums.org/showpost.php?p=9244282&postcount=2)

---

### Post by saidbakr on 2010-08-05
I could able to confirm that I found a solution for this issue for my computer in the past, but I am not able to remember how!:(

---

### Post by mojo risin on 2010-08-05
Hi if only the pc is still running with everything shut off it may help to press the power button for ten seconds. This shuts normally PC's and laptops down.

---

### Post by saidbakr on 2010-08-05
Yes it is the no choice option. However, I have some troubles with the power button and I reconfigured the computer's BIOS to a power option that allow it resume after power failure, In other word it turns on after plug the cord to electrical source.

---

### Post by saidbakr on 2010-08-08
Hi,

I found the solution.
1- From BIOS -> Power Management -> Enable ACPI
2- In  /etc/default/grub add acpi=force to:
        GRUB_CMDLINE_LINUX_DEFAULT to be something like:
GRUB_CMDLINE_LINUX_DEFAULT="acpi=force quiet splash"
3- run update-grub
4- restart

The next time the computer will do complete shutdown, in other word, the power supply will cut off the current after the system halt.

However, there is new problem. It is conflict problem. I run libsensors to get data about system temprature, cpu tempreature and fan RPM, when ACPI is force this application generates errors and only one sensor display data, CPU sensor via ACPI. The attached screenshot demonstrates what I get.

---

