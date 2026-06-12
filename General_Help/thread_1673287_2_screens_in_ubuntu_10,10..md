---
title: "2 screens in ubuntu 10,10."
date: 2011-01-22
forum: General Help
---

### Post by Guitar-maniac on 2011-01-22
I recently started using two screens, everything is cool expect i can't move anything from screen 1 to screen 2, other than the cursor. I have AWN on screen 1 but i can't start it on screen 2, they are separate screens, not extended. 
Cursor goes to screen 2 without problem when moved to the edge of screen 1, when trying same with (for example) rhythmbox it won't work.
What have i missed? :D

Sorry for bad english, i'm Finnish, hope you understand what i mean.

---

### Post by Minn3h on 2011-01-22
Try:
```
xrandr
```
to identify the "names" of your screens (something like VGA, DVI, LVDS, DP).

Then:
```
xrandr --output <screen1> --left-of <screen2>
```
replacing <screen1> and <screen2> with the names from the first command.

---

### Post by Guitar-maniac on 2011-01-22
xrandr showed only my primary screen.  I went to Nvidia control panel and tried to put the position of second one in there, but it was greyed out, tho it recognized both monitors. 
I tried that command with the names i got from Nvidia control panel <screen0> and <screen1>, terminal complained something about "newline", it was finnish and i don't exactly know how to translate it to english but here goes: Grammar error near the unexpected keyword "newline".

Here's the command i used: xrandr --output <screen0> --left-of <screen1>

---

### Post by drewsus on 2011-01-22
You have it set up as "Seperate X Screens" but you want it set as "TwinView."

I would suggest just running:
```
sudo nvidia-xconfig
```
Then restart X (log out and in, or restart). 

If that didn't fix it for you, open NVidia X Server Settings:
```
/usr/bin/nvidia-settings
```
Go to X Server Display Configuration
"Configure..."
Set to "TwinView (Requires X Restart)"
(I dont have two screens attached atm so you might have to press "Apply")
Click Save to X COnfiguration File and do so. 
Restart X


**edit:**
As you are Finnish your screen will likely have the buttons and such in your language so if you are having problems I can probably whip up a video showing what I said but I think you will be able to figure it out from here. Just ask for that or more direction.

---

### Post by Guitar-maniac on 2011-01-22
Switched on the Twinview and and saved it to the X configuration file, it's working now! This is the first time ever i have 2 screens, and somehow thought separate screens would be the correct option.. Thanks for the help!

---

### Post by drewsus on 2011-01-22
I am glad to be of service! If you need further help, don't hesitate to ask! 
Do you have compiz enabled? and do you have CompizConfig Settings Manager installed? If so, you may be interested in the "Extra WM Actions" plugin as you can set a keyboard shortcut to move a window back and forth between screens as well as other features. Handy dandy.

---

