---
title: "Nautilus background color 11.10"
date: 2011-10-11
forum: General Help
---

### Post by rmcellig on 2011-10-11
How do I change the background color of a Nautilus window in 11.10. I don't see the open anymore under the Nautilus Edit menu.

---

### Post by madjr on 2011-10-11
would like to know too.

but as far as i can see i dont think that option was reimplemented yet

---

### Post by fragos on 2011-10-12
This may unfortunately be deliberate and IMHO misguided simplification. Check out what's missing from Appearances like colors and icon choices.

---

### Post by madjr on 2011-10-13
yea plenty of stuff is missing still.

am sure many users will be annoyed tomorrow/this week when they find out

---

### Post by rmcellig on 2011-10-13
Might it just be a case of turning on a gconf setting? Can this funtionality be implemented from the command line? Just a thought.

---

### Post by sclewin on 2011-10-13
I am also interested in this as I find all the white in nautilus difficult to look at and hard to see files.

---

### Post by philinux on 2011-10-13
> **sclewin said:**
> I am also interested in this as I find all the white in nautilus difficult to look at and hard to see files.

Ditto here. I'm not at my box but would really like to sort this one.

---

### Post by mc4man on 2011-10-13
What you need is someone who knows themes & how to adjust, whether to do globally or locally, I know almost nothing..
Or wait for some theme editor to show up...

Myself just don't like the orange - that's simple to adjust if you know the #XXXXXX you want to use (I keep forgetting to write down the one I like so currently am trying some colors out.
(adjusting here in /usr/share/themes/Ambiance/ in the gtk-3.0 & gtk-2.0 - (selected_bg_color)

To get an #XXXXXX the color wheel was handy - currently it can be still found in a few spots - ccsm > cube > appearance has one (cube doesn't need to be enabled to use

So while doing the orange  went ahead & changed the window base color - don't particularly like what I choose, more to see what happened

---

### Post by rmcellig on 2011-10-13
How did you change the window base color? This is what I am trying to do so that all of my Nautilus windows have the same background color or texture like I had in previous versions of Ubuntu.

---

### Post by fragos on 2011-10-13
The dconf-editor may the the way to go for now. Using org - gnome - desktop - interface I was able to select the Faenza font that I much prefer.

---

### Post by crdlb on 2011-10-13
> **mc4man said:**
> 
To get an #XXXXXX the color wheel was handy - currently it can be still found in a few spots - ccsm > cube > appearance has one (cube doesn't need to be enabled to use

You could also use gcolor2 (in universe) or ```
zenity --color-selection
```

---

### Post by rmcellig on 2011-10-13
Can I use the gconf or dconf editor to change the background color of Nautilus windows? I would like to change the color from white to something else and also have the ability to use textures if need be like in previous versions of Ubuntu.

---

### Post by mc4man on 2011-10-13
> **rmcellig said:**
> How did you change the window base color? This is what I am trying to do so that all of my Nautilus windows have the same background color or texture like I had in previous versions of Ubuntu.
As I said i'm pretty much the wrong person to advise on this.

In any event to change the window body color I simply edited the 2 files in /usr/share/themes/Ambiance/gtk-3.0, (gtk.css; settings.ini) though likely only 1st. one had to be.
Ex. -  blue for window base, red for the selected in gnome, also did red in the gtk-2.0/gtkrc
> /* default color scheme */
@define-color bg_color #f2f1f0;
@define-color fg_color #4c4c4c;
[COLOR="Blue"]@define-color base_color #D6D1B6;[/COLOR]
@define-color text_color #3C3C3C;
[COLOR="Red"]@define-color selected_bg_color #DCB575;[/COLOR]
@define-color selected_fg_color #ffffff;
@define-color tooltip_bg_color #000000;
@define-color tooltip_fg_color #ffffff;
ect. ect.


I'm sure there are other/better ways to do this stuff, my interest level is low enough to just take the 1st. way that works in a T&E

---

### Post by rmcellig on 2011-10-13
Wow!

I hope there is a way easier way to do such a simple thing like change the color of a Nautilus Window. Thanks Mc4Man.

---

