---
title: "Firefox menus don't work!!!!"
date: 2010-11-06
forum: General Help
---

### Post by windyweather on 2010-11-06
How could this be?

Ubuntu upgraded to 10.04 a few days ago. System including firefox worked just fine. Video card added 2 days ago. Everything worked fine then.

Now...

Firefox menus ignore mouse clicks.

Toolbar works fine. and "back" button brings up a website. But main menu and bookmark tool bar just ignores mouse clicks. Bookmark toolbar highlights on mouse-over, but click does not pull it.

Firefox updated to 3.6.12 - I assume, but I can't pull the about menu now.

All other system menus and Nautilus menus work just fine.

I have restarted a few times - and once just now - to try to clear the problem.
System is not busy - so it's not like FF is hung in a CPU loop.

Another system I have [VIA based] that was upgraded at the same time shows normal behavior.


What could possibly be wrong that would cause this???
Any suggestions for how to fix?

Thanks,
ww

---

### Post by wojox on 2010-11-06
Start Firefox from a terminal and check if it displays any errors in the output. 

[Common Issues & Solutions]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html")

---

### Post by windyweather on 2010-11-06
> **wojox said:**
> Start Firefox from a terminal and check if it displays any errors in the output. 

[Common Issues & Solutions]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html")

Ok.. Sorry for being such a noob, but after I get the terminal up - which I can do - how do I start Firefox from the terminal?

No clue what the path is or what the name of the program is?

Simple as typing "firefox" to the prompt?

Thanks,
ww

---

### Post by sikander3786 on 2010-11-06
> Simple as typing "firefox" to the prompt?

Exactly. Just type

```
firefox
```

---

### Post by windyweather on 2010-11-06
No errors running from terminal. FF worked fine.
And running it normally worked just fine too. 

So not sure if condition cleared itself before I ran from terminal or not.

Thanks,
ww

---

### Post by JoachimDurchholz on 2010-11-07
I have the same problem.
I have been noticing that no menus would work after an upgrade, but that phenomenon would go away after a restart. Starting today,the menus stopped working even though no update was done and even after an FF restart.

The menus that don't work are:
* Right-click menu on links (disables important functionality)
* Bookmark toolbar (left or right click) (not too important, Ctrl-B calls up the bookmarks in another window that works fine)
* The main menu (File/Edit etc.). (Disables a whole lot of important functionality.)
Also, URL completion in the URL input field stopped working, and FF "forgot" all saved passwords. This looks like some basic infrastructural stuff in the GUI got wedged, maybe on the Chrome level.

Interestingly enough, while a restart didn't help, calling up the bookmark window with Ctrl-B fixed the issue. I'll restart Firefox and see whether that "spontaneous self-correct" persists, and edit this post accordingly.
[EDIT] Yup, it still works. Of course, something inside the pages I surfed to find a cure might have unwedged Firefox, too.
BTW I forgot to check remembered passwords before the FF restart, but they're now back, too.

---

### Post by windyweather on 2011-05-30
This just happened again. Starting firefox from a terminal cleared it. Now when I start it normally, it works just fine.
Important safety tip... Wow strange bug.
This time it was FF4 on 10.04.
Bug is still with us after all this time and a major release of FF.

- d

---

### Post by sea-geek on 2011-06-09
Just used this to fix my 11.04 system running firefox 4.0.1

---

### Post by wolfgangmcq on 2011-06-18
I've found the same thing, both on Maverick and (I think) on Karmic. There's no one solution that always seems to work. Anyone have any ideas?

---

### Post by TheoryOfGravity on 2011-07-02
Thanks for this thread and fix.

I just got a Dell Vostro v130 running 10.04 running default installed FF v3.6.3 and a few of my own Add-on preferences. I was messing around updating Avast! which wasn't working. So I saved my tabs and closed the lid to work on it later.

When I came back, I turned FF back on. Three instances of FF started but none of my tabs. So I closed it all thinking I multi-clicked the icon.

I tried again. This time I know I clicked the icon only once. Still, two instances of FF started and still no tabs. 

Next I went to

```
System > Administration > System Monitor
```and stopped processes "***firefox***" and "***firefox-bin***". That helped stop the multiple instances and I got my tabs back, but now I noticed I didn't have toolbars. In fact, I had the same quirks Joachim listed. 

So after reading advice here, I opened the terminal from ```
Applications > Accessories > Terminal
```and it worked. To final-check it, I closed FF so I can turn off the Terminal. I restarted FF on its own and everything worked.

Hope this helps!

Thanks!



edit: When I ran FF from the terminal, the terminal produced an error message. Something about a "collision". I forgot to write the exact message down when i restarted everything so I can research it. But it doesn't reproduce the error anymore.

---

### Post by edcompsci on 2011-07-26
I see this thread is from last year, but it came up at the top of my google search. I am running Maverick and it is unresponsive to mouse clicks. Chromium and Epiphany work fine. Running in terminal does nothing different.Even after crash when it askes to resotre new session or restore old session(s) it is unresponsive. Just wanted to see if this is just mine or anyone else experiencing this. 

other factors that may have caused this: I recently installed 2 virtual machine drives using virt-manager (kvm). It seems to have started since this, or else from recent firefox updates.

---

### Post by perky on 2011-07-26
Just used this to fix menus in 11.04 FF 5.0. (closing, opening from terminal, right/menu clicking, close FF, reopen normally and works!)

---

