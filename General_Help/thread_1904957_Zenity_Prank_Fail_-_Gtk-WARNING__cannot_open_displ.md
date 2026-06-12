---
title: "Zenity Prank Fail - Gtk-WARNING **: cannot open display"
date: 2012-01-05
forum: General Help
---

### Post by davethewave83 on 2012-01-05
I wanted to play a prank on my sister it didn't work and I thought I'd just ask why not. 

On my local machine I type```
find / | zenity --progress --pulsate --text "Erasing hard drive - please wait"
```

it works, and I get a pulsating dialogue box, the hard drive is using "Find" and so it's going wild, as if it's being erased... "Okay, good" I think

so I ssh to my sisters machine and login as her

I know that from ssh I will need to provide the DISPLAY command also, so I do```
DISPLAY=:0 find / | zenity --progress --pulsate --text "Erasing hard drive - please wait"
```

but it says cannot open display. 
I tried moving the DISPLAY command over next to zenity instead of find, it still doesn't work.

also, find ends a bit soon, any way to make this last a bit longer? ;)

---

