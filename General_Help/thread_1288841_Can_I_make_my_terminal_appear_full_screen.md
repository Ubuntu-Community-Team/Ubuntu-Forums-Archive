---
title: "Can I make my terminal appear full screen?"
date: 2009-10-11
forum: General Help
---

### Post by letmekilluplz on 2009-10-11
I want to be able to see my background when it appears. Any ideas?

---

### Post by jeremyswalker on 2009-10-11
Pressing F11 should make it full screen. If you want to see your desktop background, just change the background to transparent in Edit > Profile Preferences.

---

### Post by letmekilluplz on 2009-10-11
> **jeremyswalker said:**
> Pressing F11 should make it full screen. If you want to see your desktop background, just change the background to transparent in Edit > Profile Preferences.

I dont mean without the menu bars I just mean a maximized window like when you click the big square in the corner. I just don't want to have to click it everything I open my terminal. 

And I want the terminal background not desktop

---

### Post by peetbull on 2009-10-11
Hello,

I assume you refer to Gnome Desktop and its default terminal application, [FONT=Courier New]gnome-terminal[/FONT].

_1) Open the terminal_
Applications > Accessories > Terminal

_2) Open its preferences_
(in terminal window)
Edit > Profiles > Edit (button) > Background (tab)

_3) Activate transparent background_
Click on "Transparent Background" radio button and set the slide bar at the level of transparency you wish.

 I would also add that having "normal" or "extra" desktop effects, enhances [FONT=Courier New]gnome-terminal[/FONT]'s transparency, showing already open windows etc. If you want to check your configuration:
System > Preferences > Appearance > Visual Effects (tab) > Normal or Extra (radio button)

Let us know if it worked, or even if I understood your issue correctly!

[COLOR=Teal][added][/COLOR] 

About window state. I think it's default behaviour is that if you close it maximized, when you run terminal again it will be maximized.

And an idea. If you wanna go hardcore terminal try Ctrl+Alt+F1 to switch to a terminal state. While in terminal state, press Alt+F7 to return to your desktop.


Enjoy your terminal!

---

### Post by drs305 on 2009-10-11
I don't see an entry for "open maximized" in the gnome-terminal profiles or gconf-editor, but you can make a shortcut and designate the size of the window like this:
```

gnome-terminal --geometry=150x45+30+50 

```
Width, lines, from left, from top.

---

### Post by wojox on 2009-10-11
There's also the old Alt+Spacebar+X

While your at it make a keyboard shortcut with windows key.

---

### Post by fooman on 2009-10-11
> **drs305 said:**
> I don't see an entry for "open maximized" in the gnome-terminal profiles or gconf-editor, but you can make a shortcut and designate the size of the window like this:
```

gnome-terminal --geometry=150x45+30+50 

```Width, lines, from left, from top.

to take that one step further....

right-click on applications in the top panel > edit menus

when the main menu comes up, click once on "accessories" in the left column,  then right-click on "terminal" in the right side and choose properties from the menu.

in the command space....replace "gnome-terminal" with drs305's suggestion of "gnome-terminal --geometry=150x45+30+50" or use your own parameters to fill the screen, depending on your screen size....i use "170x50+0+0" on my 22" 1680x1050 monitor and it just leaves the panels visible.

close that window and the main menu window.  now when you click terminal from the menu and it should open maximized.

---

### Post by letmekilluplz on 2009-10-11
Used Drs's idea Thanks

---

