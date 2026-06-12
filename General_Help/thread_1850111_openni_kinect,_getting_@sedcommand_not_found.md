---
title: "openni_kinect, getting @sed:command not found"
date: 2011-09-25
forum: General Help
---

### Post by deepyogi on 2011-09-25
hi

I'm having issues while trying to install openni_kinect on ubuntu. i'm following the instructions from here: [http://www.ros.org/wiki/openni_kinect](http://www.ros.org/wiki/openni_kinect). i cant get past this step
```
hg clone https://kforge.ros.org/openni/drivers
cd drivers
make 
make install
```when i do make install, i get the following error:
```
sudo: @sed: command not found
make: *** [install_openni] Error 1
```can anyone please help with this? i searched around and came across this [http://ubuntuforums.org/showthread.php?t=1826181](http://ubuntuforums.org/showthread.php?t=1826181) but it didnt help either

---

### Post by desinghkar on 2011-10-14
I have encountered the issue and was able to install the drivers by using 
```
make debian
sudo dpkg -i *.deb
```

---

