---
title: "sensors-detect fails to find anything"
date: 2006-03-26
forum: General Help
---

### Post by s|k on 2006-03-26
I have lm-sensors installed and I run sensors-detect with both sudo and from root and it fails to detect anything. When I run this machine on windows xp I can see my cpu temperature, so I know I have the sensors. What am I doing wrong?

Thanks

---

### Post by bluevoodoo1 on 2006-03-26
you have lm-sensors installed... what happens if you type

```
sensors
```

in a terminal?

---

### Post by s|k on 2006-03-26
[QUOTE=bluevoodoo1]you have lm-sensors installed... what happens if you type

```
sensors
```

in a terminal?[/QUOTE]
I get:

```
eeprom-i2c-0-52
Adapter: SMBus I801 adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       1024

eeprom-i2c-0-51
Adapter: SMBus I801 adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       1024

eeprom-i2c-0-50
Adapter: SMBus I801 adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       1024

```

What I want is CPU temp. I can't seem to get it. If try the add 'Hardware Sensors' to the panel, it says no sensors detected.

---

### Post by nanotube on 2006-03-26
what is the hardware you are running on? i am on a dell laptop, for example, and i have to install "i8k" stuff to get it to detect my sensors. maybe there is something like that for your hardware, too?

---

### Post by henriquemaia on 2006-03-26
Have you tried this[ HowTo]("http://ubuntuforums.org/showthread.php?t=2780&highlight=sensors")?

It worked great with me, even in Dapper (in the thread you'll get some ideas if you get stuck, but in Breezy I do not think you'll have problems (I didn't have).

---

### Post by s|k on 2006-03-26
[QUOTE=nanotube]what is the hardware you are running on? i am on a dell laptop, for example, and i have to install "i8k" stuff to get it to detect my sensors. maybe there is something like that for your hardware, too?[/QUOTE]
I have an ASUS P5GD1 motherboard and Intel P4 HT 3Ghz. :/

What is that in your avatar?

---

### Post by s|k on 2006-03-26
[QUOTE=henriquemaia]Have you tried this[ HowTo]("http://ubuntuforums.org/showthread.php?t=2780&highlight=sensors")?

It worked great with me, even in Dapper (in the thread you'll get some ideas if you get stuck, but in Breezy I do not think you'll have problems (I didn't have).[/QUOTE]
No that How to didn't work for me. :(

---

