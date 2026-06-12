---
title: "HOW TO: Install Themes and Icon Themes on Ubuntu 11.10/11.04"
date: 2011-12-03
forum: General Help
---

### Post by Spyderkid on 2011-12-03
[SIZE="3"][B][COLOR="DarkOrange"]I bet at some point since Unity you have thought... I could sure do with a different icon theme.

Well now you can with these simple steps![/COLOR][/B][/SIZE]

[COLOR="Blue"][SIZE="3"]Installing an Icon Theme:[/SIZE][/COLOR]

[COLOR="SeaGreen"]**1)**[/COLOR] Install Advanced Settings (gnome-tweak-tool)
   to install run ```
sudo apt-get install gnome-tweak-tool
```


[COLOR="SeaGreen"]**2)**[/COLOR] Find an icon theme you like, from [GnomeLook]("http://gnome-look.org/index.php?xcontentmode=121")


[COLOR="SeaGreen"]**3)**[/COLOR] Then run ```
sudo nautilus
```
   The file browser (nautilus) should pop-up giving you permissions to edit the file system _[COLOR="Red"][SIZE="3"]BE CAREFULL![/SIZE][/COLOR]_ don't delete anything or mess with anything I don't tell you...

Go to the "filesystem" then to "usr" then "share" then "icons" copy your compressed icon theme here...


[COLOR="SeaGreen"]**4)**[/COLOR] Extract it by right-clicking then choosing "extract here" find the folder that was just extracted, double-click on it...


[COLOR="SeaGreen"]**5)**[/COLOR] Then once your inside your extracted folder extract any more compressed files your have inside, and move these back to the "icons" folder.

Now quit the file browser (nautilus) and close the terminal


[COLOR="SeaGreen"]**6)**[/COLOR] find the program Advanced Settings which you installed earlier, browse to "Theme" then choose your "Icon theme" from the list


[COLOR="SeaGreen"]**7)**[/COLOR] DONE! Enjoy your new icon theme!





[COLOR="blue"][SIZE="3"]Installing a GTK Theme...[/SIZE][/COLOR]

[COLOR="SeaGreen"]**1)**[/COLOR] Install Advanced Settings (gnome-tweak-tool)
   to install run ```
sudo apt-get install gnome-tweak-tool
```


[COLOR="SeaGreen"]**2)**[/COLOR] Find a Theme you like from [Gnome Look]("http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=100")


[COLOR="SeaGreen"]**3)**[/COLOR] Go to your home folder, create a new folder called .themes (yep, with the . it will make the folder hidden)


[COLOR="SeaGreen"]**4)**[/COLOR] Press Ctrl+H this will display all the hidden folders, browse to .themes (the folder you just created) and copy your compressed theme into here


[COLOR="SeaGreen"]**5)**[/COLOR] Right-Click on the compressed theme and click "extract here", 

then go into the folder you just extracted and extract any more compressed folders inside


[COLOR="SeaGreen"]**6)**[/COLOR] Quit the file manager (nautilus) and find the application "Advanced Settings) Go to Theme, then choose your theme from the GTK+ Theme option


[COLOR="SeaGreen"]**7)**[/COLOR] DONE! enjoy your theme






**[COLOR="DeepSkyBlue"]If it doesn't work, reply with your problem and a link to your Theme/Icon Theme[/COLOR]**

---

### Post by Spyderkid on 2011-12-04
Will be adding screen-shots :D

---

### Post by Spyderkid on 2011-12-04
added how to change your cursor!!!!!!!

---

### Post by Spyderkid on 2011-12-05
Removed how to change your cursor, I'm makeing a thread with a more simple way

---

### Post by zayastealth on 2011-12-07
I have downloaded this theme and am having trouble installing it.  So far i have downloaded tweak, made folders,extracted, but my themes are not showing up in tweak.

I also did some sudo chown for root so i could extract my themes to to /user/share/themes but this did not work either.

any ideas?


theme is here+
[http://linux.softpedia.com/progDownload/Matrix-Complete-Download-37314.html](http://linux.softpedia.com/progDownload/Matrix-Complete-Download-37314.html)

---

### Post by Spyderkid on 2011-12-08
What i'll do is make you a little script to do it for you, will be like 10 mins

---

### Post by zayastealth on 2011-12-08
thanks

---

### Post by Spyderkid on 2011-12-08
Here you go :) Download the attachment

Just Right click on the file go to Properties then Permissions and tick the "allow executing file as a program"

then double click and choose "run in terminal"

After you've run the script, open Advanced settings (gnome-tweak) and the theme will be there :D

---

### Post by Spyderkid on 2011-12-08
send a reply if it works :) (or doesn't)

---

### Post by zayastealth on 2011-12-08
No go... script ran fine... still nothing in tweak.
Any other Ideas?

---

### Post by BC59 on 2011-12-08
This is a very good guide. The only thing I would say is to use gksudo nautilus to start graphical applications, instead of sudo nautilus, because the Ubuntu Documentation is explicit on this issue.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Spyderkid on 2011-12-08
ok, cheers.

I forgot about that :S

---

### Post by Spyderkid on 2011-12-08
lemme have another look zayastealth

---

### Post by BC59 on 2011-12-08
And another think. To avoid using the root, you can create a ~/home/.icons folder.

---

### Post by Spyderkid on 2011-12-08
it doesn't work with making a .icons i believe?

---

### Post by Spyderkid on 2011-12-08
zayastealth, I think I can get the icon theme only to work for you, im not sure if i can get the gtk theme working :S

---

### Post by BC59 on 2011-12-08
The use of the .icons folder is explained in this thread, second post.

[http://ubuntuforums.org/archive/index.php/t-3757.html](http://ubuntuforums.org/archive/index.php/t-3757.html)

---

### Post by zayastealth on 2011-12-08
thanks for the help.

---

### Post by Spyderkid on 2011-12-09
I'll have a look at the .icons / .themes

Also I'll be making an auto-script :DD

---

