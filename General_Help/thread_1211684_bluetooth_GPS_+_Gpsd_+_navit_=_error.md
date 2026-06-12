---
title: "bluetooth GPS + Gpsd + navit = error"
date: 2009-07-12
forum: General Help
---

### Post by BrownieMan on 2009-07-12
I managed to get my GPS bluetooth paired with my computer but when I install and try to run Navit I get an error.

```
sudo apt-get install build-essential pkg-config automake libglib2.0-dev libtiff4-dev libtool libxmu-dev libfribidi-dev gettext zlib1g-dev cvs gpsd gpsd-clients libgps-dev libdbus-glib-1-dev libgtk2.0-dev freeglut3-dev glutg3-dev libcegui-mk2-dev libdevil-dev libglc-dev libpcre3-dev libmng-dev libfreeimage-dev


wget http://sourceforge.net/projects/navit/files/navit/navit-0.1.1.tar.gz/
tar xzf navit-0.1.1.tar.gz
cd navit-0.1.1/
./configure
make
cd navit
./navit
```


It, runs a little but then I just get teh same error again after again.


```
phil@phil-desktop:~/tmp/navit-0.1.1/navit$ ./navit
Running from source directory
vehicle_gpsd:vehicle_gpsd_try_open:gps_open failed for 'gpsd://localhost'. Retrying in 10 seconds. Have you started gpsd?
vehicle_gpsd:vehicle_gpsd_try_open:gps_open failed for 'gpsd://localhost'. Retrying in 10 seconds. Have you started gpsd?
vehicle_gpsd:vehicle_gpsd_try_open:gps_open failed for 'gpsd://localhost'. Retrying in 10 seconds. Have you started gpsd?
vehicle_gpsd:vehicle_gpsd_try_open:gps_open failed for 'gpsd://localhost'. Retrying in 10 seconds. Have you started gpsd?
map_rect_new_textfile unable to open textfile /home/phil/tmp/navit-0.1.1/navit/destination.txt
map_rect_new_textfile unable to open textfile /home/phil/tmp/navit-0.1.1/navit/bookmark.txt
navit:main:Using 'navit.xml'
vehicle_gpsd:vehicle_gpsd_try_open:gps_open failed for 'gpsd://localhost'. Retrying in 10 seconds. Have you started gpsd?
vehicle_gpsd:vehicle_gpsd_try_open:gps_open failed for 'gpsd://localhost'. Retrying in 10 seconds. Have you started gpsd?
vehicle_gpsd:vehicle_gpsd_try_open:gps_open failed for 'gpsd://localhost'. Retrying in 10 seconds. Have you started gpsd?
vehicle_gpsd:vehicle_gpsd_try_open:gps_open failed for 'gpsd://localhost'. Retrying in 10 seconds. Have you started gpsd?

```

I was attempting to try and start "gpsd", but I don't even know how to do that. Any help would be appreciated.

---

