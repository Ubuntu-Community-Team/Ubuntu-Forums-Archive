---
title: "Help Creating an Applet"
date: 2010-11-26
forum: General Help
---

### Post by ngrieb on 2010-11-26
Hi,
I have a fairly good chunk of python code I created because I was annoyed with the stupid clock turning on it's side when you pull the panel to the left or to the right (yes I know about cairo-clock, but it was too intrusive). Anyways, I was hoping to make a small clock applet that simply allows you to hide the clock and a few more functions in an icon on the panel, and shows with a transparent layer with date and time info on mouse over. I think this can be done easily enough using a few pygame calls, but I would have no clue as to how to stick the icon on the panel afterwards. 

The thing I need to know then is how to run it as or make it into an applet. 

I have a fairly decent programming background, so I should be able to pick up on most of what you send me, but I have only recently picked up python so I might need to know a few things, such as if the sleep function continues using memory when called in python...  

I appreciate the help and will of course share the end result.

---

### Post by ngrieb on 2010-11-27
Even simpler than the above would be to simply pipe the time and date text to libnotify. Does anyone know how to do this? It seems as though it should be fairly straight forward, but I have never messed with GTK applets or other Gnome GUI calls.

Thanks.

Found a great tutorial for this here: [http://roscidus.com/desktop/node/336](http://roscidus.com/desktop/node/336)
and it was as easy as I thought it would be. Hope this saves someone a bit of time.

---

### Post by ngrieb on 2010-11-27
I still have no idea how to create an applet...I have been searching all over the place, but I am not quite sure where to look, and what I have found has been very complex looking.
 
Is there a need to be familiar with pyQt in order to do this?
I have no experience with Qt or PyQt so maybe someone could give me a quick reference to the calls needed for the creation of a radio or check button and a number scroll button so that one can set a time. Thanks.

Alright...I have found a great applet tutorial that made some sense to me, and have the beginnings of a good looking applet. 

I was just wondering how I should run the pieces of the program ... seeing as some processes need to run in the background for a long time without doing much, while the clock display itself should only show when provoked. All of the scripts are written in python, and I would like them to all start up at the same time, and end when the applet is killed. 
Now I know that I can either spawn or thread the other scripts into the program, but I have never don e this before and I would not know what the advantage of one over the other is, and how it applies to my situation. Is there another way to run a python script or function from another python script without using a thread or spawning? If not which one should I use?

---

### Post by ngrieb on 2010-12-02
Ok, got most everything working in a windowed mode, but I am still having trouble with the applet server excepting the run. Is there anyone out there that has written a python applet and can help me work out some of the bugs? It is almost finished.

Thanks.

---

### Post by ngrieb on 2010-12-02
I think this now works as a separate program, but the child process initializations or bonobo timeout seems to do something to the sounds that are supposed to play. I would also like if someone could show me how to redo menus in Qt, make mouse-overs happen, and help me get this working with bonobo...

Can anyone tell me what is wrong with the .server file? As of right now adding the file to the /usr/lib/bonobo/servers/ folder only makes bonobo crash ...  :-(

---

