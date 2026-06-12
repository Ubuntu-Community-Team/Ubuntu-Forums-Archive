---
title: "Need help editing python code?"
date: 2010-01-20
forum: General Help
---

### Post by garyinspringhill on 2010-01-20
I have helped put together a very powerful hpgl front end for Ubuntu/Gnome for use with vinyl cutters/plotters/engravers/plasma torches etc. I added some new features to this new release but don't know enough about python to get the last feature done.
I have included the files needed to take a look at the gui front end for an hpgl engraver output. I just can't figure out one last feature I'd like to add before I post this newer version on my web site for download.
 As it stands on opening it reads it's defaults from ~/.hpgl/camm2.defaults which is great if you have only one machine, it also saves settings on exit to the same file. If you have multiple machines it's a real pain adjusting all the settings each time so I'd like it to read the default file camm2.defaults to avoid an error but if another config file in the same .hpgl folder is found matching the first line in camm2.defaults eg:engraver2 filename engraver it will open and read in those parameters into the gui window. Also when closing the gui or by clicking the "store settings for this hpgl device" it will save the settings to a filename based on the device selected such as "engraver2" as well as camm2.default as mentioned before. One last thing in the gui window if a different output device is selected while open I'd like the settings reread for that device from it's file and the gui refreshed.

I would sure appreciate any help in this matter as it seems to be quite useful to a lot of people and this new release will add much needed features. It adds a lot of usefulness to inkscape, corel(wine) and sk1 in the sign making industry.

 Thanks 
 Gary Langthorne

---

