---
title: "ubuntu 12.04 google earth does not start."
date: 2012-08-16
forum: General Help
---

### Post by alvpizz on 2012-08-16
hello! I am using ubuntu 12.04, on a samsung RC530-S02. i have an nvidia optimus video card, so i have installed the bumblebee driver (I don't know if the problem is also related to this). 
i have installed google earth downloading the debian package from google.com and installed it. every thing worked during the installation, but when i try to start the program, nothing happens. 

if i launch it from the terminal, I get chis error:

./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

i would like to have a working google earth on my computer so... how can i solve it?

thanks

---

### Post by Marric on 2012-08-18
install this```

sudo apt-get install ia32-libs
sudo apt-get install lsb-core
```and install this for the fonts
```
sudo apt-get install ttf-mscorefonts-installer
```run the program```
optirun /opt/google/earth/free/google-earth %f
```check this
```
 https://help.ubuntu.com/community/GoogleEarth
```

---

### Post by alvpizz on 2012-08-18
I have given the command you told me, but after that google-earth was no more installed. so I've installed it again, and i also found it in ubuntu software center.. but it is still not working, and i get the same error as before. 
was it a bad idea reinstalling it?

---

### Post by Marric on 2012-08-18
for the installation please use the recommended installation methods on this site
```
https://help.ubuntu.com/community/GoogleEarth
```

---

### Post by Marric on 2012-08-18
and install this
```
sudo apt-get install libgl1-mesa-glx:i386
```

---

### Post by alvpizz on 2012-08-18
oh.. i probably missed saying you that i have a 64bit processor.. sorry

---

### Post by alvpizz on 2012-08-18
the last package was already installed. anyway, i have tryied all of the methods, and none of them is working

---

### Post by Marric on 2012-08-18
Do you still get the same error message?

Install
```
sudo apt-get install lib32nss-mdns 
sudo apt-get install ia32-libs-gtk
```Also found this possibility to start google-earth
```
LD_LIBRARY_PATH=/usr/lib32/nvidia-current/ google-earth
```

---

### Post by xianbei on 2012-08-18
where did you get the install package?

---

### Post by Marric on 2012-08-19
which one?

---

### Post by alvpizz on 2012-08-19
> **xianbei said:**
> where did you get the install package?

i downloaded the install package from he google site.

yesterday i also added the medibuntu repositpry using the terminal command, but if i try to install "googleearth" i get "package not found". 
all in all, no installing way which i founf in che site "https://help.ubuntu.com/community/GoogleEarth" is working until now.

---

### Post by alvpizz on 2012-11-24
surfing the internet, i have found this page, where it was said that someone had solved my same problem by copying the file libGL.so.1 from the directory /usr/lib/i386-linux-gnu/mesa into the directory /opt/google/earth/free, where the file is actually missing. 
because i needed the superuser abilities, i used the terminal and i digited this command:
```
sudo cp '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' '/opt/google/earth/free' 
```
and now google earth is correctly starting.

I need also to add a strange thing that has been happening to me: I've now converted to Ubuntu 12.10, and I've already re-installed it three times. in the previous two times google earth suddenly started working after I had installed some updates (but I still don't know how and why). in fact, the third time i have evidently done something different, and google earth was not running. I have so looked around, and I have fortunately found this page, which was, to my liking, not as notified as her importance would have needed (in fact I can't find it anymore!)

i hope that now this post can solve other people's problems.

---

### Post by joham34 on 2012-12-23
> **alvpizz said:**
> surfing the internet, i have found this page, where it was said that someone had solved my same problem by copying the file libGL.so.1 from the directory /usr/lib/i386-linux-gnu/mesa into the directory /opt/google/earth/free, where the file is actually missing. 
because i needed the superuser abilities, i used the terminal and i digited this command:
```
sudo cp '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' '/opt/google/earth/free' 
```
and now google earth is correctly starting.

I need also to add a strange thing that has been happening to me: I've now converted to Ubuntu 12.10, and I've already re-installed it three times. in the previous two times google earth suddenly started working after I had installed some updates (but I still don't know how and why). in fact, the third time i have evidently done something different, and google earth was not running. I have so looked around, and I have fortunately found this page, which was, to my liking, not as notified as her importance would have needed (in fact I can't find it anymore!)

i hope that now this post can solve other people's problems.

Indeed it did the trick for me too. 
Thank you

---

