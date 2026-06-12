---
title: "Laptop turns off as soon as I take the power lead out"
date: 2010-12-24
forum: General Help
---

### Post by J-E-N-O-V-A on 2010-12-24
This has been a persistent problem with my laptop. I've gone through three batteries now! Any ideas?

"cat /proc/acpi/battery/BAT1/info"
returns:
```
present:                 yes
design capacity:         48400 mWh
last full capacity:      48774 mWh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 4840 mWh
design capacity low:     2420 mWh
cycle count:		  0
capacity granularity 1:  484 mWh
capacity granularity 2:  484 mWh
model number:            F5---22
serial number:            
battery type:            LIon
OEM info:                ASUSTEK
```

---

### Post by Quackers on 2010-12-24
I know it refers to Lucid Lynx really but have you seen the last item in post #1 in this thread?
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by J-E-N-O-V-A on 2010-12-24
> **Quackers said:**
> I know it refers to Lucid Lynx really but have you seen the last item in post #1 in this thread?
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

It still switched off despite being fully charged. After rebooting the boxed was checked.

Fortunately the boot time is so small that this problem hasn't drive me *clinically* insane :D

---

### Post by Quackers on 2010-12-24
If you boot up the laptop without the power cord does it work?

---

### Post by J-E-N-O-V-A on 2010-12-24
> **Quackers said:**
> If you boot up the laptop without the power cord does it work?
Nope, it doesn't even turn on. It behaves as if there is no battery.

---

### Post by Quackers on 2010-12-24
That has only happened to me once and the battery was finished. I was annoyed because I very rarely used the battery and kept it plugged in. However, it turns out that that was the problem. I have since been told to use the battery until it's about to turn off the laptop and then recharcge it fully, once a month. 
My first battery lasted 9 months. This present battery has lasted almost 3 years.

---

### Post by J-E-N-O-V-A on 2010-12-24
> **Quackers said:**
> That has only happened to me once and the battery was finished. I was annoyed because I very rarely used the battery and kept it plugged in. However, it turns out that that was the problem. I have since been told to use the battery until it's about to turn off the laptop and then recharcge it fully, once a month. 
My first battery lasted 9 months. This present battery has lasted almost 3 years.

This one lasted me about two months from brand new!

---

### Post by linden940 on 2010-12-24
He said he had 3 battery's and it happened three times. could it be where the battery goes there is a lose connector thats not as it should?

---

### Post by linden940 on 2010-12-24
> **J-E-N-O-V-A said:**
> This one lasted me about two months from brand new!

Can you take it back?

---

### Post by Quackers on 2010-12-24
I think they are guaranteed for 6 months.

---

### Post by linden940 on 2010-12-24
> **Quackers said:**
> I think they are guaranteed for 6 months.

lol depends on where you get it....if you know how to play walmart its guaranteed until they stop selling that item and or it comes in another color lmao

---

### Post by pikachu714 on 2010-12-24
There is probably something wrong with the computer's hardware. If you don't care about using the battery then just keep the power in. If you always keep the power in, it eventually will ruin the battery.

---

### Post by Quackers on 2010-12-24
It could be a short or a drain on the battery. If you don't use sleep or hibernate you could disconnect the battery every night. In fact if it's a Vaio there is a known battery drain on some models.

---

### Post by linden940 on 2010-12-24
> **Quackers said:**
> It could be a short or a drain on the battery. If you don't use sleep or hibernate you could disconnect the battery every night. In fact if it's a Vaio there is a known battery drain on some models.

I was thinking of there being a short but I dont think so. IF there was he should know about it by now. They battery is alot of power...a small short would not stay a small short lol

when you take the battery out are the "pins" looking good or lose/dirty?

---

### Post by J-E-N-O-V-A on 2010-12-24
> **linden940 said:**
> I was thinking of there being a short but I dont think so. IF there was he should know about it by now. They battery is alot of power...a small short would not stay a small short lol

when you take the battery out are the "pins" looking good or lose/dirty?

They look fine, it could be shorted though. I will try to return it.

---

