---
title: "Change scrollbar color - Xubuntu 11.10"
date: 2012-01-08
forum: General Help
---

### Post by tomkat3 on 2012-01-08
I've been using Xubuntu 11.10 with the axiomd theme (I like darker themes), and the result so far would be perfect if I could see the scroll bar.

There isn't an obvious way to change just the color of the scrollbar. Something little like this is probably one line in a text file somewhere, right? Where is the file that specifies the scrollbar color?

This is about as minor a complaint as it gets... :frown:

---

### Post by vasa1 on 2012-01-08
> **tomkat3 said:**
> I've been using Xubuntu 11.10 with the axiomd theme (I like darker themes), and the result so far would be perfect if I could see the scroll bar.

There isn't an obvious way to change just the color of the scrollbar. Something little like this is probably one line in a text file somewhere, right? Where is the file that specifies the scrollbar color?

This is about as minor a complaint as it gets... :frown:

See if [this]("http://www.wilderssecurity.com/showpost.php?p=2000094&postcount=26") helps.

---

### Post by tomkat3 on 2012-01-08
Yep, that's exactly what I had in mind. I Changed a line from 

   ```
 colorize_scrollbar = FALSE

```to

   ```
 colorize_scrollbar = TRUE
```I was able to solve the problem in Xubuntu 11.04 using the settings manager GUI, but it seems they removed some options in 11.10.

Thanks!

---

### Post by gregzeng on 2013-02-02
> **vasa1 said:**
> See if [this]("http://www.wilderssecurity.com/showpost.php?p=2000094&postcount=26") helps.

Above url refers to "Secret Command-Line" business here:

OPENQUOTE:

Open ~/.themes/theme name/gtk-2.0/gtkrc in a text editor and near the top of the file, you'll find a line that reads something like:

 gtk_color_scheme="fg_color:#a0a0a0\nbg_color:#161616\nbase_color:#454545\ntext_color:#50d000\nselected_bg_color:#282828\nselected_fg_color:#ffffff\ntooltip_bg_color:#303031\ntooltip_fg_color:#ffffff"

 I suppose you can play around with different colours - see what is used in gtkrc for scrollbar usually under } Style " xxx-scrollbar" {
 eg. NORMAL may be bg_color etc.

 (Themes may also be in /usr/share/themes)

 Bit fiddly I think. Personally I would rather be looking for a more suitable 
 t

ENDQUOTE

Put into English, and I get confused.

So: 

1) Find out which theme is being used (Settings/Appearance/Style: in my case, any of 49 possible themes in the folder /usr/share/themes)

2) Double-click on the one file visible in your file manager: "gtkrc"

Then try to follow the above.

I gave up. Now I'll need to search on another forum, because I do have XFCE, but not Xubuntu.  I mistook Mint XFCE  for Xubuntu.  The above is almost meaningless for Mint IMO.

---

