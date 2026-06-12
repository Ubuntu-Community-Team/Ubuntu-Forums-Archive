---
title: "laptop battery life worse on Dapper than WinXP"
date: 2006-06-07
forum: General Help
---

### Post by syxbit on 2006-06-07
anyone else noticed this
i have a Dell e1505 with a 9cell and get 2 1/2 hours in Dapper and about 4 in WinXP
anyone else have experience with this or know why

---

### Post by Maggot on 2006-06-07
Maybe all the power saving features aren't enabled/working?  I get 2 hours in both XP and Ubuntu 6.06

---

### Post by jimmyp on 2006-06-07
I have the same problem, I get about 4 hours in windows and 3 in dapper.  I only have the acpi-cpufreq module loaded for speed stepping.  I've read that it only changes the cycle speed, not the voltage supplied to the processor.  If windows lowers the voltage supplied to the processor, maybe that's why I get worse battery life.  In linux, my fan always runs.  In windows it usually does not run.  This could be another reason.

I don't know why we get worse battery life but it is very frustrating.

---

### Post by ericesque on 2006-06-07
Funny.  I did notice it felt shorter.  I didn't bother figuring out how long for each OS, but at least there are other people to confirm this.  I was just thinking about it this morning.

---

### Post by David Corrales on 2006-06-07
I've had this problem for a while too. Check that laptop mode is running and if you have an ati card, install the fglrx drivers and try using **aticonfig** to change it's power state.
**aticonfig --lsp** lists all the available modes
**aticonfig --set-powerstate #** switches the current running mode

---

### Post by jaymode on 2006-06-07
Do you use XGL/Compiz? If so that takes away a good amount of battery life as on mine it causes more cpu usage.

---

### Post by Patrick-Ruff on 2006-06-07
I don't use anything liek that and I get like a hour and a half less. :(.

---

### Post by ericesque on 2006-06-08
I tried setting my video to a lower powerstate... this is what I got :(

```
eric@ubuntu:~$ sudo aticonfig --set-powerstate 1
Password:
Error: Setting the requested power state failed.
Possible reasons:
  - running in dual head mode
  - thermal control is in effect
  - trying to set the current power state again
aticonfig: parsing the command-line failed.

```

any thoughts?

---

### Post by Patrick-Ruff on 2006-06-08
I'm not sure, I never got such an error.

---

### Post by MrKaiser on 2006-06-10
That sucks, because I was seriously considering using Linux for college on a Laptop and was wondering whether i was going to lose battery life. That sucks a lot since windows is really lame. Maybe I can virtualize Linux or something.

---

### Post by tsb on 2006-06-10
Are you Ubuntu or Kubuntu?  I have much better PM on Kubuntu.

---

### Post by nekr0z on 2006-06-10
Well, on my Fujitsu-Siemens AMILO M7400 the battery lifetime is much less than in Windows, too. And one more thing I've noticed is laptop gets very hot where the RAM and CPU modules are, much hotter than on WinXP...

---

