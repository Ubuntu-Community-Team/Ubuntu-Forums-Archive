---
title: "Reading temperature sensors"
date: 2011-10-25
forum: General Help
---

### Post by Lars Noodén on 2011-10-25
How can the hardware's temperature sensors be read?  This would be either via Unity or via the regular bash shell.

---

### Post by Mark Phelps on 2011-10-25
I don't have an answer, but if you're looking for code, the system monitor gkrellm comes in source version as well as package.  You could download the source and see how it does it.

---

### Post by 3rdalbum on 2011-10-25
Install the lm-sensors package and run the command:

```
sudo sensors-detect
```

Basically, press y (yes) to everything. Then whenever you want to look at the sensors, run this command in the terminal:

```
sensors
```

Any other programs that display sensor information use the 'sensors' program as well.

---

### Post by BazookaAce on 2011-10-25
If you're using Gnome Shell, you can get the temperature in the statusbar like this: 

[IMG]http://img824.imageshack.us/img824/7110/sensorcropped.png[/IMG]

```
sudo apt-get install lm-sensors
```

then..

```
cd
git clone https://github.com/xtranophilist/gnome-shell-extension-cpu-temperature.git
mkdir -p ~/.local/share/gnome-shell/extensions/temperature@xtranophilist
cp gnome-shell-extension-cpu-temperature/* ~/.local/share/gnome-shell/extensions/temperature@xtranophilist
```

---

### Post by Lars Noodén on 2011-10-25
> **3rdalbum said:**
> Install the lm-sensors package... run this command in the terminal:
```
sensors
```

Ok.  Which values are legit and which are not?  I ask because part of the computer is very hot to the touch but the fan is not running.  When I reboot into OS X the fan starts up heavily first thing.

```

applesmc-isa-0300
Adapter: ISA adapter
Left side  : 1996 RPM  (min = 2000 RPM)
Right side : 1999 RPM  (min = 2000 RPM)
TB0T:         +34.5°C  
TB1T:         +34.5°C  
TB2T:         +32.2°C  
TC0C:         +68.2°C  
TC0D:         +64.5°C  
TC0E:         +67.8°C  
TC0F:         +69.5°C  
TC0P:         +56.0°C  
TC1C:         +67.0°C  
TC2C:         +76.0°C  
TC3C:         +70.0°C  
TC4C:         +66.0°C  
TCFC:          +0.0°C  
TCGC:         +75.0°C  
TCSA:         +63.0°C  
TCTD:        +255.8°C  
TG0D:         +70.0°C  
TG0P:         +63.5°C  
THSP:         +41.0°C  
TP0P:         +54.2°C  
TPCD:         +58.0°C  
TW0P:        +129.0°C  
Th1H:         +57.8°C  
Th2H:         +55.5°C  

```

---

### Post by cryptotheslow on 2011-10-25
```
TCTD:        +255.8°C
```^^^ That's the hot one :D

On a serious note - there doesn't seem to be a great deal of consistency between boards even with the same chipsets in use. Seems to be down to how the board manufacturer chooses to implement the sensors.

What's the motherboard?

You may have some joy googlying "lmsensors applesmc-isa-0300"


ADD: Any use? [http://ubuntuforums.org/archive/index.php/t-1754431.html](http://ubuntuforums.org/archive/index.php/t-1754431.html)

---

### Post by Lars Noodén on 2011-11-07
> **cryptotheslow said:**
> What's the motherboard?

MacBookPro8,2.  Which program do I use to look up the details?

---

