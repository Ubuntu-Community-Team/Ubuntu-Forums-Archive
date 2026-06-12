---
title: "Conky - Symbol for battery status"
date: 2011-12-13
forum: General Help
---

### Post by 1inux on 2011-12-13
For conky, is there an if-then statement that could display a '-' or '+' depending on whether my laptop battery is charging of discharging.

Usually, i will use:

${if_match <conky variable> >= 65 } <conky action>${endif}
${if_match <conky variable> <= 64 } <conky action>${endif}

...or something close to that. but, i dont know how to a conky variable that tells chargin/discharging and how to display  + or -.

---

### Post by Habitual on 2011-12-14
> **1inux said:**
> 
${if_match <conky variable> >= 65 } <conky action>${endif}
${if_match <conky variable> <= 64 } <conky action>${endif}

...or something close to that. but, i dont know how to a conky variable that tells chargin/discharging and how to display  + or -.

Great Pseudo-Code!
+1

I only spent a few minutes researching this (here, btw) and came up with this (using your snippet)
```

${if_match battery_percent >= 65 }+${endif}$else${if_match battery_percent <= 64 }-${endif}

```That says 
IF battery_percent is >= 65, 
display "+"
else
battery_percent <= 64
display "-"
endif
[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html) has the battery_ options for conky.

Here's some actual code I use*d* last year to show me the USB free_perc on a USB mount with the option that if USB != mounted, then "USB Not Mounted"...and it uses If>then>else type logic.

```

${if_mounted /media/flash}${goto 600}${color red}USB$color is  ${fs_free_perc /media/flash/}% Free$color${else}${color red}USB Not  Mounted$color${endif}
```HTH.

Edit:
Use 
```
${font DejaVu Sans Mono:size=xx}
``` to alter the size of the displayed +\- sign(s) so it *could* be
```
${if_match battery_percent >= 65 }${font DejaVu Sans Mono:size=16+$font${endif}$else${if_match battery_percent <= 64 }${font DejaVu Sans Mono:size=16-$font${endif}
```

I purposely left out a keyword in the code I presented. It will NOT work as is.
[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html) will show you what is missing.
Consider this Incentive.

---

