---
title: "Computer Overheating!(please help)"
date: 2011-02-26
forum: General Help
---

### Post by Rossbeanerman on 2011-02-26
With windows i was able to leave my computer on my lap and go for hours on end its never overheated on me and it still doesnt with windows, but with ubuntu it will last around 30-1h then it will overheat or even faster if i do anything like play a game or watch flash.. any ideas? and its not a problem with the new flash release because last year when i had ubuntu 10.04 it did the same thing (im on 10.10)

---

### Post by cascade9 on 2011-02-26
Tell us what compuer you are using.

---

### Post by aussie_g on 2011-02-26
Does the same thing on my laptop, after searching through page after page of people saying the same thing - it seems that ubuntu is not setup to handle a laptop cpu fan.

Mine never comes on after the splash screen during boot, mine is a Toshiba u505, but I have seen many different laptops listed with the same problem.

---

### Post by Rossbeanerman on 2011-02-26
o sorry um toshiba satellite l3000D 2gb ram amd athlon 64 x2
[http://us.toshiba.com/computers/laptops/satellite/L300/L300D-ST3503](http://us.toshiba.com/computers/laptops/satellite/L300/L300D-ST3503)

---

### Post by Quackers on 2011-02-26
> **aussie_g said:**
> Does the same thing on my laptop, after searching through page after page of people saying the same thing - it seems that ubuntu is not setup to handle a laptop cpu fan.

Mine never comes on after the splash screen during boot, mine is a Toshiba u505, but I have seen many different laptops listed with the same problem.

That depends on the laptop (and quite often ACPI) - mine is fine. What make of laptop? Toshiba seem to have the worst ACPI problems, it seems.

---

### Post by aussie_g on 2011-02-26
> **Quackers said:**
> That depends on the laptop (and quite often ACPI) - mine is fine. What make of laptop? Toshiba seem to have the worst ACPI problems, it seems.


That is quite possible, a majority of people seemed to be listing a toshiba as their machine...

There has to be a way to release the control of the fan back to bios, until the acpi services start, the fan is just fine.

---

### Post by Rossbeanerman on 2011-02-26
well my next attempt at fixing will be installing 32bit..i dont see how it could help but its worth a try..

---

### Post by Quackers on 2011-02-26
You can use the boot prompt "acpi=off", but that can have an effect on the fans too (ie not running at all), but there are other prompts too - like noapic and nolapic, that can be tried.
Also, you should identify which fans are or aren't running. It can be the system fan, or, more likely the graphics fan.

---

### Post by Rossbeanerman on 2011-02-26
how would i go about finding out witch fans are running??

---

### Post by Quackers on 2011-02-26
That's a good question, but, sadly I don't know (not having had any problems). If you know where the specific fans are within the case, you could listen carefully whilst the machine is running - or open it up - but extreme caution would be needed if you do that.
I'm sure there is software that can tell you which fans are running. Maybe google?

---

### Post by Rossbeanerman on 2011-02-26
ahhh i couldn't find anything im kinda a noob.. somewhat familiar with ubuntu, i wish there was a just a simple fix its not easy trying out ubuntu but every 30 mins your computer crashes.. -.-

---

### Post by Quackers on 2011-02-26
If it's crashing because it's overheating, it's not a good idea to use it. You could burn something out! That could be expensive! If you are dual-booting with Windows, I would advise using Windows to search for a fix.

---

