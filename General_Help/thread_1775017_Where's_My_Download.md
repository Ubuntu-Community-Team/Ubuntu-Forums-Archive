---
title: "Where's My Download?"
date: 2011-06-04
forum: General Help
---

### Post by Rachel5000 on 2011-06-04
[I][SIZE=2][FONT=Arial Narrow]Help Please...

I'm trying to get the HP Printer software from the HP site:
**HPLIP-3.11.5.run**

 They say that after it's downloaded, to open terminal, and type what they tell me to.  It assumes download is in desktop folder, but it ain't.
 Where does it go by default, if not to the desktop?
Can I change the command from "desktop" to "Downloads"?
Also, (For another time maybe) How do I choose where my downloads go?
Thanks Gang,
Rachel
[/FONT][/SIZE][/I]

---

### Post by Morderwurst on 2011-06-04
[FONT=System][SIZE=2]Try something like this in the terminal

[/SIZE][/FONT][SIZE=2]```
find ~/ -iname 'HPLIP-3.11.5.run'
```This ought to display the location of your file.

You should typically be able to choose the location that I file is saved to when downloading. If not, and if you're using Firefox, go to Edit>preferences in the browser and then navigate to the 'General' tab. You will be able to select the folder where downloads will be saved.[/SIZE]

---

### Post by jocko on 2011-06-04
Have you checked your ~/Downloads folder?

---

### Post by nzjethro on 2011-06-04
To get to your ~/Downloads file in a terminal, type
```
cd Downloads
```
Then, if you need to perform any action from there, just type the filename.

---

### Post by gandaran on 2011-06-04
> **Rachel5000 said:**
> [I][SIZE=2][FONT=Arial Narrow]Help Please...

I'm trying to get the HP Printer software from the HP site:
**HPLIP-3.11.5.run**

 They say that after it's downloaded, to open terminal, and type what they tell me to.  It assumes download is in desktop folder, but it ain't.
 Where does it go by default, if not to the desktop?
Can I change the command from "desktop" to "Downloads"?
Also, (For another time maybe) How do I choose where my downloads go?
Thanks Gang,
Rachel
[/FONT][/SIZE][/I]
you can install the HP software form ubuntu software center, theres no need to download them from hp website, open synaptic package manager and type 'HP' in search box it will show every hp package available to install.

---

