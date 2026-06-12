---
title: "How to use Emerald?"
date: 2011-04-08
forum: General Help
---

### Post by neu5eeCh on 2011-04-08
I've latched onto an emerald theme that minimizes the window border.

[http://compiz-themes.org/content/show.php/Minimal+LittleGlass?content=139829](http://compiz-themes.org/content/show.php/Minimal+LittleGlass?content=139829)

However, I miss not having a button to keep the window "always on top", as I did with the following theme:

[http://compiz-themes.org/content/show.php/Do+More,+simple+clean+round+theme.?content=70823](http://compiz-themes.org/content/show.php/Do+More,+simple+clean+round+theme.?content=70823)

My question is this: I notice in the edit theme tab, under button pixmaps, that there are buttons for other functions like "always on top". And I notice that most themes include these buttons. Is there a way to activate these buttons?

If not, is there a keystroke combination for keeping a window on top?

---

### Post by Rasa1111 on 2011-04-08
you can just right click the title bar/top of the window and select "always on top" from the menu that pops up. 

I used to use the "menu" button on the title bar to do it,
until I found a right click does the same thing. 

Sorry if that's not sufficient,
I havent messed much with the emerald button settings.

Right click does the job though.,

---

### Post by neu5eeCh on 2011-04-08
Thanks Rasa, I was aware of the right click method. The problem, to me, is that this requires a number of steps. Right click, scroll, click again.

The nice thing about having a button on the titlebar is that it's one quick click. I frequently use the "always on top" option.

I'm thinking there must be some key and mouse combination in Emerald that reveals these other buttons? I don't get why they're listed under button pixmap options if they're not available for use?

---

### Post by Rasa1111 on 2011-04-08
Ohh gotcha!

My apologies. 

Yeah it is a few steps. 
and I guess I've never had a theme with an "always on top button"! 

I too, often use the 'always on top' feature, 
But apparently was not aware that some themes had a specific "button" for it! lol
Sorry mate, If I find something i'll return.

ok, i crawl back into my hole now... lol :P

---

### Post by Copper Bezel on 2011-04-08
Yeah, Emerald themes store their button layouts in their theme files. Open your home folder and hit Ctrl+H to show hidden files, then select .emerald, then themes. Pick the theme you want to edit, then select theme.ini and open it in gedit.

The last line before the description will look something like

title_object_layout=M(3)S(20):T:HN(3)X(3)C

You can edit this line to include the Always On Top button, in this case in the upper right corner (but you can put the Y whereever you like.)

title_object_layout=M(3)S(20):T:HN(3)X(3)C(3)Y

Change to another theme and switch back for the change to take effect.

---

### Post by neu5eeCh on 2011-04-08
Wow. Thanks Copper, that's exactly the info I was looking for. I wonder why Emerald doesn't make that a bit more straightforward?

And Rasa, thanks again, I still appreciate that you tried.

**Edit: **Turns out the symbol I wanted wasn't Y, but A. But where did you first stumble on this info?

---

### Post by Copper Bezel on 2011-04-08
It's similar to how Metacity handles button layouts (just with more features.) When I recently switched to Emerald, I just had to get rid of that redundant Maximize button on mine, so I just searched the theme index for "layout". = ) Poke around, and you'll find things.

I wasn't certain about the Y, either. I couldn't tell if that was the "Stay Above" item or something else.

---

### Post by Krytarik on 2011-04-09
How about a GUI way?:
- "System -> Preferences -> Emerald Theme Manager"
- to edit the currently set theme, just click at "Edit Themes", then at "Titlebar"
- on the right side you'll find the option "Title-bar Object Layout" and below of it a legend to it

Isn't that intuitive enough!? ;-)

Greetings.

---

### Post by neu5eeCh on 2011-04-09
> **Krytarik said:**
> How about a GUI way?:
- "System -> Preferences -> Emerald Theme Manager"
- to edit the currently set theme, just click at "Edit Themes", then at "Titlebar"
- on the right side you'll find the option "Title-bar Object Layout" and below of it a legend to it

Isn't that intuitive enough!? ;-)

Greetings.

Thanks Krytarik. The fellow who made the theme pointed this out to me last night (after the help I received here). I saw that "Title-bar Object Layout" but, no, it's not intuitive at all. I saw it and didn't know what I was looking at. Who the heck thought up "Title-bar Object Layout"?!? :roll:  Did some geek stick their pencil in their ear?

What herbaceous object layout would you like on your homogenized bovine? Sir? :-s

---

### Post by Copper Bezel on 2011-04-09
Well, it's definitely better than editing a text file that doesn't come with a cheat sheet. = ) (Which is, of course, the *only* way to edit Metacity themes.)

Edit: "Titlebar" and "Layout" are standard terms. "Object" is used because you technically have objects that aren't buttons in there, too. It actually does make sense. = )

---

### Post by neu5eeCh on 2011-04-09
Anyway, here it is, for those with inquiring minds.

[IMG]http://poemshape.files.wordpress.com/2011/04/minimal-titlebar1.jpg[/IMG]

I think, now, I have finally squeezed blood from a turnip. I've just about maximized the usage of vertical space on my little laptop.

---

### Post by Copper Bezel on 2011-04-09
Looks good! = )

---

