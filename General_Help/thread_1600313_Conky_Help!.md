---
title: "Conky Help!"
date: 2010-10-18
forum: General Help
---

### Post by Foxheadz on 2010-10-18
I used the guide at [this]("http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/comment-page-4/#comment-13796") site to make a nice conky but even though ive tried a bunch of themes with different scripts I always never manage to get weather working (it's just blank) and battery is always at 0% no matter what its at. I'm currently using the pogodynka.sh weather script but as you can see in the screen shot there is nothing (it's supposed to be at the top) anyone know a fix?

---

### Post by Quackers on 2010-10-18
I'm not familiar with pogodynka so I'm lost there. With regard to the battery problemI can remember that I needed to find out whether my battery was bat0 or bat1. Try changing yours and see if it starts working.

---

### Post by sendblink23 on 2010-10-18
> **Foxheadz said:**
> I used the guide at [this]("http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/comment-page-4/#comment-13796") site to make a nice conky but even though ive tried a bunch of themes with different scripts I always never manage to get weather working (it's just blank) and battery is always at 0% no matter what its at. I'm currently using the pogodynka.sh weather script but as you can see in the screen shot there is nothing (it's supposed to be at the top) anyone know a fix?

don't forget to post here your .conkyrc  code contents... so that people can see what you have in it.. that would probably help them to be able to help you

---

### Post by Foxheadz on 2010-10-18
in my conkyrc i only have 
```
${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}
```that has to do with battery

---

### Post by Quackers on 2010-10-18
Here's my .conkyrc entry for the battery bar

${battery_percent BAT0}% ${battery_bar BAT0}

Mr. S good evening sir :-)

---

### Post by Foxheadz on 2010-10-18
Ok  i got it to work by using that code but wht bat1 instead thanks

---

### Post by Quackers on 2010-10-18
Ah that's good :-)
If you want to post your weather details I will have a look, but can't promise anything. Hopefully Mr S will have a look too.

---

### Post by Foxheadz on 2010-10-19
Again thanks this is what a community is all about

---

### Post by Foxheadz on 2010-10-20
I was wondering, you seem to know a lot about conky so what weather script do you use?

---

### Post by Quackers on 2010-10-20
I only know about what I've done myself (and messed up before I got it right with Kaivalagi's expert help :-) ).
The weather is a lot more involved. Have you seen the conkyweather thread? That's where I started. All the basic details are there. Have a look :-)
[http://ubuntuforums.org/showthread.php?t=869328&highlight=conkyweather](http://ubuntuforums.org/showthread.php?t=869328&highlight=conkyweather)

---

### Post by Foxheadz on 2010-10-20
Well i tried to get this to work but i mussed of messed up somehow because it wouldnt show up...someone should really make a gui for the installation proses

---

