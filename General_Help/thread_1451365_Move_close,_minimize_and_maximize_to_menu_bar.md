---
title: "Move close, minimize and maximize to menu bar"
date: 2010-04-10
forum: General Help
---

### Post by zorkerz on 2010-04-10
I have a small screen and like to save my screen space as much as possible. One way I have done this is by turning the window title font to 0 under system->preferences->appearance|>fonts, effectively shrinking the title bar. (Note: this works to different degrees depending on the selected theme) The down side to this is that the close, minimize and maximize buttons can become distorted and hard to click.

So I was thinking is there any way to move the those three buttons down to the menu bar which usually has tons of extra space?

---

### Post by blueridgedog on 2010-04-10
Not an answer, but some suggestions.  Isn't clicking the show desktop button the same as the minimize?  Also, keyboard "alt" and a right mouse click in the window will give you a menu to minimize, restore, close or maximize.

---

### Post by zorkerz on 2010-04-11
Your right blueridgedog there are alternative ways to to do all three actions, however, having them visible on the menu bar would be preferable for other people who use my computer. I still don't know how to completely get ride of the title bar though.

---

### Post by blueridgedog on 2010-04-11
I assume you have hit the obvious - turning your dpi up to 72 or beyond (appearance, fonts, details button then DPI), running the compact theme by installing gnome color chooser.

If you really want to get into the bolts of it then you can edit config XML file for the theme you are using.  For Human that would be:

/usr/share/themes/Human/metacity-1/metacity-theme-1.xml 
 
Make a backup before you edit it and read the entire file.  You will be able to figure out how to tweak things to your liking.

---

### Post by zorkerz on 2010-04-11
Thanks for the input i have not actually gotten then deep into it yet.

I have a question about DPI. When I raise the DPI IT makes the words in nautilus windows and title bars get larger and larger so wouldn't a smaller dpi save more space on the screen albeit being harder to read?

I should have remembered what the DPI setting started at I think it was 96 but it was definitely higher than 72 to begin with.

---

### Post by blueridgedog on 2010-04-11
If you went down, then things did get "bigger" so to speak.  Play with it and see if you can get something you like.

---

### Post by zorkerz on 2010-04-11
My text gets bigger as my dpi goes up. i.e. as you raise the number of dots per inch the words and title bars appear bigger on the screen.

---

### Post by Klump on 2010-04-11
I'd suggest installing *maximus* package which is used by Ubuntu Netbook Remix. When you maximize a window, it disables title bar. Also I'd suggest installing *window picker* alongside maximus and use it instead of the default window list. So, when you maximize, title bar is disabled and you can close the window from the task bar by clicking 'x'. Hope that helps.

---

### Post by blueridgedog on 2010-04-11
> **zorkerz said:**
> My text gets bigger as my dpi goes up. i.e. as you raise the number of dots per inch the words and title bars appear bigger on the screen.

I may have it backwards...but move it in each direction until you are happy.

---

### Post by zorkerz on 2010-04-11
maximus and window-picker-applet are cool packages it makes me want to check out ubuntu netbook remix again but my 10.1" screen is really a little big for what it offers. I don't yet have an x in my taskbar for closing windows. Any idea what I need to add to get one?

---

### Post by blueridgedog on 2010-04-11
Right click then close?....sorry I know you are looking for something more elegant and something that others can use.  I will keep looking.

---

### Post by zorkerz on 2010-04-11
Thanks for all the input both of you.

---

### Post by Klump on 2010-04-12
Wait, there's no X with window-picker applet? Hm... Well, you can bind for example Alt+f1 to maximize and undecorate and Alt-F2 for unmaximize and decorate windows in your window manager. That's what I'm using right now with my openbox (don't know about others, all I had with metacity was fullscreen with alt+f11 of any application) :)

---

