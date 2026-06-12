---
title: "How can I choose upper-left controls for Clearlooks?"
date: 2010-05-25
forum: General Help
---

### Post by rewyllys on 2010-05-25
In Lucid Lynx, I've chosen the Clearlooks appearance, with customized colors, because of my liking of its overall looks.  This choice of System > Preferences > Appearance comes with the "minimize, maximize, and close" controls in the upper right-corner.

However, I'd like to get used to using these controls in the upper left-corner, because I gather that with Maverick Meerkat, this placement will be standard--and also because I think that this placement will actually prove more convenient for me, once I get used to it.

Hence, my question is:  How can I modify the Clearlooks appearance so as to put these controls in the upper left-corner?

Thanks in advance for any and all help.

---

### Post by philinux on 2010-05-25
in  customise theme choose windo controls and pick say ambiance then save the theme.

---

### Post by sisco311 on 2010-05-25
> **philinux said:**
> in  customise theme choose windo controls and pick say ambiance then save the theme.

That doesn't change the buttons position. 

@OP

Select the Ambiance theme -> Customize... In the *Controls* and *Window Border* tab select *Clearlooks* and in the *Icons* tab *Humanity*.

---

### Post by philinux on 2010-05-26
> **sisco311 said:**
> That doesn't change the buttons position. 

@OP

Select the Ambiance theme -> Customize... In the *Controls* and *Window Border* tab select *Clearlooks* and in the *Icons* tab *Humanity*.

Ah, good catch, I was on my palm pre at the time!

---

### Post by rewyllys on 2010-05-26
> **sisco311 said:**
> That doesn't change the buttons position. 

@OP

Select the Ambiance theme -> Customize... In the *Controls* and *Window Border* tab select *Clearlooks* and in the *Icons* tab *Humanity*.

Thanks, sisco311.  That does the trick!:popcorn:

But how in the world did you ever figure it out!!??

---

### Post by philinux on 2010-05-26
See the sticky in General Help for more info on this.

---

### Post by sisco311 on 2010-05-26
> **rewyllys said:**
> Thanks, sisco311.  That does the trick!:popcorn:

But how in the world did you ever figure it out!!??

You're welcome!

The config file of a custom theme looks like this:

~/.themes/Clearlooks-left/index.theme: 
```
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Clearlooks-left
Comment=Clearlooks-left theme
Encoding=UTF-8

[X-GNOME-Metatheme][color=green]
GtkTheme=Clearlooks
MetacityTheme=Clearlooks
IconTheme=gnome
CursorTheme=DMZ-White[/color][color=red]
ButtonLayout=close,minimize,maximize:[/color]

```

Via the GUI, you can change the GtkTheme (Controls), MetacityTheme (Window Border), IconTheme (Icons) and CursorTheme (Pointer), but currently there is no way to change the location of the buttons.

By default, the buttons are on the left in Ambiance, Radiance and Dust. So, you have to select one of this themes, then change the Gtk, Metacity, Icon and Cursor theme.

---

### Post by rewyllys on 2010-05-26
> **sisco311 said:**
> You're welcome!

The config file of a custom theme looks like this:

~/.themes/Clearlooks-left/index.theme: 
```
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Clearlooks-left
Comment=Clearlooks-left theme
Encoding=UTF-8

[X-GNOME-Metatheme][COLOR=green]
GtkTheme=Clearlooks
MetacityTheme=Clearlooks
IconTheme=gnome
CursorTheme=DMZ-White[/COLOR][COLOR=red]
ButtonLayout=close,minimize,maximize:[/COLOR]

```Via the GUI, you can change the GtkTheme (Controls), MetacityTheme (Window Border), IconTheme (Icons) and CursorTheme (Pointer), but currently there is no way to change the location of the buttons.

By default, the buttons are on the left in Ambiance, Radiance and Dust. So, you have to select one of this themes, then change the Gtk, Metacity, Icon and Cursor theme.

Thanks again, sisco311, for your VERY clear and helpful explanation!  I'm always glad to gain a better understanding of Ubuntu and Linux, and this has been a good lesson for me.:KS

---

### Post by Zol666taN on 2010-08-09
> Thanks again, sisco311, for your VERY clear and helpful explanation!   
> I'm always glad to gain a better understanding of Ubuntu and Linux, 
> and  this has been a good lesson for me.

I will second that .. 100%. I was just going to get mad when I finally found THIS one.

I had the same idea as OP and my settings worked fine .... then also mysteriously reverted to right corner when I was trying something in *change BG*.

All OK now. Thanks.

---

### Post by sisco311 on 2010-08-09
> **Zol666taN said:**
> > Thanks again, sisco311, for your VERY clear and helpful explanation!   
> I'm always glad to gain a better understanding of Ubuntu and Linux, 
> and  this has been a good lesson for me.

I will second that .. 100%. I was just going to get mad when I finally found THIS one.

I had the same idea as OP and my settings worked fine .... then also mysteriously reverted to right corner when I was trying something in *change BG*.

All OK now. Thanks.

My Pleasure.

---

