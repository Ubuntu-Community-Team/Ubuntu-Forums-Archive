---
title: "Optimzing Ubuntu 11.04 for Laptops"
date: 2011-06-10
forum: General Help
---

### Post by ShadedCS on 2011-06-10
I have had ubuntu for about 2-3 weeks now, and I am having a problem with the battery. Was ubuntu made for running on desktops, because whenever I unplug my laptop from the charger and the battery is not at 100%, it dies within 10 seconds. I was wondering if there was a way I could optimize 11.04 Natty Narwhal for laptops?

shadedCS

---

### Post by StrayEddy on 2011-06-10
Get some information on your battery life by typing this command:

/proc/acpi/battery/BAT0$ cat info

EDIT: If it dies in 10 seconds, that means there is a real problem with your battery first.

---

### Post by ShadedCS on 2011-06-10
No do.

```

bryan@bryan-Vostro-1520:~$ /proc/acpi/battery/BAT0$ cat info
bash: /proc/acpi/battery/BAT0$: No such file or directory
bryan@bryan-Vostro-1520:~$ /proc/acpi/battery/BATO$ cat info
bash: /proc/acpi/battery/BATO$: No such file or directory
bryan@bryan-Vostro-1520:~$ 

```

---

### Post by ruffEdgz on 2011-06-10
I think he means:
```

cd /proc/acpi/battery/BAT0/
cat ./info

```

---

### Post by ShadedCS on 2011-06-10
Still no beans

```

bryan@bryan-Vostro-1520:~$ cd /proc/acpi/battery/BATO/
bash: cd: /proc/acpi/battery/BATO/: No such file or directory
bryan@bryan-Vostro-1520:~$ cd /proc/acpi/battery/BATO/cat ./info
bash: cd: /proc/acpi/battery/BATO/cat: No such file or directory
bryan@bryan-Vostro-1520:~$ 
```

EDIT: Went searching in file system, its BAT1 for me

```

present:                 yes
design capacity:         86580 mWh
last full capacity:      25470 mWh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 1273 mWh
design capacity low:     764 mWh
cycle count:          0
capacity granularity 1:  264 mWh
capacity granularity 2:  3780 mWh
model number:            
serial number:           11
battery type:            Lion
OEM info:                Dell

```

---

### Post by ShadedCS on 2011-06-14
bump...

---

### Post by mister_playboy on 2011-06-14
How old is your computer?  A battery that goes from 100% to 0% in less than a minute is a battery that has reached the end of its life... nothing to be done there except buy a new one.

The most recent Linux kernels do indeed have a regression that seems to cause much greater power usage than previously (30%-40%), but that still would not cause the specific behavior you are seeing.

---

### Post by ShadedCS on 2011-06-14
When the battery is at a full 100%, it acts normally, I can do around without the charger for a good 2 hours of work. Its just when the battery is not at a full 100%, unplugging it makes it shut off within 10 seconds.

---

### Post by Alastair Rae on 2011-09-14
I have a new laptop with a battery that lasts 3-4 hrs on windows. But it dies without warning after about 30 mins on 11.04.

---

### Post by LMP900 on 2011-09-14
It might be an issue with calibration. Perhaps the OS thinks that the battery is at a certain level and needs to hibernate or shut down, when there is actually plenty of juice left.

---

### Post by Slim Odds on 2011-09-14
Once again, how old is this battery?
```
present:                 yes[COLOR=Red]
design capacity:         86580 mWh
last full capacity:      25470 mWh[/COLOR]
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 1273 mWh
design capacity low:     764 mWh
cycle count:          0 
capacity granularity 1:  264 mWh 
capacity  granularity 2:  3780 mWh 
model number: 
serial number:            11 
battery type:            Lion 
OEM info:                Dell
```That part in red above indicates a serious problem. You last full capacity is only about 30% of the original capacity.

You need a new battery.

---

