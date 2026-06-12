---
title: "OverHeating Ubuntu"
date: 2012-04-24
forum: General Help
---

### Post by nimzter on 2012-04-24
Hello X Brothers. :rolleyes:

Laptop ASUS K52JR. My OS is Ubuntu 11.10 with KDE (installed kubuntu-desktop), and today when I booted the OS the temp was showing 71 deegres . My question is... Exists a SW for Linux that can help cooling the Processor? When I was using Win 7, the temperature was 44 - 60. 

I was searching for some solutions like 'acpi' and coretemo modules but no change....If anyone can help I'll appreciate it. 

Thanks, 

Best Regards.

---

### Post by techsupport on 2012-04-24
> **nimzter said:**
> Hello X Brothers. :rolleyes:

Laptop ASUS K52JR. My OS is Ubuntu 11.10 with KDE (installed kubuntu-desktop), and today when I booted the OS the temp was showing 71 deegres . My question is... Exists a SW for Linux that can help cooling the Processor? When I was using Win 7, the temperature was 44 - 60. 

I was searching for some solutions like 'acpi' and coretemo modules but no change....If anyone can help I'll appreciate it. 

Thanks, 

Best Regards.

That seems kinda hot. Have you checked your BIOS settings to manually configure it yet?

---

### Post by nimzter on 2012-04-24
In the BIOS configuration there is not available configuration about the Heat. It's litle bit annoying becouse of the manufacturer...

---

### Post by techsupport on 2012-04-24
> **nimzter said:**
> In the BIOS configuration there is not available configuration about the Heat. It's litle bit annoying becouse of the manufacturer...

You should be able to manually change the BIOS settings for the CPU cooler fan. You probably have it set to auto and that is why it is overheating. 

:guitar:

---

### Post by nimzter on 2012-04-24
:) As i said before, there is no configuration about the CPU cooler fan. Nothing...

---

### Post by techsupport on 2012-04-24
> **nimzter said:**
> :) As i said before, there is no configuration about the CPU cooler fan. Nothing...

And the last time your CPU was cooler was when you had Windows installed? I remember there being a CPU cooler issue with Natty. I thought they fixed that by now.  Create a live stick of 10.10 and boot from that Flash Drive to check the temp of your CPU to see if that could be it. We might be able to go from there.

---

### Post by nimzter on 2012-04-24
> **nimzter said:**
> Hello X Brothers. :rolleyes:

Laptop ASUS K52JR. My OS is Ubuntu 11.10 with KDE (installed kubuntu-desktop), and today when I booted the OS the temp was showing 71 deegres . My question is... Exists a SW for Linux that can help cooling the Processor? When I was using Win 7, the temperature was 44 - 60. 

I was searching for some solutions like 'acpi' and coretemo modules but no change....If anyone can help I'll appreciate it. 

Thanks, 

Best Regards.

Read it again...

---

### Post by layers on 2012-04-24
Just to let you know - it happens to me too. If I load openSUSE for instance, the fan sounds like it is preparing to kill me... but with Ubuntu, it's quiet.

---

### Post by nimzter on 2012-04-24
> **layers said:**
> Just to let you know - it happens to me too. If I load openSUSE for instance, the fan sounds like it is preparing to kill me... but with Ubuntu, it's quiet.

Are you using KDE ?

---

### Post by MonkeyPaw on 2012-04-24
What does your CPU usage look like when your fan spins up? Is it at 100%?

---

### Post by thenixedreport on 2012-04-24
This is for Hardy Heron, but maybe it could be of use to you:

[http://manpages.ubuntu.com/manpages/hardy/man8/fancontrol.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/fancontrol.8.html)

Let me know if that helps.

---

### Post by nimzter on 2012-04-25
> **MonkeyPaw said:**
> What does your CPU usage look like when your fan spins up? Is it at 100%?

The four threads are between 0 and 5 % . Maybe It's something related with the AMD GPU Driver.

---

### Post by nimzter on 2012-04-25
> **thenixedreport said:**
> This is for Hardy Heron, but maybe it could be of use to you:

[http://manpages.ubuntu.com/manpages/hardy/man8/fancontrol.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/fancontrol.8.html)

Let me know if that helps.

Well ... when I execute as root "pwmconfig" says: 

# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

....

---

### Post by layers on 2012-04-25
> **nimzter said:**
> Are you using KDE ?

At first I thought it was the KDE, but then I tried Kubuntu, and it was not the KDE. Something in the code...:-k

---

### Post by MonkeyPaw on 2012-04-25
Have you checked for a BIOS update?

---

