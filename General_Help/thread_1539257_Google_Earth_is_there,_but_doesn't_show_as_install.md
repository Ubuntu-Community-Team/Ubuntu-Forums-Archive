---
title: "Google Earth is there, but doesn't show as installed"
date: 2010-07-26
forum: General Help
---

### Post by Cavsfan on 2010-07-26
I start Google Earth (Applications > Internet > Google Earth) and it gives a couple of errors 

```
Google Earth could not write to the current cache or My Places file location. The values will be set as follows:
 My Places Path: "/home/cavsfan/.googleearth"
Cache Path: "/home/cavsfan/.googleearth/Cache"
```I can click OK and it seems to work OK, but in Ubuntu Software Center and in Synaptic it does not even show that it is installed. :confused:
I have 5.2.1.1329 (beta) and was wanting to install the newest version from the Software Center.
I just do not know how to uninstall the current version or where to go to remove it.
Any help as always is greatly appreciated.

---

### Post by Vaphell on 2010-07-26
did you install it manually from by running googleearth.bin or whatever it's called? if so, then the installation happened out of the scope of the package manager and it simply doesn't know anything about GE.

---

### Post by Cavsfan on 2010-07-26
> **Vaphell said:**
> did you install it manually from by running googleearth.bin or whatever it's called? if so, then the installation happened out of the scope of the package manager and it simply doesn't know anything about GE.

Probably. I cannot remember. When I see it in Software Center, the "Install" button is available, so it apparently does not detect that it is installed either.
Thanks!

---

### Post by Vaphell on 2010-07-26
btw, that error you get is probably because of permission issues, go to .config/Google and see if the .conf files there are owned by you and if you can modify them

```
ls -l ~/.config/Google
```

if you get -rw-r--r-- cavsfan cavsfan - it's ok
open GoogleEarthPlus.conf and see if it doesn't point to some strange location not in your home dir

if everything looks fine, see if you own .googleearth dir and stuff inside it


to answer your question: most probably your GE is installed in /opt/googleearth
locations of all GE related stuff you can find with
```
locate googleearth
```

---

### Post by Cavsfan on 2010-07-26
> **Vaphell said:**
> btw, that error you get is probably because of permission issues, go to .config/Google and see if the .conf files there are owned by you and if you can modify them

```
ls -l ~/.config/Google
```if you get -rw-r--r-- cavsfan cavsfan - it's ok
open GoogleEarthPlus.conf and see if it doesn't point to some strange location not in your home dir

if everything looks fine, see if you own .googleearth dir and stuff inside it


to answer your question: most probably your GE is installed in /opt/googleearth
locations of all GE related stuff you can find with
```
locate googleearth
```

"ls -l ~/.config/Google"
Yields this:

```
total [COLOR=Red]8[/COLOR]
-rw-r--r-- 1 root root 1630 2010-06-22 11:14 GECommonSettings.conf
-rw-r--r-- 1 root root 1540 2010-06-22 11:14 GoogleEarthPlus.conf

```Not sure why it says it found 8 and shows 2. Guess the others are hidden maybe?

"locate googleearth"
Yields this:

```
/home/cavsfan/.googleearth
/home/cavsfan/.googleearth/Cache
/home/cavsfan/.googleearth/Temp
/home/cavsfan/.googleearth/instance-running-lock
/home/cavsfan/.googleearth/myplaces.backup.kml
/home/cavsfan/.googleearth/myplaces.kml
/home/cavsfan/.googleearth/myplaces.kml.tmp
/home/cavsfan/.googleearth/Cache/dbCache.dat
/home/cavsfan/.googleearth/Cache/dbCache.dat.index
/home/cavsfan/.googleearth/Cache/dbroot_cache
/home/cavsfan/.googleearth/Cache/icons
/home/cavsfan/.googleearth/Cache/models
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_1050_l.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_3d_buildings_new_l.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_blue_star_l.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_cabs64_l.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_census_new_l.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_city_capital_star.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_city_major.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_flag64_l.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_generic_poi_l.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_lil_earth_l.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_ocean_l.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_panoramio_photo_square.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_panoramio_photo_square_l.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_park-15.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_plane_blue_small_nh.png
/home/cavsfan/.googleearth/Cache/icons/kh.google.com_icons_roads_legend_l.png
/home/cavsfan/.googleearth/Temp/ge20964
/home/cavsfan/.googleearth/Temp/ge31882
/opt/google-earth/Google-googleearth.desktop
/opt/google-earth/googleearth
/opt/google-earth/googleearth-bin
/opt/google-earth/googleearth-icon.png
/opt/google-earth/googleearth-mimetypes.xml
/opt/google-earth/googleearth.xpm
/opt/google-earth/libgoogleearth_free.so
/usr/local/bin/googleearth
/usr/share/app-install/desktop/googleearth.desktop
/usr/share/app-install/icons/_usr_share_googleearth_resources_googleearth-icon.png
/usr/share/applications/Google-googleearth.desktop
/usr/share/mime/packages/googleearth-mimetypes.xml
```Is it possible to get rid of all of this and start over by installing in through the Software Center?
Thanks for your help. I tried "locate google-earth" which found nothing.
Still learning...

---

### Post by Vaphell on 2010-07-26
most probably yes, you can wipe the stuff from /opt/googleearth and these few files in /usr/share and then install with package manager

i have no idea why ls -l says total 8 (mine does the same), but you can see these files are owned by root, thus GoogleEarth complains that it can't modify them

to fix ownership
```
sudo chown -R cavsfan:cavsfan ~/config/Google
sudo chown -R cavsfan:cavsfan ~/.googleearth

```

---

### Post by Cavsfan on 2010-07-26
> **Vaphell said:**
> most probably yes, you can wipe the stuff from /opt/googleearth and these few files in /usr/share and then install with package manager

i have no idea why ls -l says total 8 (mine does the same), but you can see these files are owned by root, thus GoogleEarth complains that it can't modify them

to fix ownership
```
sudo chown -R cavsfan:cavsfan ~/config/Google
sudo chown -R cavsfan:cavsfan ~/.googleearth

```

Thanks! I appreciate you prompt response and help!!! :D
I will proceed to removing this stuff as it is beta and I really don't like beta anyway.
I'll report back when I have it done.
Thanks again!

---

### Post by Cavsfan on 2010-07-26
Thanks for your help! I got the new version non-beta installed and it looks good.
Doesn't give any errors upon startup at all.

Thanks again! :D

---

