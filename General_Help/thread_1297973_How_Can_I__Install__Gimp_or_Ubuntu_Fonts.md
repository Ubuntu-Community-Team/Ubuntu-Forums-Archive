---
title: "How Can I  Install  Gimp or Ubuntu Fonts?"
date: 2009-10-22
forum: General Help
---

### Post by wapotter on 2009-10-22
[FONT=Times New Roman][SIZE=3]I downloaded a Gimp fonts freefonts-0.10.tar.gz package which has an installation guide that reads: 


Installation for X11 [/SIZE][/FONT]
[LIST]
[*][SIZE=3][FONT=Times New Roman]**Change to /usr/X11/lib/fonts** [/FONT][/SIZE]
[*][SIZE=3][FONT=Times New Roman]**Untar the archive freefonts-0.10.tar.gz** {*How?*} [/FONT][/SIZE]
[*]**[SIZE=3][FONT=Times New Roman]Give the the follwing commands to make X11 accept the new fonts[/FONT][/SIZE]**
[/LIST]**[SIZE=3][FONT=Times New Roman]xset fp+ /usr/X11/lib/fonts/freefont[/FONT][/SIZE]**

**[SIZE=3][FONT=Times New Roman]xset fp rehash[/FONT][/SIZE]** 
[LIST]
[*][SIZE=3][FONT=Times New Roman]**The fonts are available under X11.** [/FONT][/SIZE]
[/LIST]**[SIZE=3][FONT=Times New Roman]Check them out by running “xfontsel” for example. [/FONT][/SIZE]**


[SIZE=3][FONT=Times New Roman]Installation for Ghostscript [/FONT][/SIZE]
[LIST]
[*]**[SIZE=3][FONT=Times New Roman]Change to /usr/lib/ghostscript [/FONT][/SIZE]**
[*][SIZE=3][FONT=Times New Roman]**Save the file “Fontmap” **{*What's a Fontmap file?*}[/FONT][/SIZE]
[*][SIZE=3][FONT=Times New Roman]**e.g. cp Fontmap Fontmap.old **{*Do I have to type this command?*}[/FONT][/SIZE]
[*]**[SIZE=3][FONT=Times New Roman]Copy the new Fontmap from the archive [/FONT][/SIZE]**
[/LIST]**[SIZE=3][FONT=Times New Roman]If you have installed it already in X11 do[/FONT][/SIZE]**

**[SIZE=3][FONT=Times New Roman]cp /usr/lib/fonts/freefont/Fontmap[/FONT][/SIZE]** 
[LIST]
[*]**[SIZE=3][FONT=Times New Roman]Copy necessary fonts to the ghostscript directory[/FONT][/SIZE]**
[/LIST][SIZE=3][FONT=Times New Roman]**(or use links) **{*How to use links?*}[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**cp /usr/libs/freefont/tempo*pfb font**[/FONT][/SIZE][SIZE=3][FONT=Times New Roman]** cp /usr/libs/freefont/baskvl*pfb font **{*Do I have to copy all of them individually?*}[/FONT][/SIZE]

[FONT=Times New Roman][SIZE=3]Is this how all .pfb and .ttf gimp/Ubuntu fonts are installed? Are we always required to install fonts into both directories? In my Filesystem directory pre-installed .pfb files are stored in the /usr/share/fonts/X11/Type1, /usr/share/fonts/type1/gsfonts and /var/lib/defoma/gs.d/dirs/fonts directories, is this where all fonts are automatically stored once they are installed? How can I install fonts in GUI, as a root user?[/SIZE][/FONT]

---

### Post by MarkStarCrashes on 2009-10-22
I know it's not really an answer to your question, but have you checked out Fonty Python (Available under Applications>Add/Remove...)?

It's a quick way to add/remove new fonts without having them permanently installed.

---

### Post by razorboy5 on 2009-10-22
not sure if this will answer ur question either but when i needed to install a few fonts for Conky instructions told me to

1. make a folder named .fonts into home
2. add the fonts u want into that folder
3. restart (not sure if this is required)

tried with a few other fonts after that and i can use all of them from Office (never tried GIMP)

---

### Post by rednano12 on 2009-10-22
Just follow the instructions that razorboy5 showed earlier. Any font that works with Windows should work with 'Buntu. However, after you add the fonts, you have to restart whatever program is going to use them.

---

### Post by wbjoly on 2009-11-11
razorboy5:
It does work for GIMP.  Thanks for posting the instructions.  So much easier that what my ex, who set up my system, said I was going to have to do.

---

