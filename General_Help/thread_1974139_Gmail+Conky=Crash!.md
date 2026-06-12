---
title: "Gmail+Conky=Crash!"
date: 2012-05-05
forum: General Help
---

### Post by hakermania on 2012-05-05
I've been playing with conky for an hour or so, and it crashes where in the configuration, it says:
```

 ${goto 32}Gmail: ${alignr}${font Ubuntu:style=Bold:size=8}${color0}${execpi 3600 /home/alex/.conky/gmail.sh}${color}${font} New email(s)

```

Conky starts up fine if I comment out this line, put I don't understand what conky finds 'frustrating' at this line!
If I normally run the script /home/alex/.conky/gmail.sh I get the count of my gmail emails, and it works perfectly. It outputs the number of new emails at about 2-3 seconds after run!

Also, it shouldn't be external's script mistake, as I've tried with another script with the same result.

On the other hand, if I turn 'execpi' to 'exec' I think, I get conky running but where it should place the count of my emails, it places: (null)

Any help appreciated :)):P

---

### Post by Gillingham on 2012-05-05
I have got a script working for a similar purpose working fine with conky with "execpi".  Have you running conky from a terminal?  I've had luck with that approach in the past.

---

### Post by hakermania on 2012-05-06
> **Gillingham said:**
> I have got a script working for a similar purpose working fine with conky with "execpi".  Have you running conky from a terminal?  I've had luck with that approach in the past.

Yep, I'm running conky from a terminal, and I get the error

```
Segmentation fault Core dumped
```

---

### Post by Gillingham on 2012-05-06
That isn't looking terribly useful.  I know you have said that the script runs normally from a terminal.  Are you specifying the shell the script should use?

---

### Post by hakermania on 2012-05-06
> **Gillingham said:**
> That isn't looking terribly useful.  I know you have said that the script runs normally from a terminal.  Are you specifying the shell the script should use?

No, you maybe misunderstood me. Conky always crashes if I don't have the GMAIL line uncommented, no matter how I run it. If i run it through terminal I get the above error message.

Terminal uses bash, and so conky runs through bash and crashes...

---

### Post by stinkeye on 2012-05-06
You should only use execpi if you want to parse conkyrc objects included in a script or template.
eg if you were running a colorize script to change text color with temperature.
eg```
#!/bin/bash
# colorize.sh
# by: Crinos512

COOL=32
WARM=48

if [[ $1 < $COOL ]]
   then echo "\[COLOR="Magenta"]${color7}[/COLOR]"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\[COLOR="magenta"]${color4}[/COLOR]"$1    # HOT
else echo "\[COLOR="magenta"]${color8}[/COLOR]"$1       # WARM
fi

exit 0
```
The execpi command
```
${execpi 3 sensors k10temp-pci-00c3 | grep temp1 | awk '{print $2}' | cut -c2-3 | xargs ~/conky/ColorTemp/ColorTempCPU.sh}
``` 
will interpret the [COLOR="magenta"]${color}[/COLOR] values in the output. **Pic1**
Using execi for the same command gives **Pic2**.

There is a bug in the conky package for 12.04.
Execi commands don't run until the interval is greater than your computer uptime... ie outputs "null".

Downgrading conky will fix the "null" output. 
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11894013&postcount=19669")

---

### Post by hakermania on 2012-05-06
> **stinkeye said:**
> 
There is a bug in the conky package for 12.04.
Execi commands don't run until the interval is greater than your computer uptime... ie outputs "null"

Oh, I see, thanks a lot!

---

