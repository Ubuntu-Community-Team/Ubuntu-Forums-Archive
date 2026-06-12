---
title: "Mr Sid files in QGIS 12.04 Precise"
date: 2012-06-05
forum: General Help
---

### Post by BigBaka on 2012-06-05
Dear all, 

After having recently made the switch from 10.04 to 12.04 I've been busying installing all my applications and getting things just right. Having now installed QGIS 1.7.4 successfully in 12.04 I couldn't help but notice that Mr Sid raster files can still not be used in QGIS on 12.04 precise. Wondering if anyone has managed to get sid raster files working in qgis on 12.04.

Regards,
BigBaka

---

### Post by BigBaka on 2012-07-01
So have now updated to QGIS 1.8 'Lisboa' in Ubuntu 12.04 LTS 32 bit.

Still can't see any new instructions on how to get sid or ecw files going in QGIS, although at least the sid formats can be loaded in the Windows version!

Anyone managed to find a way to put sid files into QGIS 1.8? Why is this always an ongoing issue? I haven't been able to load sid files in Ubuntu for more than a year now!

Eternally hopeful

BB

---

### Post by BigBaka on 2012-08-04
Anyone?

---

### Post by thechachman on 2012-09-11
> **BigBaka said:**
> Anyone?

this worked perfectly for me with Lisboa:

wget -nd [https://api.opensuse.org/public/source/home:jluce2:GEO/libecwj/libecwj2-3.3.tar.bz2](https://api.opensuse.org/public/source/home:jluce2:GEO/libecwj/libecwj2-3.3.tar.bz2)
tar -xvjf libecwj2-3.3.tar.bz2
cd libecwj2-3.3
./configure
make
sudo make install

sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable && sudo apt-get update 
sudo apt-get install libgdal-ecw-src build-essential 
sudo gdal-ecw-build /usr/local 
sudo ldconfig

gdalinfo --formats|grep -i ecw

( from [http://gis.stackexchange.com/questions/29281/ecw-on-qgis-1-8-ubuntu-11-10](http://gis.stackexchange.com/questions/29281/ecw-on-qgis-1-8-ubuntu-11-10) )

---

