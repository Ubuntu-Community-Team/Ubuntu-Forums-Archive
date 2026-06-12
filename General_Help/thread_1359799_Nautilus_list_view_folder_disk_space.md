---
title: "Nautilus list view: folder disk space"
date: 2009-12-20
forum: General Help
---

### Post by maszy on 2009-12-20
Good morning everyone,
I'd like to see in nautilus list view how much disk space the folders are using.
Is it possible?

Thanks
Greetings

---

### Post by lmarmisa on 2009-12-20
This is very easy. Symply, select the folder (left button of the mouse), click right button and Properties. You can see there how much disk space that folder is using.

---

### Post by wojox on 2009-12-20
You can't have it show up automatically. If you go to Edit > Preferences > List Columns you can see your options.

---

### Post by maszy on 2009-12-20
> **lmarmisa said:**
> This is very easy. Symply, select the folder (left button of the mouse), click right button and Properties. You can see there how much disk space that folder is using.

I know this method but I want to see all the disk space space of each folder in a column

---

### Post by maszy on 2009-12-20
> **wojox said:**
> You can't have it show up automatically. If you go to Edit > Preferences > List Columns you can see your options.

Yes but in the "Dimension" column you can see the number of file included, I want to see how much Mb the folder is (sorry for the bad eng)
Thanks

---

### Post by drs305 on 2009-12-20
For a one-time check, you can use Disk Usage Analyzer to see folder sizes (Applications, Accessories, Disk Usage Analyzer). I am not a big DUA fan but you can click on "Scan a folder" and then get the folder/subfolder sizes in this manner.

---

### Post by maszy on 2009-12-20
> **drs305 said:**
> For a one-time check, you can use Disk Usage Analyzer to see folder sizes (Applications, Accessories, Disk Usage Analyzer). I am not a big DUA fan but you can click on "Scan a folder" and then get the folder/subfolder sizes in this manner.

Thanks for the reply but I'd like see the folders space in Mb in nautilus if this is possibile:
I have my dowload folder where there are 200 folders with a lot of different file inside, and I need to see the space of each folder quickly

---

### Post by drs305 on 2009-12-20
> **maszy said:**
> Thanks for the reply but I'd like see the folders space in Mb in nautilus if this is possibile:
I have my dowload folder where there are 200 folders with a lot of different file inside, and I need to see the space of each folder quickly

I use PCManFM, which does what you want:
```
sudo apt-get install pcmanfm
```

I know it's not nautilus, but it's an excellent file browser when Nautilus can't do what you want.

Added: I checked gconf-editor and do not see any default settings that will do what you would like.

---

### Post by maszy on 2009-12-20
I'll try this thank you, but I think that a simple feature like this could be integrated in nautilus, maybe editing some pref file... hope someone knows I'd like to try

---

### Post by maszy on 2009-12-20
Just tryed but the space of each folder is 4,1 Kb with Pcman 
I want to se the space of the included files

---

### Post by maszy on 2009-12-20
I found the command du -h in the terminal but nothing about nautilus I can't belvieve that there isn't a solution :(

---

