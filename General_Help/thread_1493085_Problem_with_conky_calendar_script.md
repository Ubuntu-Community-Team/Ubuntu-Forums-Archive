---
title: "Problem with conky calendar script"
date: 2010-05-25
forum: General Help
---

### Post by entsyymi on 2010-05-25
I finally found a calendar script that I like, and it even works. I just would like to have the week to start on Monday instead of Sunday. I just can't figure how to do it, if it's even possible...

Here's the lines that I use:

```
${font Aerial:style=Bold:pixelsize=14}${execi 60 date +"%B %Y" | tr "[:lower:]" "[:upper:]"}${font Snap.se:size=8} ${hr 1 }

${font Bitstream Vera Sans Mono:style=Bold:size=13}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS " s/" $DJS "/" "'${color1}'"$DJS"'${color0}'" "/}
```Anyone got any ideas?

Oh, and I'm using 10.04.

---

### Post by El_Belgicano on 2010-08-06
Hi, since I upgraded to Lucid Lynx, I ran into the exact same problem, before that, the gutsy version of cal had a "-m" option to start the weeks on monday but it's gone now...
Any input appreciated...

Thanks

---

