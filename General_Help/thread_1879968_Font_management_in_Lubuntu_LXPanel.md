---
title: "Font management in Lubuntu LXPanel"
date: 2011-11-12
forum: General Help
---

### Post by Dennis N on 2011-11-12
I am looking for the way to change the font used in the LXPanel's Task Bar (Window List) to boldface for better readability. This seems possible for the clock only. 

The font used for the lxpanel also seem independent of the font chosen in the "Customize Look and Feel" utility (default font).

I am using Lubuntu 11.04.

---

### Post by amjjawad on 2011-11-12
> **Dennis N said:**
> I am looking for the way to change the font used in the LXPanel's Task Bar (Window List) to boldface for better readability. This seems possible for the clock only. 

The font used for the lxpanel also seem independent of the font chosen in the "Customize Look and Feel" utility (default font).

I am using Lubuntu 11.04.

Hi,

Sadly I got rid of all my systems and installed Lubuntu 11.10 as the one and only OS on here. I need to check my other PC where many systems are installed including Lubuntu 11.04.

In the mean time, are we talking about one type of font that you can't seem to set it as the font for LXPanel?

---

### Post by Dennis N on 2011-11-12
> **amjjawad said:**
> Hi,

In the mean time, are we talking about one type of font that you can't seem to set it as the font for LXPanel?


1. I see no place to set the font used in the lxpanel's task list (window list) from the existing one to any other font, or to set the existing font to boldface. These are the problems I want to solve. [see Edit below]  

2. The "Customized Look and Feel" tool allows you to change the "default font" in the widget tab, but that only affects window content such as the file manager and other program windows. There is no effect on the panel font. [see Edit below]

Thanks.

EDIT: Partially solved: I am now able to get the font face to change, even in the lxpanel, but the font size in the panel will not change as it does elsewhere, and it seems it still can't be made boldface in the panel (except for the clock) even if it is in the other menus.

So, the question now is can the font within the lxpanel task list (window list) be set to boldface? And if so, how to set this?

---

### Post by Rodney9 on 2011-11-12
It doesn't seem something you can do *yet*.

It has been added to a wish list -

[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/690662](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/690662)

Others have been trying, curiously they want the font smaller - 

[http://forum.lxde.org/viewtopic.php?f=21&t=1423](http://forum.lxde.org/viewtopic.php?f=21&t=1423)


Rodney

---

### Post by Dennis N on 2011-11-12
> **Rodney9 said:**
> It doesn't seem something you can do *yet*.

It has been added to a wish list -

[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/690662](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/690662)

Others have been trying, curiously they want the font smaller - 

[http://forum.lxde.org/viewtopic.php?f=21&t=1423](http://forum.lxde.org/viewtopic.php?f=21&t=1423)


Rodney

Thanks for the info. 

The default panel font size is o.k. on my laptop, but too small (for me) on a large desktop monitor that I use. Hope it will become possible in Lubuntu 12.04.

---

### Post by Rodney9 on 2011-11-12
There is a one way to make them bigger , you increase the panel size and icon size, this is ok on large monitors.

You have to set the panel Appearance to a solid colour to make look any good.

See my example image below.


Rodney

---

### Post by Dennis N on 2011-11-12
> **Rodney9 said:**
> There is a one way to make them bigger , you increase the panel size and icon size, this is ok on large monitors.

You have to set the panel Appearance to a solid colour to make look any good.

See my example image below.


Rodney

Yes, I had previously noticed this, but I didn't like the wider panel I had to use. I think having a bold font option (like in the clock) would help a lot.

---

### Post by dajare on 2011-11-13
> **Dennis N said:**
> I am looking for the way to change the font used in the LXPanel's Task Bar (Window List) to boldface for better readability. This seems possible for the clock only.

I noticed the possibility of "bolding" the font for the clock ... but can you change the point size? On some screencast or somewhere, I saw the "clock" on two lines (and the instructions on the Lubuntu FAQ help with this part), but then the text is too tall for my bar. Is there also a way of making the font *smaller*? (I see this is addressed in the thread above, but (mildly worringly) lxde.org seems to be down.)

Thanks!

---

### Post by Dennis N on 2011-11-13
> **dajare said:**
> I noticed the possibility of "bolding" the font for the clock ... but can you change the point size? On some screencast or somewhere, I saw the "clock" on two lines (and the instructions on the Lubuntu FAQ help with this part), but then the text is too tall for my bar. Is there also a way of making the font *smaller*? (I see this is addressed in the thread above, but (mildly worringly) lxde.org seems to be down.)

Thanks!

The clock always has the same font size as other text in the panel (like the task or window list). It can't be set independently, except for the bold font check box.

On the clock, enter \n for a line break within the clock format code and you should get two lines for the clock. 

As of now, it appears the only way the font size in the lxpanel can be increased is to increase the icon size (and panel width to fit the bigger icons) in the panel settings (right click on the panel), as mentioned in posts above. Also, it appears there is no way to make the window list text boldface.

These issues perhaps will be addressed in a future release.

---

### Post by amjjawad on 2011-11-14
Task or Window List? sorry but what do you mean by that?

---

### Post by Dennis N on 2011-11-15
> **amjjawad said:**
> Task or Window List? sorry but what do you mean by that?

**Window List** = That part of the LX Panel which displays the open windows for your applications.

[Right click at an open place on the LX Panel: First entry on the menu is "**Task Bar (Window List) Settings**" - this little settings dialog box might be a good place to offer a bold face font option for the text on the buttons.]

---

### Post by amjjawad on 2011-11-15
> **Dennis N said:**
> **Window List** = That part of the LX Panel which displays the open windows for your applications.

[Right click at an open place on the LX Panel: First entry on the menu is "**Task Bar (Window List) Settings**" - this little settings dialog box might be a good place to offer a bold face font option for the text on the buttons.]

You mean this:

[IMG]http://i42.tinypic.com/vsmiva.jpg[/IMG]


[IMG]http://i42.tinypic.com/bf553s.jpg[/IMG]


It might be the fever that made me thing it's a pure Windows Thing and I totally forgot that name does actually exist in Lubuntu, my bad :)

---

