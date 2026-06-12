---
title: "computer  shutdown"
date: 2010-01-24
forum: General Help
---

### Post by dato1989 on 2010-01-24
sorry first of all i didnot know where to put this thread do i decided put here
i explain now my situation i have dual boot win7/ubuntu 9.10 both systems have been booting fine but unfortunately now is problem and very weired problem of course anybody thinks that problem is about ubuntu or win7 booting but no problem is very strange when i power on computer it shows me grub menu (grub2) but there is three case 1) computer shuting down without any error imediately 2)i choose ubuntu and almost with 99% it booted but when i choose win7 there is a big chance that computer shutdown for example today i was in ubuntu i have restarted and choose win7 it start booting and suddenly it shuted down then try again also this event repeat and after a few try it was booted win7 i dont know what is cause of this problem?cpu?memory?motherboard or this is typical software and hardware problem?i saw this situation a few days ago to so i am surprised please help me i need it very much (and first of all if i have written badly i mean english then dont be angry for this please )i will be happy if somebody help me
david

---

### Post by dato1989 on 2010-01-24
[QUOTE=dato1989;8716625]sorry first of all i didnot know where to put this thread do i decided put here
i explain now my situation i have dual boot win7/ubuntu 9.10 both systems have been booting fine but unfortunately now is problem and very weired problem of course anybody thinks that problem is about ubuntu or win7 booting but no problem is very strange when i power on computer it shows me grub menu (grub2) but there is three case 1) computer shuting down without any error imediately 2)i choose ubuntu and almost with 99% it booted but when i choose win7 there is a big chance that computer shutdown for example today i was in ubuntu i have restarted and choose win7 it start booting and suddenly it shuted down then try again also this event repeat and after a few try it was booted win7 i dont know what is cause of this problem?cpu?memory?motherboard or this is typical software and hardware problem?i saw this situation a few days ago to so i am surprised please help me i need it very much (and first of all if i have written badly i mean english then dont be angry for this please )i will be happy if somebody help me
david








please help

---

### Post by teresaejunior on 2010-01-24
> **dato1989 said:**
> sorry first of all i didnot know where to put this thread do i decided put here
i explain now my situation i have dual boot win7/ubuntu 9.10 both systems have been booting fine but unfortunately now is problem and very weired problem of course anybody thinks that problem is about ubuntu or win7 booting but no problem is very strange when i power on computer it shows me grub menu (grub2) but there is three case 1) computer shuting down without any error imediately 2)i choose ubuntu and almost with 99% it booted but when i choose win7 there is a big chance that computer shutdown for example today i was in ubuntu i have restarted and choose win7 it start booting and suddenly it shuted down then try again also this event repeat and after a few try it was booted win7 i dont know what is cause of this problem?cpu?memory?motherboard or this is typical software and hardware problem?i saw this situation a few days ago to so i am surprised please help me i need it very much (and first of all if i have written badly i mean english then dont be angry for this please )i will be happy if somebody help me
david

Your cpu must be overheating, it shuts down not to melt pieces. Wait for it to cool, start the computer again. In linux, get the the temperature by running the command in a terminal:

grep -o "[0-9]*" /proc/acpi/thermal_zone/T*/temperature

and paste this output here for me.

---

### Post by dato1989 on 2010-01-24
> **teresaejunior said:**
> Your cpu must be overheating, it shuts down not to melt pieces. Wait for it to cool, start the computer again. In linux, get the the temperature by running the command in a terminal:

grep -o "[0-9]*" /proc/acpi/thermal_zone/T*/temperature

and paste this output here for me.



grep -o "[0-9]*" /proc/acpi/thermal_zone/T*/temperature
here is the output
/proc/acpi/thermal_zone/TZ0/temperature:76
/proc/acpi/thermal_zone/TZ1/temperature:75
/proc/acpi/thermal_zone/TZ3/temperature:60
/proc/acpi/thermal_zone/TZ4/temperature:34
/proc/acpi/thermal_zone/TZ5/temperature:80

---

### Post by teresaejunior on 2010-01-24
You have 5 sensors around your motherboard. 76, 75, 80 are high temperatures, is it a laptop? check which process are using most of the cpu running 'top' in the terminal.

---

### Post by dato1989 on 2010-01-24
> **teresaejunior said:**
> You have 5 sensors around your motherboard. 76, 75, 80 are high temperatures, is it a laptop? check which process are using most of the cpu running 'top' in the terminal.
yes it is laptop
i will see
maximum usage is 13%  process sendmail-mta

---

### Post by teresaejunior on 2010-01-24
13 is not that much, maybe the fans are blocked with dust. This happened to me... I had to open by moving the keyboard upwards. and clean the fans. Also you must then change the paste which covers the cpu. Without care you can damage components. You should monitor more frequently CPU usage placing conky in your desktop. Search the forums for a conky tutorial, there are a lot.

---

### Post by dato1989 on 2010-01-24
> **teresaejunior said:**
> 13 is not that much, maybe the fans are blocked with dust. This happened to me... I had to open by moving the keyboard upwards. and clean the fans. Also you must then change the paste which covers the cpu. Without care you can damage components. You should monitor more frequently CPU usage placing conky in your desktop. Search the forums for a conky tutorial, there are a lot.
thanks  very much yes i know with laptop  it is a bit  difficult  to do something  then   pc  no problem i    will  shutdonw computer    sometimes   ok thanks a lot  
good luck

---

### Post by teresaejunior on 2010-01-24
> **dato1989 said:**
> thanks  very much yes i know with laptop  it is a bit  difficult  to do something  then   pc  no problem i    will  shutdonw computer    sometimes   ok thanks a lot  
good luck

if you install cpufrequtils, you can run a command to decrease cpu speed, reducing temperature. In my conky I have placed the temperature, so you'll always know how much is the temperature. If it gets hot, you run that command. If interested, let me know and we'll try that!

---

