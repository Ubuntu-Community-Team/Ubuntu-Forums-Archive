---
title: "a offline users woes"
date: 2006-04-16
forum: General Help
---

### Post by newbietolinux on 2006-04-16
I am a Home Desktop User who moved from Windows to Ubuntu. I want to install the multimedia plugins and dvd playback for my Ubuntu 5.10. But the problem is that I donot have an internet connection. But I can download the required files from another computer and get it to my computer. Please tell me the links to the files that I have to download. I would be very thankful if you could also tell me a way to get these files working.
Please consider this as a general problem. Many users like me donot have an internet connection on the computer on which the are installing Ubuntu. But they can download the required files from elsewhere. Can you do anything to make the lives of these souls easier. 
Ubuntu developers please, please look onto this matter.

---

### Post by sYs^ on 2006-04-16
You can install a .deb package with this command:

sudo dpkg -i /location/randompackage.deb

But I dont know from where could you get those packages, may you want to read this:
[https://wiki.ubuntu.com/PackageCDs](https://wiki.ubuntu.com/PackageCDs)
or try a dvd release: [http://nginyang.uvt.nl/breezy/](http://nginyang.uvt.nl/breezy/)

---

### Post by Ramses de Norre on 2006-04-16
It wont be in the dvd version, ubuntu just doen't ship with proprietary codecs..
But your repo's are just url's, you can find the packages at those sites (you'll need to download all the dependencies dpkg asks for from there too and install them.)

---

### Post by PriceChild on 2006-04-16
For other packages, you can go to:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

download deb files and copy them to his computer.

dpkg -i <<name>>.deb

Will install them :)

---

### Post by Gray. on 2006-04-16
Try searching for apt-cd or something along those lines. You basically download all the packages you may require (and their dependencies), burn them to a CD, then use ```
apt-cdrom add
``` to add them the cd to your sources.list.

Not a very good guide, but if you search you should get more information.

Good luck!

---

