---
title: "QGIS - downloading and installing"
date: 2012-02-26
forum: General Help
---

### Post by Catlike on 2012-02-26
I do not understand the instructions on   [http://hub.qgis.org/projects/quantum-gis/wiki/Download](http://hub.qgis.org/projects/quantum-gis/wiki/Download)    for downloading QGIS. 
The following quotes are found on the page under the header "Ubuntu" and then "Ubuntu: Release" . I am looking under "Oneiric" .

 Quote: "Add the lines for one of the repositories of the following sections to your /etc/apt/sources.list file, then type: "

What is my "/etc/apt/sources.list" file? How do I find it and open it to add the lines which follow the above instruction? 

By the way, the lines to be typed/added to the above-named file are
sudo apt-get update sudo apt-get install qgis 

Thank you.

---

### Post by raja.genupula on 2012-02-27
```
sudo gedit /etc/apt/sources.list
```
Type it in your terminal and it will open that file . 

NOTE : please dont make any other modification to present lines , just add what ever you wanna add at the bottom of the file , Save and close . 

then in terminal type those commands 
```
sudo apt-get update
sudo apt-get install qgis 
```
All the best .

---

### Post by Herman on 2012-02-27
> By the way, the lines to be typed/added to the above-named file are
sudo apt-get update sudo apt-get install qgis No.
The instructions on that page do look confusing, they're and out of sequence and incomplete. I don't know why they put those at the top. They should be at the bottom because you use those commands last. 
The lines they're trying to tell you to copy and paste into your /etc/apt/sources.list are like:

deb     [http://qgis.org/debian](http://qgis.org/debian) oneiric main 
deb-src [http://qgis.org/debian](http://qgis.org/debian) oneiric main 

But I don't think you need to bother with them anyway. 
There's no need to any command line work or editing of text files  if you're using a recent version of Ubuntu and if you just want the standard 'stable' Copiapo version of QGIS. Just install Quantum GIS from Ubuntu Software Center, QGIS is in the standard repositories now I believe.


If you want the Wroclaw version of QGIS, then that's different, the five commands given a little further down on that page would do the trick for you.
Here they are again in case you have trouble finding them,

sudo apt-get install python-software-properties
sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo apt-get update
sudo apt-get install qgis
sudo apt-get install python-qgis

At the time of writing (28/02/2012), Wroclaw 1.7.4 is the most up to date version recommended for users.
Although it's called 'unstable', the 'unstable' version seems to work perfectly well in Ubuntu. That's the version I'm using right now and I think most other QGIS users would be using it too.
In my personal opinion, running those five commands is the fastest and easiest way to install the latest version of QGIS in Ubuntu.

---

### Post by Catlike on 2012-03-09
Thank you for the very clear instructions. I have just downloaded/installed Wroclaw 1.7.4. Hope to make time soon to try it out.

---

