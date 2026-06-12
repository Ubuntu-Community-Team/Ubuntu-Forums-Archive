---
title: "Display Asian characters in gnome-terminal"
date: 2010-12-31
forum: General Help
---

### Post by bk__888 on 2010-12-31
I am having issues with displaying Asian characters when using the $ tree command.

I have tried changing it via

Terminal -> Set character Encoding -> Unicode (UTF-8.) in terminal options.

I have also tried changing it to various other Asian encodings as well.

Asian characters do display correctly in Pcman, Firefox, Leafpad and Terminal if I open Terminal from Pcman. 

When I try the command

$ tree> /home/sun/music_dir.txt 

or

$ tree

Both in  Leafpad or Gnome-Terminal I get the output.


&#9500;&#9472;&#9472; \343\203\225\343\202\247\343\202\244\343\203\273\343\202\246\343\202\251\343\203\263
&#9474;   &#9492;&#9472;&#9472; \343\203\201\343\203\243\343\203\263\343\203\273\343\203\250\343\202\246\357\274\210\346\255\214\343\201\202\343\201\235\343\201\263\357\274\211\357\275\236\343\202\271\343\203\232\343\202\267\343\203\243\343\203\253\343\203\273\343\202\250\343\203\207\343\202\243\343\202\267\343\203\247\343\203\263

instead of

&#9500;&#9472;&#9472; &#12501;&#12455;&#12452;&#12539;&#12454;&#12457;&#12531;
&#9474;   &#9492;&#9472;&#9472; &#12481;&#12515;&#12531;&#12539;&#12520;&#12454;&#65288;&#27468;&#12354;&#12381;&#12403;&#65289;&#65374;&#12473;&#12506;&#12471;&#12515;&#12523;&#12539;&#12456;&#12487;&#12451;&#12471;&#12519;&#12531;


 
Any help would be appreciated

---

### Post by bk__888 on 2011-01-02
Found the problem

I needed to use -N.

$ tree -N

-N Print non-printable characters as is instead of the default carrot notation.

---

