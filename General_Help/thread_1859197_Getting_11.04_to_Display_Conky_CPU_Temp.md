---
title: "Getting 11.04 to Display Conky CPU Temp"
date: 2011-10-13
forum: General Help
---

### Post by fleamour on 2011-10-13
I have copied a Conky script of the web.  The code for CPU temp is such:

```
Core 1: ${freq 1} MHz Temprature: $color ${exec sensors|grep ‘Core0&#8242;|awk ‘{print $3}’}
```

Frequency works but displays no temp entry on desktop.  I manage to monitor my temps in Gnome's top bar with Computer Temp Monitor 0.9.6.1.  It displays core 0 as:

```
hwmon0 (1)
```

If that helps?  I would like Conky to display temps as well.

Anyone know the necessary code?

---

### Post by effenberg0x0 on 2011-10-13
Is lm-sensors installed (sudo apt-get install lm-sensors)
Have you ran sudo-sensors-detect?
What is the output of the command sensors? Then we see if we use awk, cut, etc to get the value. But first we need to see if lm-sensors is really instyalled, configured and getting the temp of the core.

regards,
Effenberg

---

### Post by fleamour on 2011-10-13
I installed lm-sensors to get Gnome bar temp gauges working.  Output of sensors is:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +38.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38.0°C  (high = +78.0°C, crit = +100.0°C)  

w83627ehf-isa-0290
Adapter: ISA adapter
Vcore:       +1.07 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +1.07 V  (min =  +1.65 V, max =  +1.02 V)   ALARM
AVCC:        +3.30 V  (min =  +1.01 V, max =  +3.30 V)   
+3.3V:       +3.30 V  (min =  +2.61 V, max =  +2.69 V)   ALARM
in4:         +1.67 V  (min =  +1.53 V, max =  +1.75 V)   
in5:         +1.65 V  (min =  +1.53 V, max =  +0.63 V)   ALARM
in6:         +1.85 V  (min =  +2.04 V, max =  +1.34 V)   ALARM
3VSB:        +3.30 V  (min =  +0.66 V, max =  +0.70 V)   ALARM
Vbat:        +2.05 V  (min =  +1.90 V, max =  +3.55 V)   
in9:         +1.59 V  (min =  +0.12 V, max =  +1.97 V)   
fan1:          0 RPM  (min = 3515 RPM, div = 128)  ALARM
fan2:       1081 RPM  (min = 3668 RPM, div = 8)  ALARM
fan3:          0 RPM  (min = 3515 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
temp1:       +34.0°C  (high = -33.0°C, hyst =  -5.0°C)  ALARM  sensor = thermistor
temp2:       +33.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
temp3:       +45.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

```

---

### Post by effenberg0x0 on 2011-10-13
Rep&#314;ace this...
Core 1: ${freq 1} MHz Temprature: $color ${exec sensors|grep &#8216;_Core0_&#8242;|awk &#8216;{print $3}&#8217;}

with this:
Core 1: ${freq 1} MHz Temperature: $color ${exec sensors | grep "_Core 0_" | awk '{print $3}'}

Small difference (1 space) in the underlined section. The it will be the third word. Otherwise it would be {print $2}

Regards,
Effenberg

---

### Post by fleamour on 2011-10-13
Copy & pasted your code:

```
Core 1: ${freq 1} MHz Temperature: $color ${exec sensors | grep '_Core 0_' | awk '{print $3}'}
```

Still does not show temperature I'm afraid, unless I have to reboot?

---

### Post by effenberg0x0 on 2011-10-13
> **fleamour said:**
> Copy & pasted your code:

```
Core 1: ${freq 1} MHz Temperature: $color ${exec sensors | grep '_Core 0_' | awk '{print $3}'}
```Still does not show temperature I'm afraid, unless I have to reboot?

- Conky calls other programs and work with the text they output using standard BASH commands (grep, cat, awk, sed, cut, etc).

- Conky is running sensors. Sensors outputs many lines (try it yourself on prompt). But the output is "piped" with the "|" symbol to the command "grep". 

Grep will select only the line that contains exactly the text "Core 0"

Try this commands on console:

sensors | grep "**banana**" - > Will show nothing, no match!
sensors | grep "**________Core 1.000.000_______**" -> Will show nothing, no match!
sensors | grep "**Hi my name is John**" -> Will show nothing, no match!
sensors | grep "Core 0" -> MATCH! There is a line that has this exact words. Grep will output the exact matching line. It will show "**Core 0:      +38.0°C  (high = +78.0°C, crit = +100.0°C)** 

We just want the second "word" (words are groups of letters of symbols separated by spaces). The first word is "Core". The second is "0:". The third word is "+38.0°C". We want this one. The third one. We will use the **print** directive of the command **awk** to choose the third word.

So, until now, we took the BIG output (many lines) of the command "sensors" and we **piped** it to **grep**. Grep was instructed to only select a line that had exactly the text "Core 0" in it. Grep found a match and outputs this line, in which the match happened. But we will once again **pipe** the output, but now to awk. Awk will select the word we want.

Try this commands on console:
sensors | grep "Core 0" | awk '{print $1}' => Will show "Core" (First word)
sensors | grep "Core 0" | awk '{print $2}' => Will show "0:" (Second word)
sensors | grep "Core 0" | awk '{print $3}' => Will show "+38.0°C" (Third word).

Now you just have to insert this into conky's script syntax:

Core 1: ${freq 1} MHz Temperature: $color ${exec sensors | grep "Core 0" | awk '{print $3}'}

Regards,
Effenberg

---

### Post by fleamour on 2011-10-13
Thanks!  But all three commands return full string:

```
fleamour@ASRock:~$ sensors | grep "Core 0" | awk "{print $1}"
Core 0:      +38.0°C  (high = +78.0°C, crit = +100.0°C)  
fleamour@ASRock:~$ sensors | grep "Core 0" | awk "{print $2}"
Core 0:      +38.0°C  (high = +78.0°C, crit = +100.0°C)  
fleamour@ASRock:~$ sensors | grep "Core 0" | awk "{print $3}"
Core 0:      +38.0°C  (high = +78.0°C, crit = +100.0°C)
```

Conky is now showing full string & not the third article.

---

### Post by effenberg0x0 on 2011-10-13
Use single quotes here:

awk '{print $3}'

Regards,
Effenberg

---

### Post by fleamour on 2011-10-13
Thanks.

Works now but get horrid foreign character between "38.0" & degrees centigrade symbol.  Looks like a mini capital "A" with a ^ above?!?

---

### Post by effenberg0x0 on 2011-10-13
hmmm, no idea... Maybe the font don't know how to make the ° symbol? You could try another, like:

Add this to the beggining of the .conkyrc file:
```
use_xft yes
xftfont Droid Sans:size=8
override_utf8_locale yes
color0 F0EBE2
color1 F56F6E
color2 E6E6E6

```

And use a different font in the lines, like this:
```
${font Droid Sans:style=Bold:size=8}${color1}
```

Your line would look something like this:
```
Core 1: ${freq 1} MHz Temperature:**${font Droid Sans:style=Bold:size=8}${color1}**${exec sensors | grep "Core 0" | awk '{print $3}'}

```

Regards,
Effenberg

---

### Post by fleamour on 2011-10-13
Sounds like a good workaround.  Will try tomorrow.

Thanks for your kind assistance.

---

### Post by WhitePearl on 2011-10-22
THanks a lot guys, I was reading this thread too.
Could not get the weird A to go away though...

---

### Post by dolmance41 on 2011-11-27
hi effenberg!!! i did everything you said to try!!! i installed lmsensors...  i tryed pasting sensors | grep "Core 0" | awk '{print $3} into the console, but nothing happens!  i tried using it as a line in conky and nothing happens...  here is my output when i type sensors in the console: acpitz-virtual-0 Adapter: Virtual device temp1:         +0.0°C  (crit = +105.0°C)  k10temp-pci-00c3 Adapter: PCI adapter temp1:        +68.1°C  (high = +70.0°C)   PLEASE help me!!!! [email]dolmance41@yahoo.com[/email]

---

### Post by dvorim4 on 2012-04-20
> **dolmance41 said:**
> hi effenberg!!! i did everything you said to try!!! i installed lmsensors...  i tryed pasting sensors | grep "Core 0" | awk '{print $3} into the console, but nothing happens!  i tried using it as a line in conky and nothing happens...  here is my output when i type sensors in the console: acpitz-virtual-0 Adapter: Virtual device temp1:         +0.0°C  (crit = +105.0°C)  k10temp-pci-00c3 Adapter: PCI adapter temp1:        +68.1°C  (high = +70.0°C)   PLEASE help me!!!! [EMAIL="dolmance41@yahoo.com"]dolmance41@yahoo.com[/EMAIL]


you don`t have "Core 0" in your sensors.
you can write there "Virtual device temp1" or "PCI adapter temp1"
Maybe your board can't measure CPU temp or you have it disabled in BIOS

---

