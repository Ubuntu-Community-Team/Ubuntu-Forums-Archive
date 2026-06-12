---
title: "How to customize GTK+ theme's background color under ubuntu 11.10"
date: 2012-03-28
forum: General Help
---

### Post by mjsilverstri on 2012-03-28
How can I customize the tool tip background color of the GTK+ theme under ubuntu 11.10? 

Like the way describe below but for 10.04.
[http://www.tipstank.com/2010/05/23/solve-eclipse-black-pop-up-code-assist-box-in-ubuntu-10-4-lucid/](http://www.tipstank.com/2010/05/23/solve-eclipse-black-pop-up-code-assist-box-in-ubuntu-10-4-lucid/)

Thank you.

---

### Post by fragos on 2012-03-28
Here's what I've written on changing theme colors. The tool tip background color is easily identifiable with the variable name in theses configuration files.

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

