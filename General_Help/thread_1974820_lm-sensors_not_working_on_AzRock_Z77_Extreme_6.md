---
title: "lm-sensors not working on AzRock Z77 Extreme 6"
date: 2012-05-06
forum: General Help
---

### Post by airspoon on 2012-05-06
Hello, I just tried running 'sensors-detect' and after hitting 'enter' on all of the defaults, I'm not able to get any temp readouts through the 'sensors' command. In addition, the 'system-monitor' shell extension for Gnome-Shell is not working.

I have a relatively new motherboard, the AsRock z77 e6 so could it be that lm-sensors simply doesn't support my motherboard yet? Or, should I choose an option other than the defaults when running sensors-detect?

Here is what the 'sensors-detect' found:

```

Driver `w83627ehf':
  * ISA bus, address 0x290
    Chip `Nuvoton NCT6776F Super IO Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
w83627ehf
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

```

Should I have cut and pasted those on the option that followed which asked me if I wanted to add these automatically to /etc/modules, with the default being 'No'?

Any and all help would be greatly appreciated. I'm overclocking my i5-2500k to about 4.5ghz and would like to keep an eye on my temps. Thanks.

---

### Post by gordintoronto on 2012-05-06
Where the default is "no," type "yes." Then reboot.

Did you begin with: sudo sensors-detect

---

### Post by airspoon on 2012-05-06
Thanks for the reply! I tried it and it worked :-). I was kind of worried to against the defaults because the little warnings would say something to the effect of "this PROBABLY won't hurt your computer", lol.

Anyway, now that lm-sensors is working, I was hoping that the system-monitor shell extension would simply start working too. However, I have a feeling that I need to re-install it, though I have no idea how. Can I just erase it from its directory in order to re-install it once again? If so, which directory do gnome extensions reside? Is there a better way to do it?

Again, thanks!

---

### Post by gordintoronto on 2012-05-07
Sorry, I don't know what the system monitor shell extension is. Are you running 11.10 with Unity? If you installed it using the software center, you can remove it from there. Or from Synaptic Package Manager, which I prefer.

I use Conky. Every time I try a different version or distro (which is about every three weeks...) I wind up tweaking my conkyrc file.

---

### Post by airspoon on 2012-05-07
I'm using Gnome-Shell on 12.04 and installed the extension from [extensions.gnome.org]("https://extensions.gnome.org/extension/120/system-monitor/"). It's like a little button that you click and that's it. The process is pretty cool actually. Anyway, that button has now turned into error message so there is no way to turn it off or uninstall it, at least from what I can tell.  

Conky, I was using conky under 11.10 and while I also like it, I have been far too busy with final exams to rework another conkyrc file for this new machine. Besides, I could never get conky to read out the data from lmsensors on my old machine but I guess I'll give it a try once my school is over.

However, I'm still aiming to get this extension working because unlike conky, a readout on my taskbar will be visible at all times, regardless of any windows that I have open.

Anyway, thanks for the help.

---

### Post by gordintoronto on 2012-05-09
Here are the relevant lines in my 12.04 conkyrc:

```

${color #A548CC}Uptime:${color}    ${uptime}
${color #A548CC}Kernel:${color}      ${exec uname -r|cut -b1-8}
${color #A548CC}IP Address:${color} ${addr wlan0}
${color #A548CC}CPU Temp:${color}         ${hwmon temp 1}C
${color #A548CC}Drive Temp:${color}       ${hddtemp}C
${color #A548CC}Video Temp:${color}       ${execi 60 nvidia-settings -t -q GPUCoreTemp} C

```

---

