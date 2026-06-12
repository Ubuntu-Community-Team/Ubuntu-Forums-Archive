---
title: "Editing GTK3 themes Ubuntu 11.10 Unity"
date: 2012-03-08
forum: General Help
---

### Post by coldjeanz on 2012-03-08
Basically I haven't been able to find a theme for GTK3 that I like (it's a shame all the good ones are not usable for this environment) and no one seems to be creating new ones either, but I have found a few that if they just had a few adjustments I would like them. The problem is I have no idea how to edit the files, I tried looking in some of those .css files inside the theme folders but when I edit around what I presume to be color codes nothing happens, clearly I have no idea what I'm doing.

Ex:

This is a screenshot of my file manager

[IMG]http://i.imgur.com/ruxMR.png[/IMG]

I want to change the color of the background here from what is currently light grey to something darker but I have no idea where this is done. Also the calendar background color when you click on the clock in the upper right.

A quick direction to go in would be nice but if there's some documentation out there about what section is controlled by what file that would be okay too.

---

### Post by fragos on 2012-03-09
To change theme colors there are three files you need to edit.

/usr/share/themes/{theme name}/gtk-3.0/gtk.css
/usr/share/themes/{theme name}/gtk-3.0/settings.ini
/usr/share/themes/{theme name}/gtk-2.0/gtkrc

In the beginning of these files you'll find 4 pairs of core foreground and background colors used in applications based on the gtk 2 and gtk 3 libraries. Pair base_color and text_color are used for the document or text entry portions of windows where bg_color and fg_color are are used for the windows area where icons and labels are displayed. Selected pair is for selected text and the tooltip pair is used for the tips that pop up when you hover over a button or link. These colors may be applied by applications with varying opacity or shadings. The color of text in buttons comes from the fg_color. These sets of labels appear in all three files so I've been changing all three to be the same for any label I change. Here's an example of what I changed in the gtk.css file in the Ambiance theme.

/* default color scheme */
@define-color bg_color #cdc3b8;
@define-color fg_color #262626;
@define-color base_color #accdff;
@define-color text_color #262626;
@define-color selected_bg_color #01b9fc;
@define-color selected_fg_color #ffffff;
@define-color tooltip_bg_color #A3D0FF;
@define-color tooltip_fg_color #023C79;

---

### Post by coldjeanz on 2012-03-10
it appears none of those codes have any effect on the file manager however. i even tried to make them blatantly obvious by setting the color to the black color code but nothing happens. does it change when you do it? it changes in other areas for me but not file manager.

---

### Post by fragos on 2012-03-10
> **coldjeanz said:**
> it appears none of those codes have any effect on the file manager however. i even tried to make them blatantly obvious by setting the color to the black color code but nothing happens. does it change when you do it? it changes in other areas for me but not file manager.

Some changes may not take effect until a reboot.

---

### Post by coldjeanz on 2012-03-10
You were right about that, logging out and logging back in worked. But I guess I failed to mention I use Marlin as my file manager and that code didn't seem to affect it. I'm 100% sure you can change it in Marlin though because when I use different themes it always changes, but I just don't know where to change it from. Any ideas? One of the themes I use produces a nice background color in the default manager but in Marlin it's white and looks rather ugly.

---

### Post by fragos on 2012-03-10
> **coldjeanz said:**
> You were right about that, logging out and logging back in worked. But I guess I failed to mention I use Marlin as my file manager and that code didn't seem to affect it. I'm 100% sure you can change it in Marlin though because when I use different themes it always changes, but I just don't know where to change it from. Any ideas? One of the themes I use produces a nice background color in the default manager but in Marlin it's white and looks rather ugly.

I'm not familiar with Marlin. My starting point was the Ambiance theme and I stuck with nautilus. Marlin may have an application specific way to change it's background, nautilus used to be like that and gedit still is. The leafpad editor does use the theme colors.

---

### Post by coldjeanz on 2012-03-11
Would you happen to know how to the change the color of this?

[IMG]http://i.imgur.com/lVTu0.png[/IMG]

I'm using a theme but that ugly pink color is used when you select a file or when you click "log out" and the buttons are highlighted with that pink as well.

And I also can't figure out how to change the top panel bar either, where is that controlled from?

---

### Post by Frogs Hair on 2012-03-11
I use marlin and have large number of GTK 3 themes. Some themes don't work right in marlin at all so trying to modify the colors may be a headache.

I discovered that by having both file browsers open that certain areas that are supposed to be colored are not colored at all in marlin . The themes look fine they just render differently in marlin than they do in Nautilus. 

Marlin is on the bottom.

---

### Post by coldjeanz on 2012-03-11
That's the problem mine has, it's all white in marlin so it looks ugly. Some themes skin it correctly though (such as Elementary) but Zutikwo doesn't.

---

### Post by fragos on 2012-03-11
> **coldjeanz said:**
> Would you happen to know how to the change the color of this?

[IMG]http://i.imgur.com/lVTu0.png[/IMG]

I'm using a theme but that ugly pink color is used when you select a file or when you click "log out" and the buttons are highlighted with that pink as well.

And I also can't figure out how to change the top panel bar either, where is that controlled from?

Read #2 in this thread for directions. The specific field you're interested has the label selected_bg_color. Be sure to change all three referenced files.

---

