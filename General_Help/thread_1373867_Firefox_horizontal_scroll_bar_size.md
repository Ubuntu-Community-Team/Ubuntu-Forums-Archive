---
title: "Firefox horizontal scroll bar size"
date: 2010-01-06
forum: General Help
---

### Post by sisyphus1978 on 2010-01-06
I've been working on tightening up my firefox display. I've managed to cut down the vertical scrollbar. Anyone know how to do the same with the horizontal scroll bar. See screenshot?

I'm running this on an eeepc 701 (hence the small screen size).

From my userchrome.css

> /* hide vertical scrollbar */
notificationbox {
    overflow-x: hidden;
}

browser[type="content-primary"], browser[type="content-targetable"] {
    overflow-y: scroll;
    margin-right: -12px; /* 12px == width of my scrollbar */
}


---

### Post by sisyphus1978 on 2010-01-06
I upgraded to the latest firefox beta but still no luck. In fact if you look at the two screenshots, it seems as though different pages result in different behaviours.

I may just give up and forget about changing it...

---

### Post by howefield on 2010-01-06
Try this, it will reduce the scroll bars in more than Firefox though, so if it isn't what you want, just delete the file.

Open a terminal (Applications > Accessories > Terminal) and type

```
gedit ~/.gtkrc-2.0  --
```

Paste the following in to the document and save. 8 is the size I use, you can change to suit yourself.

> style "scroll"
{
    GtkScrollbar::slider-width        = 8
}

class "*" style "scroll"

Reload firefox if it was running when you created the file.

---

### Post by sisyphus1978 on 2010-01-06
Thanks for that, but most of my computer usage is via ssh (x forwarded and vanilla). I don't want to reduce the scrollbars on my desktop (the computer I ssh into) just reduce horizontal scrollbar in firefox. The vertical scrollbar looks so good, I thought I would see if I could replicate on the horizontal.

---

### Post by howefield on 2010-01-06
In that case try this...

Open a terminal and navigate to..

/home/username/.mozilla/firefox/j9sj4hbo.default/chrome

(You may have a different folder to j9sj4hbo.default)

and create a file with the content below and call it userContent.css


> scrollbar[orient="vertical"] scrollbarbutton,
scrollbar[orient="vertical"] slider,
scrollbar[orient="horizontal"] scrollbarbutton,
scrollbar[orient="horizontal"] slider{
height: 8px !important;
width: 8px !important;
}

---

### Post by sisyphus1978 on 2010-01-06
Thanks for trying Howefield, but the only code that I can get to change my ff scrollbars is the one in my OP. And still it only applies to the vertical, not the horizontal. I would be perfectly happy with a) no horizontal scrollbar or b) no horizontal or vertical scrollbar (i mean it's pretty obvious if a page is going to scroll). But atm the current state is inconsistent behaviour across pages (and the horizontal is twice as large as the vertical). Such non-symmetry does my nut right in (if you pardon the expression).

I guess I could go exploring over at the mozilla board (or investigate an addon to achieve the effect - though I don't really want to install a program just to change the scrollbars)...

---

### Post by sisyphus1978 on 2010-02-02
I solved it. From userChrome.css 

notificationbox {
overflow-x:  hidden;
margin-bottom: -12px;
}

browser[type="content-primary"],  browser[type="content-targetable"] {
overflow-y: scroll;
margin-right:  -12px; /* 12px == width of my scrollbar */
}

---

