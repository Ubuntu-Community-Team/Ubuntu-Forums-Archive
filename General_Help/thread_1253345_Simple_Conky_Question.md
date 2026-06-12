---
title: "Simple Conky Question"
date: 2009-08-30
forum: General Help
---

### Post by tom.swartz07 on 2009-08-30
Hi all,

I have a really easy question, but I cannot seem to figure it out myself.

In my Conky config file, I would like to grab the output of several lines from a python script. The script in question gives a current conditions output, and then lists the forecast for the next few days. I only want the current conditions. 
```

${execi 1200 python ~/scripts/conkyscripts/weather.py ZIP}
``` outputs:```
(Scranton, PA)
66°?! ITS NICE!
Open a window or something!

Forecast
  Today (Sat)
    High: 73
    Low: 60
    Weather: Partly Cloudy
  Tomorrow (Sun)
    High: 75
    Low: 52
    Weather: Partly Cloudy
```I would like to have an output of simply ```
(Scranton, PA)
66°?! ITS NICE!
Open a window or something! 
```I tried a grep, but it only gets the first line, Scranton.


What, my dear friends, should I do to get only those first 3 lines? :confused: Any help would be greatly appreciated.

Thanks,
Tom

---

### Post by razorboy5 on 2009-08-30
i'm not very pro at this either but

what's ur weather.py look like?

---

### Post by tom.swartz07 on 2009-08-30
haha

Ive already tried to pull it apart, its a recursive python script that pulls information systematically from a website. Id post it here, but its almost 300 lines long. 

Normally Im alright with pulling apart programs and making a frankenprogram for myself fit to my needs, but this one seems to be a little more difficult.

If you really think it will help, Ill post it, but like I have said- its a big one. haha

---

### Post by geirha on 2009-08-30
If you always want the first three lines of output, you could just use head
```
command | head -3
```

A more portable way would be something like
```
command | sed -n '1,3p'
```

---

### Post by tom.swartz07 on 2009-08-30
geirha, that worked perfectly!

i knew there was a basic command that would do what i needed, i just couldnt figure out what it was.

Cheers!
Tom

---

