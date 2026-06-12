---
title: "usb pendrive is not opening"
date: 2011-01-24
forum: General Help
---

### Post by suryak on 2011-01-24
Actually when I started format under ' FAT32 All Systems '.. it started and after some time it showed an error and close.. it pendrive unmouted automatically .. 
I tried with another USB port .. It didn't show up on desktop but there in my computer.. 
but its not opening there.. 
When I right clicked on it.. it not showing any options that a pendive icon usually shows like format.. 

what is the problem.. ?? 
I'm just a beginner to linux ..

---

### Post by earthmeLon on 2011-01-24
Have you tried viewing your available drives in a program such as [gparted]("http://gparted.sourceforge.net/documentation.php")?

You can install gparted by opening up a terminal and running the following command:
```
sudo apt-get install gparted
```


You can run it by typing gparted in the same terminal, or by going to Administration>gparted.
[COLOR="Red"]This will open *ALL* of your connected HDD's.  Make sure not to mess up your HDD with linux on it![/COLOR]

On the top right of gparted will show something like /dev/sda or /dev/hda.  It's a 'combo-box' that you can click and select each harddrive detected on your system. 

See if it shows up there and if there is anything you can do within gparted to get your USB thumb drive working.

---

