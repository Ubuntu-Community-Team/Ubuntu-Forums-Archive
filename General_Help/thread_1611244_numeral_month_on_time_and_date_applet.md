---
title: "numeral month on time and date applet"
date: 2010-11-01
forum: General Help
---

### Post by Dex73 on 2010-11-01
Is there any time and date applets that display the date in all numerals instead of writing out the abbreviated lettered form of the month, or perhaps an upgrade?

---

### Post by Dex73 on 2010-11-03
Are there any solutions at all? For some reason it really bugs me that it takes up that much space when it doesn't have to. Am I the only one that feels this way? Anyways, I would really like to get rid of the 3 alphabetic characters and the large space after that and replace it with the number of the month and some kind of comma or slash. I think it would really free up some space on the panel. However I can't find any thing that has helped yet. Any ideas would be greatly appreciated.

---

### Post by stinkeye on 2010-11-03
> **Dex73 said:**
> Is there any time and date applets that display the date in all numerals instead of writing out the abbreviated lettered form of the month, or perhaps an upgrade?

You can change the format of the clock applet in gconf-editor.
/apps/panel/applets/clock_screen0/prefs
I only have the one top panel.Your location may be different. Just search for **custom_format** in gconf.
When searching, tick the "Search also in key names" box.

Change the format key to **custom** .
Then insert your own format in the custom_format key.

Date and time formats....[**_[COLOR="DarkRed"]http://manpages.ubuntu.com/manpages/hardy/en/man3/strftime.3.html[/COLOR]_**]("http://manpages.ubuntu.com/manpages/hardy/en/man3/strftime.3.html")

eg. this code shows as in pic.
```
%a %e/%m/%y  %l:%M %P
```

There is another way of formatting here....[**_[COLOR="DarkRed"]http://www.omgubuntu.co.uk/2009/09/customize-the-gnome-panel-clock-to-match-karmics-new-icons/[/COLOR]_**]("http://www.omgubuntu.co.uk/2009/09/customize-the-gnome-panel-clock-to-match-karmics-new-icons/")

---

### Post by Dex73 on 2010-11-04
Thanks for the help stinkeye, but I don't know enough to follow your first suggestion and the second one seems to focuses on changing the font. I'm looking to change the letters representing the month into numbers.

e.g. ( I want Nov. to become 11 )

I'm sorry if I'm just not getting it. Is there a more simplified way of explaining it?

---

### Post by stinkeye on 2010-11-04
> **Dex73 said:**
> Thanks for the help stinkeye, but I don't know enough to follow your first suggestion and the second one seems to focuses on changing the font. I'm looking to change the letters representing the month into numbers.

e.g. ( I want Nov. to become 11 )

I'm sorry if I'm just not getting it. Is there a more simplified way of explaining it?

Post exactly how you want it to look.

---

### Post by stinkeye on 2010-11-04
Alt + F2 and run
```
gconf-editor
```

Drill down to /apps/panel/applets/clock_screen0/prefs

In the right hand column double click on **format** and change the value to **custom**.

Now double click on **custom_format** and change the value to
```
%a %e/%m/%y  %l:%M %P
```

Just delete the parts you don't want.
The link I gave previously for time formats shows you what **%a** etc will display. 
eg %m shows the month as a decimal number.

Play around with it. Rearrange how you like. You can't mess anything up.

You can go back to how it was by double clicking on **format** 
and changing the value back to **12-hour**

---

### Post by Dex73 on 2010-11-04
Got it! the look i was going for ended up being 

%e/%m/%y-%H:%M

It produces dd/mm/yy-hh:mm. So date and then time in 24-hour format but with out the day of the weak, which to me isn't that important.

---

