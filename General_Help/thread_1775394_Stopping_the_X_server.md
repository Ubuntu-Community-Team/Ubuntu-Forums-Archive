---
title: "Stopping the X server"
date: 2011-06-04
forum: General Help
---

### Post by enimeizoo on 2011-06-04
To try another windows manager, I have to open a new display without a windows manager. The problem is that when I run 
```
startx -- :1
```kde runs automatically on it. 

How can I open a graphic session without a window manager?

(edit) Actually, I just did it. Not sure how, thought... I'd like to know how to do it more reliably

---

### Post by The Geeko on 2011-06-25
I just installed awesome WM and I wondered the same thing...  to choose an alternative WM, you must do so at the time of login... click on your username, then at the bottom of the screen, you will see a drop-down which allows you to select the window manager which you would like to execute upon login...  Choose the one you want, then enter your password and continue...

By the way, (I'm still new at this myself), the UI refers to it as "Session" and the "awesome.desktop" config file is located under /usr/share/xsessions...

Hope this helps.

---

### Post by enimeizoo on 2011-06-25
Well, thanks. 
I found it already, just forgot to notify here.
For some reason kde is called by startx if you don't specify a client. So if I want an empty X session, I have to specify a wrong client. 
```
startx fakeClient -- :1
```
From there, I can launch my window manager. 
I did that only to try it. To install it as others sessions, I had to create a *.desktop file in /usr/share/xsessions/ indeed.

---

