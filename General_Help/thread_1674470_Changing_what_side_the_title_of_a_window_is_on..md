---
title: "Changing what side the title of a window is on."
date: 2011-01-23
forum: General Help
---

### Post by besby11 on 2011-01-23
Hello forums,


I have been messing about with my themes lately and was wondering if it was possible to force the title of a window to display on the right side and have the buttons on the right. I'm already aware of using gconf-edit to change the order and position of the buttons but I can't seem to figure out how to move the title. Thanks!



Besby11

---

### Post by yiannis66 on 2011-01-24
Open the gconf-editor at the /apps/metacity/general/button_layout put this line 
"menu:minimize,maximize,spacer,close"

---

### Post by Krytarik on 2011-01-24
Besby11, I would allege that the title itself is always in the middle of the title bar, I haven't seen any different so far.

---

### Post by besby11 on 2011-01-24
I've attached an image to make this a little bit easier to explain. My problem is that in my current theme (the top one) my window title is scrunched up next to my window buttons. What I would like to do is move it to the opposite side of the window bar (like the bottom one).

---

### Post by Krytarik on 2011-01-24
Ok, convinced.;)

It's an emerald theme, right?

To change the titlebar's arrangement, go to "System -> Preferences -> Emerald Theme Manager", choose the theme you want to edit, click the tab "Edit Themes", then the tab "Titlebar", then on the right side "Title-bar Object Layout" is the relevant option.

---

### Post by besby11 on 2011-01-24
Actually these particular two themes use gtk2 and metacity. I'm not exactly sure how to edit the parameters to move the text. I'm guessing it has something to do with gconf-edit if anything.

---

### Post by Krytarik on 2011-01-24
Oh, don't look like metacity frames, I thought those diagonal mirror effect is only possible with emerald.

It's a bit more complicated then. I don't know so far, which is the relevant option.
You have to edit the metacity theme configuration manually, the file is called "metacity-theme-1.xml" and is located in the "metacity-1" subdir of the themes' dir. Either in ~/.themes or /usr/share/themes, depending on how you installed them.

Open the config files of both themes and compare it's options regarding the keyword "title".

Please post the URL of the theme with the right-sided title, I will also have a look then.

Good luck!

---

### Post by besby11 on 2011-01-24
Thanks, here is the link to the theme with the title on the right side. [http://gnome-look.org/content/show.php/Elegant+Brit?content=74553](http://gnome-look.org/content/show.php/Elegant+Brit?content=74553) .

---

### Post by Krytarik on 2011-01-24
So, the clue is in here:
```
<draw_ops name="draw_title_text_normal">
    <title x="((width - title_width)-5)" y="(height - title_height) / 2" color="#FFFFFF"/>
</draw_ops>

<draw_ops name="draw_title_text_inactive">
    <title x="((width - title_width)-5)" y="(height - title_height) / 2" color="#47494d"/>
</draw_ops>

```
as opposed to those in the Macbuntu, which I've used for testing:
```
<draw_ops name="title-text-focused">
  <clip x="0" y="0" width="width" height="height"/>
<icon  x=[COLOR=Blue]"(width - title_width - mini_icon_width - IconSpacing) / 2"[/COLOR]
         y="(height-mini_icon_height) / 2"
         width="mini_icon_width" height="mini_icon_height"/>
<title color="#dddddd" x=[COLOR=Red]"(width - title_width) / 2 +0"[/COLOR] y="(height - title_height) / 2 + 1"/>
<title color="#3c3c3c" x=[COLOR=Red]"(width - title_width) / 2"[/COLOR] y="(height - title_height) / 2"/>
</draw_ops>

<draw_ops name="title-text-unfocused">
  <clip x="0" y="0" width="width" height="height"/>
<icon  x=[COLOR=Blue]"(width - title_width - mini_icon_width - IconSpacing) / 2"[/COLOR]
         y="(height-mini_icon_height) / 2"
         width="mini_icon_width" height="mini_icon_height"
     alpha="0.5"/>
<title color="#dddddd" x=[COLOR=Red]"(width - title_width) / 2 +0"[/COLOR] y="(height - title_height) / 2 + 1"/>
<title color="#3c3c3c" x=[COLOR=Red]"(width - title_width) / 2"[/COLOR] y="(height - title_height) / 2"/>
</draw_ops>

```
It's a calculation where the title will start.
You can spare the additional "(", like this:
```
<title color="#cecece" x=[COLOR=Red]"width - title_width - 5"[/COLOR] y="(height - title_height) / 2 + 1"/>
```
Good luck!

PS: Great, I've learned some again!;)

---

