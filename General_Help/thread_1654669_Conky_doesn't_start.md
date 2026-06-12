---
title: "Conky doesn't start"
date: 2010-12-28
forum: General Help
---

### Post by Mr. ViC on 2010-12-28
Hi again guys!

So, today is my first day with conky. I have installed the all-featured one from the software center. And I found this config I really damn love, has LOTS of stats and that is just what I want:

[URL="http://gnome-look.org/content/show.php/My+conky+config?content=86112"]```
http://gnome-look.org/content/show.php/My+conky+config?content=86112[/URL]
```
But when I try to execute conky from the command line, this happens:

[FONT=monospace]
[/FONT]```
Conky: /home/dave/.conkyrc: 9: config file error
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't open '/sys/class/hwmon/hwmon1/temp1_input': No such file or directory
please check your device or remove this var from Conky
Conky: Error destroying thread
Conky: Error destroying thread
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.
```
[FONT=monospace]
Can anyone help me out here? Thanks a lot in advance! :p


[/FONT]

---

### Post by cariboo on 2010-12-28
Usually you need to type:

```
conky -c /path/to/configfile
```

in order to start conky from the command line.

---

### Post by Mr. ViC on 2010-12-28
Hello.

Tried what you told me, worked, but still the same error mate.

---

### Post by Mr. ViC on 2010-12-28
<bump>

---

### Post by wojox on 2010-12-28
Edit .conkyrc and change 

use_spacer yes to use_spacer right

And remove the /sys/class/hwmon/hwmon1/temp1_input variable.

See [Ubuntu Geek]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html")

---

### Post by Mr. ViC on 2010-12-28
Hello.

Thank you! The first code you gave me worked and solved the problem.

And with the second I was able to find out what was wrong:

And it is there:

```
${color #B8FF00}HDD:${color white} ${alignr} HDD Temp: ${color orange}${execi 1 /home/ghostrider/.conky_script_hddtemp}.0${color white}°C
```The author left it's own path there.

It works great now and it is so damn beautiful! Thank you so much!

---

