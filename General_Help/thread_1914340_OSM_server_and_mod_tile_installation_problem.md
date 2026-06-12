---
title: "OSM server and mod_tile installation problem"
date: 2012-01-24
forum: General Help
---

### Post by still_bg on 2012-01-24
Hi,
  I have correctly installed database with imported world data and mapnik2 (i have rendered image with generate_image.py - it work). Now i try to install mod_tile and apache2. It seem everything to be fine until i use comand - apache2ctl restart and see this:
[B]
root@mslocalmap:/etc/apache2/mods-enabled# apache2ctl restart
apache2: Syntax error on line 204 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/mod_tile.load: Cannot load /usr/lib/apache2/modules/mod_tile.so into server: /usr/lib/apache2/modules/mod_tile.so: cannot open shared object file: No such file or directory[/B]

Can somebody help me with this problem. :confused: Any idea why mod_tile.so is not installed in /usr/lib/apache2/modules/ . :confused: Maybe this is not right place to ask this but I will be very thankful if somebody can help me with this.

---

