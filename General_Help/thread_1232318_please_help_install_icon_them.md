---
title: "please help install icon them"
date: 2009-08-05
forum: General Help
---

### Post by parkadodge on 2009-08-05
im pretty new to linux as a whole and am using jaunty. im trying to install an icon them, but the directions im getting either dont work or im an idiot. i have it placed in home folder/ icons. these are the directions i have.
1. Go to /your_home_folder/.icons/ACYL_Icon_Theme_0.6.1.

There should be a file there that is named script.sh.

2. Double click on it and select run in terminal. (If you select "run" it might break the icons, happened to me once)

1&2(alt). The two steps above can be done in the terminal by typing:

cd ~/.icons/ACYL_Icon_Theme_0.6.1/
bash script.sh

Now a terminal should pop up and show you a menu where you can choose what action you want to preform.

however whin i double click it opens in gedit. so i cant click run in terminal. and when i type it in the terminal it just says no such file found what am i doing wrong???

---

### Post by credobyte on 2009-08-05
```
cd $HOME/.icons/ACYL_Icon_Theme_0.6.1/ && ./script.sh
```

---

### Post by parkadodge on 2009-08-05
i copied pasted and still says no such file

---

### Post by credobyte on 2009-08-05
> **parkadodge said:**
> i copied pasted and still says no such file

Show us the output of:
```
cd $HOME/.icons/ACYL_Icon_Theme_0.6.1 && ls -al
```

---

### Post by tjwoosta on 2009-08-05
Could you please link to the icon pack that you are trying to install, so we can get a better understanding?

Also, I dont know if this is just a typo in you post, but I noticed you said  home folder/ icons, when it should be home folder/.icons

---

### Post by parkadodge on 2009-08-05
output just says no such file
link is [http://www.gnome-look.org/content/show.php?content=102435&forumpage=0](http://www.gnome-look.org/content/show.php?content=102435&forumpage=0)
and as far as the typo file is named icons but doesnt work with or without the dot

---

### Post by stuffystuff200681 on 2009-08-05
i don't think you made it executable (one of those must know linux security measures:P)

```
cd ~/.icons/ACYL_Icon_Theme_0.6.1/
chmod +x ./script.sh
./script.sh
```
add "sudo" when you get the "Permission Denied" "Resource Temporarily Available" error ](*,)

or use nautilus and right-click the file and select "properties" and under permisions choose "allow executing file as program" then run in terminal
[IMG]http://ma65p.files.wordpress.com/2008/07/screenshot-jre-1_5_0_12-linux-i586-copybin-properties.png[/IMG]

 Have a nice day:D
:popcorn:

EDIT:nice icon set choice by the way!! :P

---

### Post by credobyte on 2009-08-05
The problem is that you have script.sh~, not script.sh !
Remove ~ symbol and try running the whole process again ..

---

### Post by stuffystuff200681 on 2009-08-05
> **credobyte said:**
> The problem is that you have script.sh~, not script.sh !
Remove ~ symbol and try running the whole process again ..
i believe he did it correctly (try following my advice in this one, new to linux and happens to me allot) just not executable :!:
> cd ~/.icons/ACYL_Icon_Theme_0.6.1/
bash script.sh
AND

> Code:

cd $HOME/.icons/ACYL_Icon_Theme_0.6.1/ && ./script.sh


---

### Post by parkadodge on 2009-08-05
i have script.sh
and my nautilus looks totally different so i guess its just above me couldnt even copy paste

---

### Post by stuffystuff200681 on 2009-08-05
another thing is that you might have to do is open it from the terminal

downloaded it and it installed fine just make sure you choose "**_run in terminal_**" NOT "Display" 

"Display" opens it for editing
[IMG]http://i30.tinypic.com/2r3b0g7.png[/IMG]

again Have a nice day

:popcorn:

---

### Post by stuffystuff200681 on 2009-08-05
> **parkadodge said:**
> i have script.sh
and my nautilus looks totally different so i guess its just above me couldnt even copy paste
Are you using KDE? 
if you are then i don't know what to do

---

### Post by stuffystuff200681 on 2009-08-05
this is how the icon theme looks on my desktop
[IMG]http://i29.tinypic.com/27yn7ec.png[/IMG]

---

### Post by parkadodge on 2009-08-05
im not getting what you are i have a folder titled ACYL_con_theme_0.6.1.tar.bz2 when i open it i get a series of other things
such as 

scalable
icon.theme.cache
witch goes on for like 10 files i dont get the option to execute anything it just automatically goes to gedit

---

### Post by parkadodge on 2009-08-05
im totally a retard i forgot to extract the file my bad sorry i took up your time thanks for the help

---

### Post by parkadodge on 2009-08-05
well after i opened it in terminal and set my prefs it didnt change anything

---

### Post by stuffystuff200681 on 2009-08-05
NO PROBLEM, this is what linux is about (small mistakes that you realize later:D)

---

### Post by stuffystuff200681 on 2009-08-05
> **parkadodge said:**
> well after i opened it in terminal and set my prefs it didnt change anything
did you give it some time?
this script depends upon restarting gnome so wait about 10 to 20 seconds

---

