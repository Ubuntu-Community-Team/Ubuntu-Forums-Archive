---
title: "Change Image Icons of FileTypes"
date: 2009-10-27
forum: General Help
---

### Post by satish_j on 2009-10-27
How can one modify the image icon of Filetypes in Ubuntu??
Like,if i want to change the same for all PDF documents,then how to do it?
I successfully managed to change it for 1 pdf file by going to File--Properties-click Icon--Browse to /usr/shares/icons..folder and then selecting an adobe.png file.
The icon of selected file changed,but remaining pdf files are still showing the old default icons..
Someone pls help...

---

### Post by martrn on 2009-10-27
> **satish_j said:**
> How can one modify the image icon of Filetypes in Ubuntu??Like,if i want to change the same for all PDF documents,then how to do it?

Navigate to your directory /usr/share/themes/yourthemename , where yourthemename is the name of the theme your are currently using and you will see the pre-choosen icon for the type of file your are viewing.  If you want to put a new icon there it should change the icon for every instance of that item.

See: [http://live.gnome.org/GnomeArt/Tutorials/IconThemes]("http://live.gnome.org/GnomeArt/Tutorials/IconThemes") for more info about icon themes.

Added: I just realise you also need to change ever instance such at /24x24  /32x32  /48x48  /64x64  and /scalable

---

### Post by satish_j on 2009-10-27
I checked /usr/share/themes/yourthemename and there are no icons there..Only 2 folders and index.theme file.
I cannot find any logical entry in this theme file that can be edited...

---

### Post by martrn on 2009-10-27
> **satish_j said:**
> I checked /usr/share/themes/yourthemename and there are no icons there..Only 2 folders and index.theme file. I cannot find any logical entry in this theme file that can be edited...

If there are not any icons of that name/type then it would defualt to the gnome default icons at /usr/share/icons/gnome/  .

You would also need to change every instance of the icon appearing at the directory locations /16x16  /22x22 /24x24 /32x32 /48x48 /64x64 and /scalable .

I hope that helps.

---

### Post by satish_j on 2009-10-28
> **martrn said:**
> If there are not any icons of that name/type then it would defualt to the gnome default icons at /usr/share/icons/gnome/  .

You would also need to change every instance of the icon appearing at the directory locations /16x16  /22x22 /24x24 /32x32 /48x48 /64x64 and /scalable .

I hope that helps.

Can you pls be more elaborate.I need to apply acrobat icon to ALL the pdf files in my system.
How can i achieve that??
I can see there are icons in each of the above folders,but it is really very difficult to understand.
There should be a standard procedure.Like if i want to use a diff icon for doc files,then the procedure to be followed should be same for these as well..

---

### Post by martrn on 2009-10-28
> **satish_j said:**
> Can you pls be more elaborate.I need to apply acrobat icon to ALL the pdf files in my system. How can i achieve that??
I can see there are icons in each of the above folders,but it is really very difficult to understand. There should be a standard procedure.Like if i want to use a diff icon for doc files,then the procedure to be followed should be same for these as well..

I can elaborate, what I am saying but don't think it will extend what I have already said.  I have read and understand what you have said.

The standard procedure for a gnome desktop is to let [Metacity]("https://help.ubuntu.com/community/Metacity") handle its themes eg icons winows boarders etc. etc.

When gnome loads it will load Metacity.  Metacity will look at the folder /usr/share/themes folder, for a rules file that will tell Metacity and gnome how to display multiple things including icons.  Metacity will also look at /homeyourusername/.themes folder for additional rules.

Every time you change a theme it will change the icon for .pdf's or portable document formats, so every single theme has a diffrent icon set.

I suggest, you just change your theme, because even if you modified it yourself and changed the icon, next time your icons set get updated you will need to change it again, and its not easy.

I can not answer your question becuase :

1.  I do not know what theme you are using.
2.  I do not know what icon set you are using.
3.  I do not know what the index.theme file looks like for the theme you have chosen. (need the answer to 1 first).

I sudgest you just change your theme to an icon set you like.
System > Preferences > Appearance

---

### Post by satish_j on 2009-10-28
well,all pdf files are now showing proper acrobat icon.
I selected the 'customize' button in themes window---Icon tab--and selected _crystal SVG_ and then the icons for all the file types were changed..
I understood that there are pre-defined sets of Icons which gives different icons for diff file types.
Just wanted to know whether it is possible(and easy to implement)my own set of icons for each file type.
eg.the above setting of crystal svg solved pdf files icon issue,but the doc and xls files are still showing the default gnome type icon.

---

