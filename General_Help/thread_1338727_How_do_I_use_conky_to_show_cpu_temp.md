---
title: "How do I use conky to show cpu temp"
date: 2009-11-26
forum: General Help
---

### Post by ardchoille42 on 2009-11-26
I'm using conky (1.6.1-0ubuntu4) in Ubuntu 9.04 and am attempting to do the following:
[LIST]
[*]Fetch CPU temperature and display it in fahrenheit
[*]Fetch nvidia card (GPU?) temperature and display it in fahrenheit
[/LIST]

I see a lot of articles that say you can do this with lm-sensors but that requires fiddling with kernel modules and I'd rather not do that.

I have gKRELLm installed and it fetches both temps without the need for lm-sensors (lm-sensors is not installed) so I figure I can do the same with conky but I just need to learn how to do it.

My system:
AMD Sempron 2800
nVidia GeForce 6200

The following line in conky works perfectly but displays the temp in celcius:
```
${color #9cc4ff}Temperature: ${color #e6e6e6}${execi 2 cat /sys/bus/pci/drivers/k8temp/000*/temp1_input | cut -c1,2}C
```

How do I display the CPU and nvidia GPU temps in fahrenheit in conky without having to use lm-sensors? If gKRELLm can do it, then I'm sure conky can do it too.

---

### Post by demosthenese on 2009-11-26
You could use execi to run the following line to give the temperature in degrees F.

acpi -t -f | cut -d, -f2-

You might have to fiddle with sed or tr to adjust the wording of the output.

Edit:

For Nvidia settings there is a thread here [http://bbs.archlinux.org/viewtopic.php?id=84346]("http://bbs.archlinux.org/viewtopic.php?id=84346")

which suggests:

nvidia-settings -q GPUCoreTemp | awk '{if (NR==2) {print ($4*9)/5+32}}'

---

### Post by ardchoille42 on 2009-11-26
> **demosthenese said:**
> You could use execi to run the following line to give the temperature in degrees F.

acpi -t -f | cut -d, -f2-

You might have to fiddle with sed or tr to adjust the wording of the output.

```
[~ @ 17:47:59]$ acpi -t -f | cut -d, -f2-
[~ @ 17:48:03]$ which acpi
/usr/bin/acpi
[~ @ 17:50:39]$ acpi
[~ @ 17:51:54]$
```
That doesn't work for some reason.

---

### Post by demosthenese on 2009-11-26
acpi with no parameters gives me my battery status. I guess if you are not running a laptop it may give a blank return. What does adding -t (thermal status) and -f (fahrenheit) switches give you?

Edit:

Doh! you tried that already.

---

### Post by ardchoille42 on 2009-11-26
> **demosthenese said:**
> You could use execi to run the following line to give the temperature in degrees F.

acpi -t -f | cut -d, -f2-

You might have to fiddle with sed or tr to adjust the wording of the output.

Edit:

For Nvidia settings there is a thread here [http://bbs.archlinux.org/viewtopic.php?id=84346]("http://bbs.archlinux.org/viewtopic.php?id=84346")

which suggests:

nvidia-settings -q GPUCoreTemp | awk '{if (NR==2) {print ($4*9)/5+32}}'

That nVidia line works perfectly! Thank you very much :)

---

### Post by ardchoille42 on 2009-11-26
> **demosthenese said:**
> acpi with no parameters gives me my battery status. I guess if you are not running a laptop it may give a blank return. What does adding -t (thermal status) and -f (fahrenheit) switches give you?

```
[~ @ 17:53:49]$ acpi -t
[~ @ 17:57:17]$ acpi -t -f
[~ @ 17:57:23]$
```
It returns nothing. Perhaps my hardware doesn't support acpi?

---

### Post by ardchoille42 on 2009-11-26
This line works perfectly for CPU temp, but it's in Celcius:
```
${color #9cc4ff}Temperature: ${color #e6e6e6}${execi 2 cat /sys/bus/pci/drivers/k8temp/000*/temp1_input | cut -c1,2}C
```

Is there a way to convert that to Fahrenheit? If I could convert that to Fahrenheit, this project would be complete.

---

### Post by demosthenese on 2009-11-26
Ok, if acpi isn't going to work, then you could pipe the line you are currently using through the same awk conversion I posted for the nvidia gpu temperature.

---

### Post by ardchoille42 on 2009-11-26
> **demosthenese said:**
> Ok, if acpi isn't going to work, then you could pipe the line you are currently using through the same awk conversion I posted for the nvidia gpu temperature.

This line returns "C"
```
${color #9cc4ff}CPU temp: ${color #e6e6e6}${execi 2 cat /sys/bus/pci/drivers/k8temp/000*/temp1_input | cut -c1,2 | awk '{if (NR==2) {print ($4*9)/5+32}}'}C
```

And this line returns "32C"
```
${color #9cc4ff}CPU temp: ${color #e6e6e6}${execi 2 cat /sys/bus/pci/drivers/k8temp/000*/temp1_input | cut -c1,2 | awk '{print ($4*9)/5+32}'}C
```

Both of which are incorrect. Do I have a typo somewhere?

---

### Post by ardchoille42 on 2009-11-26
> **demosthenese said:**
> Ok, if acpi isn't going to work, then you could pipe the line you are currently using through the same awk conversion I posted for the nvidia gpu temperature.

A friend of mine gave me some info about the awk command you used and I used that info to edit it to this:
awk '{print ($1*9)/5+32}'

which worked perfectly.

This line worked:
```
${color #9cc4ff}CPU temp: ${color #e6e6e6}${execi 2 cat /sys/bus/pci/drivers/k8temp/000*/temp1_input | cut -c1,2 | awk '{print ($1*9)/5+32}'}C
```

Problem solved :)

---

### Post by demosthenese on 2009-11-26
awk '{print ($1*9)/5+32}'

the $1 will work on the first 'word' instead of the fourth that was needed for the nvidia-settings query. I'm assuming that your existing command strips everything bar the temperature.

Edit:
You beat me to it.

---

### Post by ardchoille42 on 2009-11-26
> **demosthenese said:**
> awk '{print ($1*9)/5+32}'

the $1 will work on the first 'word' instead of the fourth that was needed for the nvidia-settings query. I'm assuming that your existing command strips everything bar the temperature.

Edit:
You beat me to it.

Thank you very much for your help. I wouldn't have arrived where I did if you hadn't got the ball rolling :)

---

