---
title: "opera forward back mouse buttons"
date: 2009-07-13
forum: General Help
---

### Post by SlugSlug on 2009-07-13
Hi all,

I use imwheel to allow me to use the mouse back / forward buttons in firefox and nautilis.

In Opera the forward back button scroll up and down, does anyone know how to fix this? I've tried /usr/share/opera/ini/ mouse but made no diffrence...

also tried options shortcuts> mouse forward / back but it ignores the enrty...

a squiggly red line for spelling mistakes would be nice too - like firefox...   ;-)

cheers,

---

### Post by sisco311 on 2009-07-14
> **SlugSlug said:**
> Hi all,

I use imwheel to allow me to use the mouse back / forward buttons in firefox and nautilis.

In Opera the forward back button scroll up and down, does anyone know how to fix this? I've tried /usr/share/opera/ini/ mouse but made no diffrence...

also tried options shortcuts> mouse forward / back but it ignores the enrty...

a squiggly red line for spelling mistakes would be nice too - like firefox...   ;-)

cheers,
Go to *Tools -> Preferences -> Advanced tab -> Shortcuts -> Mouse Setup -> Edit -> Applications* and add a new Shortcut. (i.e. Button8 Back, Button9 Forward)

If you don't know the number of the mouse button, then open a terminal and type:
```
xev | grep button
```
and press the mouse button while the mouse pointer is on xev the window.

EDIT: for inline spell-checking you have to install opera 10 (now is beta).

i have had no issues using the alpha version as my primary (and only) browser and now the beta is rock solid on my system.

---

### Post by SlugSlug on 2009-07-14
> **sisco311 said:**
> Go to *Tools -> Preferences -> Advanced tab -> Shortcuts -> Mouse Setup -> Edit -> Applications* and add a new Shortcut. (i.e. Button8 Back, Button9 Forward)

If you don't know the number of the mouse button, then open a terminal and type:
```
xev | grep button
```
and press the mouse button while the mouse pointer is on xev the window.
.

I have it set to button8 and button9 - but it still scrolls up and down

the side buttons don't show with the |grep but without it I get

KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  4294967172 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


all the other buttons show (left middle right scroll, and scroll left/right) none are refered to as 8 or 9

---

### Post by SlugSlug on 2009-07-14
> **sisco311 said:**
> 

i have had no issues using the alpha version as my primary (and only) browser and now the beta is rock solid on my system.


I installed the beta version10 can you point me towards the inline spell checker its not on by default and I carnt seem to find it..

---

### Post by SlugSlug on 2009-07-14
can anyone help with the spelling ? google is quite limited it all seems like old posts and that version 10 will solve it all. I've only been on Opera since the weekend it is already my default just 2 snags now spelling (which I only have my self to blame) and them back forward mouse buttons...   there is also no stumble - but I dnt think thats a bad thing I found this site as a really good adblockplus subsitute 
[http://www.fanboy.co.nz/adblock/opera/](http://www.fanboy.co.nz/adblock/opera/)

I've also noticed 'malfuctions' in the V10 beta like menus dnt allow point hover expand > new menu - - that may just be my setup tho....

---

### Post by SlugSlug on 2009-07-16
bump

---

### Post by Arup on 2009-07-16
Inline spell check is on by default on Opera 10, you will see underlines on mispelt words. Use the qt4 build instead of qt3 as it works far better.

---

### Post by SlugSlug on 2009-07-16
> **Arup said:**
> Inline spell check is on by default on Opera 10, you will see underlines on mispelt words. Use the qt4 build instead of qt3 as it works far better.

it never worked for me - check spelling was greyed out

---

### Post by SlugSlug on 2009-07-16
really loved this speed of this browser - but its back to firefox for me

---

### Post by twizler on 2009-10-28
THIS WORKS = Linux fix opera 10 mouse -
 I have a Micro Soft Mouse 5 button IntelliMouse optical .  This will fix your Linux  Opera 10 mouse forward and back button 
I was MAD, NEW browser NO FREAKING BACK AND FORWARD MOUSE IN OPERA 10 I THINK NOT... 

HERE IS THE FIX 

_____________ Linux Opera 10 mouse forward back button ___________________
1:  sudo su 

2: cd /usr/share/opera/ui

3: edit the file in standard_mouse.ini
4. change button names from Button5 Button6 TO --> Button8 Button9 

Button8                                                 = Back
Button9                                                 = Forward

> Open the /usr/share/opera/ui/standard_mouse.ini file in your fav text editor. 

Change the orig file that says button5 and buttonSix to Button8 for back and Button9 for forward. 

LOOK AT RED TYPE FONT SHOULD LOOK LIKE THIS 

> [QUOTE][QUOTE][QUOTE]
______________________________________________________
Opera Preferences version 2.0
; Mouse input specification file for Opera 7.0
; This file is stored in UTF-8 encoding

[Version]
File Version=1

[Info]
Name=Opera Standard
Description=Opera Standard mouse setup
Author=Opera Software ASA
Version=1

[Application]
GestureLeft						= Back
GestureLeft shift					= Rewind
GestureLeft, GestureDown				= Rewind
GestureRight						= Forward | Fast forward
GestureRight shift					= Fast forward
GestureRight, GestureUp					= Fast forward
GestureUp						= Stop
GestureUp, GestureDown					= Reload
GestureUp, GestureLeft					= Go to parent directory
GestureUp, GestureRight					= Maximize page, 1 | Restore page, 1
GestureDown, GestureLeft				= Minimize page, 1 | Restore page, 1
GestureDown, GestureRight				= Close page, 1
GestureRight, GestureLeft, GestureRight			= Close page, 1
GestureDown						= Open link in new page | New page
GestureDown, GestureUp					= Open link in background page | Duplicate page

FlipBack						= Back
FlipBack shift						= Rewind
FlipForward						= Forward | Fast forward
FlipForward shift					= Fast forward
[COLOR="Red"]
Button8							= Back
Button9							= Forward[/COLOR]

[Tree Widget]
GestureLeft						= Close all items
GestureRight						= Open all items
FlipBack						= Close all items
FlipForward						= Open all items
[/QUOTE][/QUOTE][/QUOTE]

---

### Post by bendib on 2009-10-28
If you are wondering, it might have something to do with the fact Opera is written in QT, and Nautilus and Firefox are written in GTK. Sorry, I do not know what I can do.

---

