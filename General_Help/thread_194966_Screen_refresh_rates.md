---
title: "Screen refresh rates"
date: 2006-06-12
forum: General Help
---

### Post by gibson on 2006-06-12
Hi there, 

I have an LCD monitor (fairly old) and any refresh rate higher than 60 causes some blurry parts around the screen (currently on 75) so i want to get back down to 60. 

I have the nvidia-glx from repos installed and here is the monitor section in my xorg.conf

```
Section "Monitor"
    Identifier     "NEC LCD1800"
    Option         "DPMS"
    HorizSync       24-80
    VertRefresh     55-86
EndSection

```

but in the screen resolution settings i still only see 75hz. Im pretty sure these are the correct Horiz and Vert settings as i used the same ones in breezy.

Any ideas on anything i have missed?

All the best

---

### Post by kvonb on 2006-06-12
Try commenting out the Horiz and Vert lines (put a # at the beginning), I think it will default to 60hz.

Regards,

Kev :)

---

### Post by jvictor on 2006-06-12
I guess u dont need the h-v refresh rates on a LCD monitor. They are for CRTs IMHO

---

### Post by PriceChild on 2006-06-12
try reconfiguring your x, it will then give you the option to choose the modes that your screen can support half way through.
 
Don't forget to backup your xorg.conf file first ;)

---

### Post by mlind on 2006-06-12
With new nvidia drivers, you must request custom modeline on "Screen" section on /etc/xorg.conf

```

SubSection "Display"
	Depth		24
	Modes		**"1280x1024_60"** "1280x1024" "1024x768"
EndSubSection

```

Bolded part gets 60Hz for 1280x1024 resolution.

---

### Post by gibson on 2006-06-12
[QUOTE=mlind]With new nvidia drivers, you must request custom modeline on "Screen" section on /etc/xorg.conf

```

SubSection "Display"
	Depth		24
	Modes		**"1280x1024_60"** "1280x1024" "1024x768"
EndSubSection

```

Bolded part gets 60Hz for 1280x1024 resolution.[/QUOTE]

Thanks for all the replys guys, have just had a chance to try and using the "_60" part worked for me. 

Thanks again
G

---

