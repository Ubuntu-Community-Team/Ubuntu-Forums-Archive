---
title: "MS fonts"
date: 2011-06-29
forum: General Help
---

### Post by northwestern on 2011-06-29
[SIZE=2]Please help

I have downloaded TTF-mscorefonts installer onto my system (Ubuntu 11.04)  but they appear nowhere on my system in the appearance/preferences/fonts section.

Thanks for your help
Northwestern[/SIZE]

---

### Post by nomko on 2011-06-29
Check if you have the folder msttfcorefonts in the folder /usr/share/fonts. Normally in this folder all fonts installed by synaptic are placed there.

---

### Post by grahammechanical on 2011-06-29
On my system it is usr/share/fonts/truetype/msttcorefonts.

Regards

---

### Post by nomko on 2011-06-30
> **grahammechanical said:**
> On my system it is usr/share/fonts/truetype/msttcorefonts.
 
Regards
 
Then the MS Core fonts are installed in the correct folder. Normally it would be visible for the whole system.
 
Try this:
- open nautilus
- press Ctrl+H (this makes all hidden files and folders visible)
- check if you have a folder called .fonts (be aware of the . (dot) at the beginning of the folder name)
- If you have this folder, okay. If you dant have it, create this folder.
 
Then copy all the contents of the usr/share/fonts/truetype/msttcorefonts folder into the /home/{username}/.font folder.
 
Does your system see those fonts then?

---

### Post by jtappin on 2011-07-27
Might be worth re-installing the package. On my newly installed Natty system, the package was installed but the fonts were not there. I just did a re-install and it downloaded the font files and now they work. (I did not have the same problem with a machine I upgraded from Maverick).

I don't know if any of the package installers times out the request to agree to the EULA, as I might well have set up a Gig or so of downloads/installs  and left the machine to get on with it.

---

### Post by oldos2er on 2011-07-28
The installer should update the font cache, but if for some reason it doesn't you can run ```
sudo fc-cache -f
```

---

