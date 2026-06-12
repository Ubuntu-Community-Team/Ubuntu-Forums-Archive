---
title: "Old floppy disks?"
date: 2010-10-08
forum: General Help
---

### Post by UncleMonty on 2010-10-08
Is there anyway of reading old floppy disks on a computer running ubuntu lucid 64 bit please?

---

### Post by UnterUn on 2010-10-08
Jesus Christ are floppy disks still used!? :)

Anyway try:
```
sudo apt-get install gwhere
```

and/or look here [http://linux.about.com/od/linux101/a/desktop04a.htm](http://linux.about.com/od/linux101/a/desktop04a.htm)
also: [http://www.adsb.co.uk/bbc/linux/](http://www.adsb.co.uk/bbc/linux/)

---

### Post by egglestn on 2010-10-08
If you have the hardware on your PC then lucid will/should read them automatically. If not you can but a usb external floppy from PC world or amazon 
[http://www.amazon.co.uk/Iomega-External-Floppy-Drive-Reader/dp/B00027YIHM](http://www.amazon.co.uk/Iomega-External-Floppy-Drive-Reader/dp/B00027YIHM)
I tried a similar one and it worked out of the box.  YMMV
Hope this helps

---

### Post by UncleMonty on 2010-10-08
> **UnterUn said:**
> Jesus Christ are floppy disks still used!? :)

Anyway try:
```
sudo apt-get install gwhere
```

and/or look here [http://linux.about.com/od/linux101/a/desktop04a.htm](http://linux.about.com/od/linux101/a/desktop04a.htm)
also: [http://www.adsb.co.uk/bbc/linux/](http://www.adsb.co.uk/bbc/linux/)

Yeah I know lol. A friend of the family wants them and I figured I should clean them out first before donating them. I've installed gwhere. What next please?

---

### Post by UnterUn on 2010-10-08
> **UncleMonty said:**
> Yeah I know lol. A friend of the family wants them and I figured I should clean them out first before donating them. I've installed gwhere. What next please?
You *just want to format them* rather then look at the files? :P Okay do:
```
sudo apt-get install kfloppy
```and it should be self explanatory when you load the program up.

Then remove that last one (I think that's to look through files, but I've yet to use it unlike kfloppy)
```
sudo apt-get remove gwhere
```And if you want you can remove kfloppy in a similar way

---

### Post by Yellow Pasque on 2010-10-08
```
sudo modprobe floppy
```

---

