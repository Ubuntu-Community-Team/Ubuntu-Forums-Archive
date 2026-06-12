---
title: "Is it possible to make my desktop snow when it snows in my local place?"
date: 2010-11-08
forum: General Help
---

### Post by MKVCrazy on 2010-11-08
I have the weather feature turned in my system tray and it shows my local weather. Let's say I setup a snowing effect on my desktop, I want it to snow when my local weather reporter shows snow sign.

Is this possible? Is there a tutorial on how to do this?



Thanks

---

### Post by coldraven on 2010-11-09
Try this:
[http://www.omgubuntu.co.uk/2010/08/weatherpaper-puts-the-weather-outside-on-your-desktop-inside/](http://www.omgubuntu.co.uk/2010/08/weatherpaper-puts-the-weather-outside-on-your-desktop-inside/)

You can modify it with your own images, maybe even animations.

---

### Post by stinkeye on 2010-11-09
Let me preface this by saying I know very little about writing scripts
and just looked at other peoples scripts I use.
I had a go at making a script and it actually works so I thought I would share it with you.

I have no idea about how to get info on the current icon the weather applet
is using, so I used curl (download in the software centre) to get current 
conditions from a wunderground.com rss feed for Helsinki.
I just chose a location where it was currently snowing.
Find your location at wunderground.com and click on the rss feed and then substitute that address into the highlighted 
part of the script.

The script downloads the feed every 15 mins and then counts the number of instances of "snow" ignoring case distinctions.
If the number does not equal zero then it initates the keyboard shortcut
for the snow plugin using xdotool (download in the software centre)
and you will see snow on the desktop for 30 secs.

I'm sure someone who knows how to write scripts can improve it.eg do a proper loop.
As I live in Australia I will never see snow on the desktop so I'll have
to adapt it to use the Water Effect plugin.
```
#! /bin/bash
until [ "$done" = "true" ]
do
       if 
             [ $(curl "[COLOR="Magenta"]http://rss.wunderground.com/auto/rss_full/global/stations/02974.xml?units=metric[/COLOR]" | sed -e :a -e 's/<[^>]*>//g;/</N;//ba' | grep -m 1 "Current Conditions :" | grep -c -i "snow") != 0 ]
        then
             xdotool key "super+F3"
             sleep 30;
             xdotool key "super+F3"
             done="false"
             sleep 15m;
        else
             echo "No Snow"
             done="false"
             sleep 15m;
        fi
done
exit 0
```

---

### Post by MKVCrazy on 2010-11-14
Thank you. I will check those out.

---

