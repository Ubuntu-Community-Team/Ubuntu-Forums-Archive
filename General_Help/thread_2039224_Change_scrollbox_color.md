---
title: "Change scrollbox color"
date: 2012-08-08
forum: General Help
---

### Post by lumaja on 2012-08-08
Scroll box in Ubuntu 12.04 difficult to see not enough contrast, want change to light blue or orange or just a color with more contrast.
Thank you

---

### Post by vasa1 on 2012-08-08
Please be more specific. Attach a small image that illustrates your problem. Use the paper clip icon to upload the image from your computer.
Also, make it clear whether you are referring to conventional scrollbars or the overlay scrollbars and do mention which desktop environment you're running, and the programs which give you trouble.

---

### Post by lumaja on 2012-08-23
Sorry for the late reply.
Its the side scrollbar in Libre and Firefox send attachment.
New question, how can I change to bigger font the Modify Layer on the bottom screen with sheet numbers.
Screenshot wrong don't know how to delete the wrong one, the correct one is from Libre Calc.
Thank you

---

### Post by vasa1 on 2012-08-23
Which theme are you using?

Search for a line like
		colorize_scrollbar  = FALSE
in the theme's gtk-2.0/gtkrc and change FALSE to TRUE.

---

### Post by lumaja on 2012-08-24
gtk Theme:Radiance.


What is the command for colorize_scrollbar?
Thank you for the help

---

### Post by vasa1 on 2012-08-24
> **lumaja said:**
> gtk Theme:Radiance.


What is the command for colorize_scrollbar?
Thank you for the help

From the Ubuntu Software Center, install Gnome Color Chooser. It has options for coloring scrollbars under the tab labelled "specific".

I think that will be easier than the command line way.

---

### Post by lumaja on 2012-08-28
Sorry for the late response and thank you for the int but you could send the the full command  to gain lodge on Terminal.

Another Question: in Libreoffice Calc there is a scrollbar with sheet numbers and the text is very small, is there away to enlarge I can't find it anywhere.
Thank you

---

### Post by vasa1 on 2012-08-28
> **lumaja said:**
> Sorry for the late response and thank you for the int but you could send the the full command  to gain lodge on Terminal.

Could you please clarify what you want? It's not clear to me.
> **lumaja said:**
> 
Another Question: in Libreoffice Calc there is a scrollbar with sheet numbers and the text is very small, is there away to enlarge I can't find it anywhere.
Thank you
No, I don't know how to increase the font size. I agree that it's a bit small. I usually rename the tabs to what I want and use CAPS if needed.

---

### Post by MARP1961 on 2012-08-28
I simply installed 'Gnome Colour Chooser' from the Ubuntu Software Centre and changed the background to blue and scroll button to black.

---

### Post by rcosby on 2012-09-06
I have noticed that this is a result of the theme that you have chosen.  I like to use the elementary theme and this extremely small font on the tabs is a by product of that theme.  I have never discovered how to correct it.  Changing the theme will change the tab size back to a more readable one.

---

### Post by vasa1 on 2012-09-06
> **rcosby said:**
> I have noticed that this is a result of the theme that you have chosen.  I like to use the elementary theme and this extremely small font on the tabs is a by product of that theme.  I have never discovered how to correct it.  Changing the theme will change the tab size back to a more readable one.
Thanks for that tip! Perhaps, it may now be worthwhile looking for what is responsible. (In things like Chrome/Chromium, a search is futile because the tiny size is hard-coded by Google's youngsters.)

---

### Post by vasa1 on 2012-09-06
I had a look at the font size in LibreOffice Calc's tabs. As mentioned, Elementary's was really, really small. I wonder what Satya was thinking. Or maybe it's just the *age thing*. There are other themes with small fonts but the Elementary one tops! Greybird is decent but let's see if it can be made a little bigger.

---

### Post by vasa1 on 2012-09-07
This really is a digression but OP started it ;)
One way to increase the font size in LibreOffice Calc **while retaining the same theme**, is to edit the .gtkrc file as suggested [here]("http://askubuntu.com/a/152998/25656").

In this file, search for:
```
GtkScrollbar		::slider-width				= 6
```
and increase the value from the default, whatever that maybe.
The downside is that the horizontal and vertical scrollbars increase in height and width, respectively, **for all gtk2 apps**.
Also, after a point, while the tab height can be increased, the font size doesn't increase.

---

