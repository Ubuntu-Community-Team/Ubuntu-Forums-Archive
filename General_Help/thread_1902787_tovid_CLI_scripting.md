---
title: "tovid CLI scripting"
date: 2011-12-31
forum: General Help
---

### Post by temporos on 2011-12-31
I'm writing a script to make a DVD for my niece.  But tovid is having issues with my source file paths.  I don't understand what's going wrong here...  I've pasted the script clip and output below.  I tried using escape characters for spaces ("\ ") in the *sourcevid* lines, but that didn't make a difference.

relevant script parts...
```
# Set source video files.
sourcevid1="~/Videos/Yellowstone Park 1.mp4"
sourcevid2="~/Videos/Jasper National Park 3.mp4"

# Set respective output video files.
outvid1="yellowstone1"
outvid2="jasper2"

# Convert the mp4 files to DVD-ready mpg.
tovid -noask -dvd -in "$sourcevid1" -out $outvid1
tovid -noask -dvd -in "$sourcevid2" -out $outvid2
```

CLI output...
```
--------------------------------
tovid
DVD and (S)VCD video conversion script
Version 0.31
http://www.tovid.org
--------------------------------
Using config file /home/jonathan/.tovid/tovid.config, containing the following options:
(none)
tovid command-line used:
-noask -dvd -in ~/Videos/Yellowstone Park 1.mp4 -out yellowstone1
Could not find input file . Exiting.
--------------------------------
tovid
DVD and (S)VCD video conversion script
Version 0.31
http://www.tovid.org
--------------------------------
Using config file /home/jonathan/.tovid/tovid.config, containing the following options:
(none)
tovid command-line used:
-noask -dvd -in ~/Videos/Jasper National Park 3.mp4 -out jasper2
Could not find input file . Exiting.

```

---

