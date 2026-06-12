---
title: "Problems in installing nvidia, how do i stop X server?"
date: 2010-03-04
forum: General Help
---

### Post by stevpm on 2010-03-04
[IMG]http://i784.photobucket.com/albums/yy121/stymo8/nvidia1.png[/IMG]

---

### Post by stevpm on 2010-03-04
then hwen i accept..it takes me here...


[IMG]http://i784.photobucket.com/albums/yy121/stymo8/nvidia2exitXserver.png[/IMG]

---

### Post by stevpm on 2010-03-04
plz help!!!!

---

### Post by realzippy on 2010-03-04
You had to log out,then log in at shell.(alt+ctrl+F1)
then type:

**sudo service gdm stop**

or,if not on Karmic:

**sudo /etc/init.d/gdm stop**

but message complains about missing NVIDIA card.If you have an old nvidia card,use older driver.What card you have?

**lspci**

should show you...

---

### Post by stevpm on 2010-03-06
[IMG]http://i784.photobucket.com/albums/yy121/stymo8/terminal.png[/IMG]that is wat it gives me bro... let me add more images....i tried your way i failed.

---

### Post by stevpm on 2010-03-06
[IMG]http://i784.photobucket.com/albums/yy121/stymo8/nohardwaredrivers.png[/IMG]

---

### Post by gradinaruvasile on 2010-03-06
Your lspci said you have an Intel integrated card...
Where did you get the nvidia?

---

### Post by stevpm on 2010-03-06
[IMG]http://i784.photobucket.com/albums/yy121/stymo8/Graphiccard.png[/IMG]

---

### Post by stevpm on 2010-03-06
i downloaded it offline. So wat can i do? i want to be able to experience 3D effects

---

### Post by gradinaruvasile on 2010-03-06
Well. Here it is:

Nvidia is a video card chip maker. Naturally the nvidia drivers are made for nvidia chipsets.

Now. You have an Intel video card (and it has its drivers, they already included in  Ubuntu and are used automatically). You cannot use nvidia drivers for an Intel card. 

The only way you can use nvidia drivers if you buy an nvidia video card.

Intel video cards are integrated in the computer's mainboard and they suck at 3d.

Long story short: you cannot use the nvidia drivers because you dont have nvidia video card.

---

