---
title: "Firefox won't start and opera is also crazy"
date: 2009-07-12
forum: General Help
---

### Post by vratnica on 2009-07-12
Hello all!

After 3 weeks of not using my PC, today I started it and since the automatic updates doesn't work by me, I have done it manually

after restart I cannot start firefox, and when I open Opera, there are almost no graphics to be seen on web pages, only text (now durinf writing I see only ubuntu logo up left and smileys on the right- everything else is white + text)

videos I also cannot see

I run the latest version of Ubuntu, but I dont know how to see details, sorry

Please help, cause on this way I cannot surf and cannot access many sites, since my passwords are saved on firefox

---

### Post by vratnica on 2009-07-12
If I start FF in the terminal, I get the following:

/usr/share/themes/HumanME/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/HumanME/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/HumanME/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/HumanME/gtk-2.0/gtkrc:141: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/HumanME/gtk-2.0/gtkrc:204: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Segmentation fault

---

### Post by XCan on 2009-07-12
What did you update? Perhaps a backup of your .mozilla directory and a reinstallation of firefox is in order? What bothers me though is that Opera broke simultaneously.

---

### Post by vratnica on 2009-07-13
Well, it was plenty of things that I have updated

The thing that I have just realised is that neither opera nor konqueror, which I am now also trying, can remember the sites and passwords from earlier sessions. 

I always have to agree with terms and conditions for opera, and I always have to manually tip the names of the sites that I want to visit. During the same session they can remember, but next time not.

In Konqueror I have also installed the shockwave plugin, ant changed the start page, and today I see that nothing is changed

Epiphany browser, which came in the ubuntu package, I also cannot start

---

### Post by vratnica on 2009-07-13
:lolflag:


I found it out

the reason was quite dummy

I already began to think about the reinstallation and than looked up in my home partition (in order to choose it again as the home partition and to hold all my configuration files the same) and than I notices that my  home partition is COMPLETELY full :p

I deleted some big files and voila! Everything is perfectly functioning as before

The only strange question would be: how could my last update take so much space? 3 weeks ago I deleted around 1,5 GB and since than I didnt download almost anything...

---

### Post by XCan on 2009-07-13
That's strange, a system update performed by the update tool in Ubuntu should never download anything to your /home partition. Thus, I don't think it was the update that clogged your /home up. You may want to take a look in the Disk Usage Analyzer for hints of why your /home is full.

---

