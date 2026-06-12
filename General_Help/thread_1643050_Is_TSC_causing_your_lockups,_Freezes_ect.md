---
title: "Is TSC causing your lockups, Freezes ect??"
date: 2010-12-11
forum: General Help
---

### Post by coffee412 on 2010-12-11
**I am starting this thread for those that are experiencing system lockups, Mouse freezes, Video problems, USB problems and such.** 

The reason I am writing this is that I think I have found a possible cure to probably 75 percent of those experiencing weird problems with their Ubuntu install. I have been installing Ubuntu on a wide range of computers and have experienced these problems and they actually lead me back to one fix that solved them all. Of course, Your mileage may vary but I would love to hear from you if this fixed your problem.

I have found that an error occurs and is listed in your logs (/var/log/messages) that can be overlooked. This deals with the TSC Clocksource.

The TSC Clocksource from what I have read is a time stamp created by the cpu to determine time. Sometimes - and I dont know if this is a hardware or software issue - it becomes unstable and causes a whole range of system problems. Just do this to be sure this is not causing your problem:

Check your log file for "Clocksource tsc unstable ..." . If you do find this statement then you need to change your clocksource. There are two files to look at.

> /sys/devices/system/clocksource/clocksource0/current_clocksource

/sys/devices/system/clocksource/clocksource0/available_clocksource
Determine what your current clocksource is and also what clocksources are available on your system. Then you need to edit your grub conf file and tell linux what clocksource to use with the line here:

acpi=<clocksource>

I have seen the following clocksources available on systems to a varying degree: tsc, acpi_pm, jiffies, hpet

I had a Dell Dimention install that the mouse would lockup intermittenly along with anything else on a USB port. I checked the current clocksource and it was set to acpi_pm. Then I looked at available_clocksources and acpi_pm was the only one available. Therefore, I pretty much replaced the computer as I had no other clocksource to pick from. But on alot of systems checking this and changing it solved alot of issues.

Just edit your /etc/default/grub file and add the line to your boot options and run update-grub. Then reboot. See if that fixes it.

Im currently running Fedora and it works the same way. Im pretty sure this is going to be standard with other flavors of linux as far as the clocksource files/locations and fixes are. The real determining factors are 1- The error message in your log file, 2- Hopefully an alternate clocksource being available.

Iam interested in replies that include what Manufactuer and model number your computer is(i.e. compaq, dell ect), If its a custom built what motherboard and model number you have if you can.

Thanks,

Coffee :D

---

### Post by dcstar on 2010-12-11
> **coffee412 said:**
> **I am starting this thread for those that are experiencing system lockups, Mouse freezes, Video problems, USB problems and such.** 

The reason I am writing this is that I think I have found a possible cure to probably 75 percent of those experiencing weird problems with their Ubuntu install. I have been installing Ubuntu on a wide range of computers and have experienced these problems and they actually lead me back to one fix that solved them all. Of course, Your mileage may vary but I would love to hear from you if this fixed your problem.

I have found that an error occurs and is listed in your logs (/var/log/messages) that can be overlooked. This deals with the TSC Clocksource.
.........

If in fact this does fix any systems, people should be reporting it as a kernel bug otherwise **it may never get fixed properly**.

---

### Post by 3rdalbum on 2010-12-11
Manually check your RAM (by taking some of it out and seeing if the issue still occurs) before fiddling with this clocksource stuff. Bad RAM is a more likely cause.

---

### Post by coffee412 on 2010-12-11
> **3rdalbum said:**
> Manually check your RAM (by taking some of it out and seeing if the issue still occurs) before fiddling with this clocksource stuff. Bad RAM is a more likely cause.

Well good luck playing with your RAM when you have a message like this in your logs:

> [   76.680037] Clocksource tsc unstable (delta = -175079518 ns)

---

