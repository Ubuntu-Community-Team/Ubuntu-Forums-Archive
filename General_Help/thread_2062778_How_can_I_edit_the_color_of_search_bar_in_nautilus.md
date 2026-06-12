---
title: "How can I edit the color of search bar in nautilus gtk3?"
date: 2012-09-25
forum: General Help
---

### Post by madinc on 2012-09-25
i want to change the search bar in nautilus to purple but i don't know how this is my first theme still don't know my way around.

you can see image [here]("https://dl.dropbox.com/u/2078155/Screenshot%20from%202012-09-25%2021%3A51%3A03.png")

---

### Post by Frogs Hair on 2012-09-25
I don't think GTK 3.xx is easy but you can start here.  [http://worldofgnome.org/making-gtk3-themes-part-2-the-gtk-css-and-gtk-widgets-css-files/](http://worldofgnome.org/making-gtk3-themes-part-2-the-gtk-css-and-gtk-widgets-css-files/)

---

### Post by madinc on 2012-09-25
thanks man i will take a deep look in that now i have some place to start lol.

---

### Post by vasa1 on 2012-09-25
> **madinc said:**
> i want to change the search bar in nautilus to purple but i don't know how this is my first theme still don't know my way around.

you can see image [here]("https://dl.dropbox.com/u/2078155/Screenshot%20from%202012-09-25%2021%3A51%3A03.png")
Are you wanting to remove the whitish part in the image? Most everything else _is_ purple.

---

### Post by madinc on 2012-09-26
> **vasa1 said:**
> Are you wanting to remove the whitish part in the image? Most everything else _is_ purple.

thats exactly what i want to do can you help me?

---

### Post by vasa1 on 2012-09-26
> **madinc said:**
> thats exactly what i want to do can you help me?
Which theme are you using? Which desktop environment? In any case, I'll take a look.

---

### Post by madinc on 2012-09-26
i am tweaking ambiance and i am using unity.

---

### Post by vasa1 on 2012-09-26
> **madinc said:**
> i am tweaking ambiance and i am using unity.
To my mind, it appear that you need to look at bg_color in ~/.themes/Ambiance/gtk-3.0/gtk.css or the same file in /usr/share/themes/Ambiance/gtk-3.0.

---

### Post by madinc on 2012-09-26
@define-color bg_color #f2f1f0

this is what i have i change to purple but no result
if you want i can post the css files?

---

### Post by vasa1 on 2012-09-26
> **madinc said:**
> @define-color bg_color #f2f1f0

this is what i have i change to purple but no result
if you want i can post the css files?
Yes, you can paste the gtk.css file between code tags:
```
your stuff here
```

---

### Post by madinc on 2012-09-26
> **vasa1 said:**
> Yes, you can paste the gtk.css file between code tags:
```
your stuff here
```

```
/* default color scheme */
@define-color bg_color #f2f1f0;
@define-color fg_color #4c4c4c;
@define-color base_color #363636;
@define-color text_color #ffffff;
@define-color selected_bg_color #a020f0;
@define-color selected_fg_color #363636;
@define-color tooltip_bg_color #000000;
@define-color tooltip_fg_color #363636;

/* misc colors used by gtk+ */
@define-color info_fg_color rgb (181, 171, 156);
@define-color info_bg_color rgb (252, 252, 189);
@define-color warning_fg_color rgb (173, 120, 41);
@define-color warning_bg_color rgb (250, 173, 61);
@define-color question_fg_color rgb (97, 122, 214);
@define-color question_bg_color rgb (138, 173, 212);
@define-color error_fg_color rgb (166, 38, 38);
@define-color error_bg_color rgb (237, 54, 54);
@define-color link_color #a020f0;
@define-color error_color #cc0000;

/* theme common colors */
@define-color button_bg_color shade (#363636, 1.06);
@define-color button_insensitive_bg_color mix (@button_bg_color, @bg_color, 0.6);
@define-color dark_bg_color #3c3b37;
@define-color dark_fg_color #dfdbd2;
@define-color transparent rgba (0, 0, 0, 0);

@import url("gtk-widgets.css");
@import url("apps/gedit.css");
@import url("apps/gnome-panel.css");
@import url("apps/gnome-terminal.css");
@import url("apps/nautilus.css");
@import url("apps/unity.css");
@import url("apps/unity-greeter.css");
```

---

### Post by vasa1 on 2012-09-26
In order to get changes to take effect you need to switch to a different theme and back. Sometimes, you may even need to **log out and log in again**.

BTW, you can un-SOLVE the thread the same way you marked in SOLVED.

---

### Post by madinc on 2012-09-26
> **vasa1 said:**
> In order to get changes to take effect you need to switch to a different theme and back. Sometimes, you may even need to **log out and log in again**.

BTW, you can un-SOLVE the thread the same way you marked in SOLVED.

i did log out and log in.

---

### Post by vasa1 on 2012-09-26
> **madinc said:**
> i did log out and log in.

What is the path of the file you are editing?

---

### Post by madinc on 2012-09-26
> **vasa1 said:**
> What is the path of the file you are editing?

/usr/share/themes/Ambiance-Purple/gtk-3.0

---

### Post by madinc on 2012-09-26
> **joysmith said:**
> Hey i have just same situation thats exactly what i want to do?

good to see i'm not alone! lol

---

### Post by vasa1 on 2012-09-26
> **madinc said:**
> /usr/share/themes/Ambiance-Purple/gtk-3.0
Hmmm ... Don't know what suggest. **Plus this site is currently so slow for me that I going for a long walk**

---

### Post by madinc on 2012-09-26
> **vasa1 said:**
> Hmmm ... Don't know what suggest. **Plus this site is currently so slow for me that I going for a long walk**

well thanks for trying anyway :)

---

### Post by madinc on 2012-09-26
i do think the problem is in gtk-widgets.css or in nautilus.css but i don't know wich section

---

### Post by vasa1 on 2012-09-26
This is my gtk.css
```
/* default color scheme */
@define-color bg_color #666;
@define-color fg_color #a2e5fb;
@define-color base_color #777;
@define-color text_color #000000;
@define-color selected_bg_color #2e3436;
@define-color selected_fg_color #a2e5fb;
@define-color tooltip_bg_color #333333;
@define-color tooltip_fg_color #a2e5fb;

/* misc colors used by gtk+ */
@define-color info_fg_color rgb (181, 171, 156);
@define-color info_bg_color rgb (252, 252, 189);
@define-color warning_fg_color rgb (173, 120, 41);
@define-color warning_bg_color rgb (250, 173, 61);
@define-color question_fg_color rgb (97, 122, 214);
@define-color question_bg_color rgb (138, 173, 212);
@define-color error_fg_color rgb (166, 38, 38);
@define-color error_bg_color rgb (237, 54, 54);
@define-color link_color #f07746;
@define-color error_color #cc0000;

/* theme common colors */
@define-color button_bg_color shade (#505050, 1.06);
@define-color button_insensitive_bg_color mix (@button_bg_color, @bg_color, 0.6);
@define-color dark_bg_color #3c3b37;
@define-color dark_fg_color #a2e5fb;
@define-color transparent rgba (0, 0, 0, 0);

@define-color backdrop_selected_bg_color shade (@bg_color, 0.92);
@define-color backdrop_selected_fg_color @fg_color;

@import url("gtk-widgets.css");
@import url("gtk-widgets-backdrop.css");
@import url("apps/gedit.css");
@import url("apps/gnome-panel.css");
@import url("apps/gnome-terminal.css");
@import url("apps/nautilus.css");
@import url("apps/unity.css");
@import url("apps/unity-greeter.css");

```
@define-color bg_color #666; is the only line I changed to get the two images shown below.

---

### Post by madinc on 2012-09-26
> **vasa1 said:**
> @define-color bg_color #666; is the only line I changed to get the two images shown below.

Hey thanks i try that but it didn't work for me what that did change was the colour from some inactive letters but i found a solution for my problem in

/usr/share/themes/Ambiance-Purple/gtk-3.0/gtk-widgets.css

i change this

```
/***********
 * infobar *
 ***********/
.info {
    background-image: -gtk-gradient (linear, left top, left bottom,
                                     from (shade (#dbdbdb, 1.04)),
                                     to (shade (#dbdbdb, 0.96)));

```to this

```
/***********
 * infobar *
 ***********/
.info {
    background-image: -gtk-gradient (linear, left top, left bottom,
                                     from (alpha (#dbdbdb, 0.0001)),
                                     to (alpha (#dbdbdb, 0.0001)));

```and that did the job for me.

---

### Post by vasa1 on 2012-09-26
> **madinc said:**
> ... ... i found a solution for my problem in
...
Great. Your fix is quite specific.
If you want, you can go over to askubuntu.com and answer your own question. It's quite okay to do so and they don't discourage it at all.
Don't forget to include an image of the modified version so people will know just what has been fixed.

---

### Post by madinc on 2012-09-27
before

[ATTACH]224737[/ATTACH]

after

[ATTACH]224738[/ATTACH]

---

