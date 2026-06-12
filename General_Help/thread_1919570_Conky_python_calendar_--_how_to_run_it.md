---
title: "Conky python calendar -- how to run it???"
date: 2012-02-03
forum: General Help
---

### Post by ppqq on 2012-02-03
Simple Q nevertheless....

I'm trying to make an instance of conky run a python script calendar (I found it [here]("http://www.kittykatt.us/index.php?page=scripts&s=conkycal"))

So I have normally a bash script that runs .conkyrc and .conkycal at start up

.conkycal used to have
TEXT
$color

# Clock
${color blue}${font ubuntu:size=25}${time %H:%M}$font$color
${font :size=12}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/ /' | sed /" $DJS "/s/" $DJS "/" "'${color orange}'"$DJS"'${color}'" "/}
#${font DejaVu Sans Mono :size=10}${exec cal}

but it has always failed to display properly, today's date was always between two boxes rather than highlighted.

so I was looking for a better one, and I replaced the stuff under "#Clock" with the command to run the python script from that page above:

**command**:

-which I put in a file conkycal.py (executable)

{execp python /conky/conkycal.py}
also tried {exec python /conky/conkycal.py}

**script**:
<
#!/usr/bin/env python
import time, calendar, re
 
localtime = time.localtime(time.time())
calendar.setfirstweekday(calendar.SUNDAY)
cal = calendar.month(localtime[0], localtime[1])
 
parts = cal.split('\n')
cal = '${alignc}${offset -8}' + '\n${offset 37}'.join(parts)
 
regex = '(?<= )%s(?= )|(?<=\n)%s(?= )|(?<= )%s(?=\n)' % (localtime[2], localtime[2], localtime[2])
replace = '${color1}%s${color white}' % localtime[2]
newCal = re.sub(regex, replace, cal)
print newCal
>

but on start up the conky shows that text on the desktop ie {exec python /conky/conkycal.py}

what am i doing wrong??  I have very little idea about python!

thanks anyone

---

