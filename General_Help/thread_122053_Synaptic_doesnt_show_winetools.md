---
title: "Synaptic doesnt show winetools"
date: 2006-01-26
forum: General Help
---

### Post by Vash on 2006-01-26
Ok so i added deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ which is suppose to give you the option of installing wine and winetools. Wine isntalled just fine but winetools doesnt even show up in synaptic i have tried apt-get but im such a newbie that that didnt work for me. The wine repositories seem to fail in the synaptic log that shows which repo's are being loaded. The funny thing is that just last week i used them with Mepis. I dont know what to do? I have only been using linux for 2 weeks constantly. I had fedora core 4 a couple of months ago but ubuntu is the best distro ive tried so far, please someone help!  Thank You in advance for your help.

---

### Post by kwaanens on 2006-01-26
Winetools appear to have disappeared from that repo. You have to ask the wine-maintainers about why.

wine.sourceforge.net is a server experiencing way too much traffic, so they're very often down. I'm getting failed messages on these repos too.
However, you could surf to wine.sourceforge.net/apt and manually download the files you want (.deb-files), and then install them in console with
$ dpkg -i /path_to_package/package_name.deb

- Ketil

---

### Post by dcstar on 2006-01-26
[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

---

### Post by Vash on 2006-01-26
Ok thanks guys looks like im gona have to compile it myself because the deb package is not present. Ill see how that goes i have never compiled any packages. Thank You

---

### Post by dcstar on 2006-01-26
[QUOTE=Vash]Ok thanks guys looks like im gona have to compile it myself because the deb package is not present. Ill see how that goes i have never compiled any packages. Thank You[/QUOTE]
There should be a HOWTO on that in these forums (somewhere), do a search and you could save yourself a lot of time (and hassles........)

---

