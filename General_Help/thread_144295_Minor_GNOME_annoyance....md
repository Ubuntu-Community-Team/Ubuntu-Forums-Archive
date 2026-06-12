---
title: "Minor GNOME annoyance..."
date: 2006-03-14
forum: General Help
---

### Post by ziplux on 2006-03-14
In Windows, if I have a window maximized, I can go to the upper-right-hand corner of the screen and click, and the window closes.  In GNOME, it seems like there is a 2 or 3 pixel border that prevents me from doing this.  Is there anything I can change in the theme, or something, to fix this?

Thanks!

---

### Post by dcstar on 2006-03-14
[QUOTE=ziplux]In Windows, if I have a window maximized, I can go to the upper-right-hand corner of the screen and click, and the window closes.  In GNOME, it seems like there is a 2 or 3 pixel border that prevents me from doing this.  Is there anything I can change in the theme, or something, to fix this?

Thanks![/QUOTE]
It probably depends entirely on what theme you are using, mine does what you say yours won't do.

Try another theme.

---

### Post by ziplux on 2006-03-14
> It probably depends entirely on what theme you are using, mine does what you say yours won't do.

Try another theme.

I tried all the themes in my stock Ubuntu install.  What theme are you using?

---

### Post by predaeus on 2006-03-14
The window borders and titlebar (including the buttons to close window, etc.) are drawn with Metacity themes, as far as I know. If you are familiar with the directory structure in your /home directory and with editing configuration files, you could try to tweak it to your wishes.

Here is a nice tutorial you can use to alter existing themes:
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

!!! But beware if you don't know what you are doing, you could severely mess up your desktop !!!

---

### Post by ziplux on 2006-03-15
If anyone is having the same problem, I solved it by editing [FONT="monospace"]/usr/share/themes/Human/metacity-1/metacity-theme-1.xml[/FONT]

Here's a diff against the stock version of the file:
```

29,32c29,30
<   <distance name="left_titlebar_edge" value="0"/>
<   <distance name="right_titlebar_edge" value="0"/>
<   <border name="title_border" left="0" right="0" top="0" bottom="0"/>
<   <border name="button_border" left="1" right="0" top="0" bottom="3"/>
---
>   <distance name="left_titlebar_edge" value="1"/>
>   <distance name="right_titlebar_edge" value="1"/>

```

---

### Post by dcstar on 2006-03-15
[QUOTE=ziplux]I tried all the themes in my stock Ubuntu install.  What theme are you using?[/QUOTE]
SphereCrystal

---

