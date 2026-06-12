---
title: "Natty Narwhal design+look changes"
date: 2011-06-15
forum: General Help
---

### Post by Dannylee on 2011-06-15
Hey all,
I recently upgraded to Natty, and although it looks sweet with that new menu, I must say it is quite unorganized and slow. I liked the older ubuntu menu's better where everything was neatly sorted and organized, now for almost every program i need to search it up and/or press a few buttons just so I can finally get that Category button to pop up so I can choose the category in what the program might be in. Also with the side bar i can't open multiple windows; for example with my home folder I can only open one at a time, making it a pain to copy files in between folders. Also command lines: I open one up, minimize it for whatever reason and then when I want to reopen it in the side bar by clicking on it it starts a complete new command line!!! (note: I have the command line pinned to the side bar)
It is also pretty glitchy and slow at times, programs won't open up sometimes or the minimize/close/resize at the top "glitch" out and I have to use the command line to quit the window/program.

The new versions also seems to be a lot slower than the others IMO. My computer isn't the fastest and newest, but for all the other Ubuntu versions my 1gb ram and dual core were more than enough power, while now with Natty it takes longer to open up stuff, video players have many bugs and are "lagging", also a lot more programs (mainly games) crash on me or freeze than in any other Ubuntu version.
I don't want to be a negative Nancy here, and the Dev. team did a great job and I like the futuristic new look of Ubuntu, but I must say it is still somewhat buggy and slow IMO.

Any help how I can fix the bugs, "lag" and make the menu more categorized/organized??
Thanks all.
Dan

---

### Post by DirtyPC on 2011-06-15
Thats called Unity, you want Gnome.
After selecting your login name on the bottom of the screen you will see the desktop options. Choose Ubuntu Classic. You will be back in your familiar Gnome desktop.

---

### Post by DirtyPC on 2011-06-15
run sudo apt-get upgrade to get the latest updates, should fix most bugs

---

### Post by Dannylee on 2011-06-15
Thanks for the help, I put it back to gnome, but now the problem is that the menu bar above the windows are gone! In Unity it used to be in the upper task bar but since I changed it it completely disappeared. Is there a way to put the menu bar back directly on top of the windows like in the older Ubuntus and like in MS Windows?
Thank you for your help
Dan

---

### Post by wildmanne39 on 2011-06-16
> **Dannylee said:**
> Thanks for the help, I put it back to gnome, but now the problem is that the menu bar above the windows are gone! In Unity it used to be in the upper task bar but since I changed it it completely disappeared. Is there a way to put the menu bar back directly on top of the windows like in the older Ubuntus and like in MS Windows?
Thank you for your help
Dan
Hi please include a screen shot of your desktop.

---

### Post by wildmanne39 on 2011-06-16
Hi, I found this link see if it helps.
[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

---

### Post by Dannylee on 2011-06-16
the picture is in the attachments.
The encircled area shows that there is no menu bar above the window, this happens to all the windows except for a few such as google chrome (my guess that is because it has its own appearance settings). Is there a way to get that menu bar back?
Thanks

---

### Post by dFlyer on 2011-06-16
You said you upgraded to 11.04. Was this fresh install or an upgrade from 10.10 using update manager? I've been using unity since beta 1 and have found it fairly stable for being a recent desktop environment, and it very responsive. I always do a fresh install and keep my system up to date.

---

### Post by Dannylee on 2011-06-16
> **dFlyer said:**
> You said you upgraded to 11.04. Was this fresh install or an upgrade from 10.10 using update manager? I've been using unity since beta 1 and have found it fairly stable for being a recent desktop environment, and it very responsive. I always do a fresh install and keep my system up to date.

I upgraded it using the update manager

---

### Post by Dannylee on 2011-06-19
anybody know how to fix that menu bar problem?

---

### Post by lemonchicken on 2011-06-19
classic view>>auto hide top and bottom panels>>dust theme>>window button layout as menu:close. sorted.

---

### Post by pqwoerituytrueiwoq on 2011-06-19
> **Dannylee said:**
> the picture is in the attachments.
The encircled area shows that there is no menu bar above the window, this happens to all the windows except for a few such as google chrome (my guess that is because it has its own appearance settings). Is there a way to get that menu bar back?
Thanks
[alt]+[f2]
[FONT=Courier New]gtk-window-decorator[/FONT]

---

### Post by Dannylee on 2011-06-19
> **lemonchicken said:**
> classic view>>auto hide top and bottom panels>>dust theme>>window button layout as menu:close. sorted.
I dont like the looks of that theme. Anyways how is that going to get my buttons back?

> **pqwoerituytrueiwoq said:**
> [alt]+[f2]
[FONT=Courier New]gtk-window-decorator[/FONT]
I did it, but nothing is happening in the terminal, it doesn't give me any response at all for 10 minutes now

---

### Post by arukaddp on 2011-06-19
Looks like your window manager is not started.

I would say to install Compiz Fusion Icon from which you can restart/replace the window manager and play around with it.

Did you make any modifications in themes or anything like that?

---

### Post by Dannylee on 2011-06-19
> **arukaddp said:**
> Looks like your window manager is not started.

I would say to install Compiz Fusion Icon from which you can restart/replace the window manager and play around with it.

Did you make any modifications in themes or anything like that?

compiz is installed, but idk what changes to make to get that menu bar back. And all I did was I changed from the Ubuntu Natty theme back to Ubuntu classic, that's when the menu bars disappeared.

---

### Post by arukaddp on 2011-06-19
Compiz Fusion is not installed automatically with Compiz. It is a different package and you have to install it manually from the Software Center. 

I just tried it in the terminal and this should start the compiz decorator:

/usr/bin/compiz-decorator &

I'm not an expert but I had some problems recently also and I've played around with it a bit.

Also you might want to look in CCSM > Effects > Window Decoration > Command and see what you have in there, I for instance have the above line, if you reset it it should also bring that line.

---

### Post by pbhill on 2011-06-20
> **harrylucas1 said:**
> Thats called Unity, you want Gnome.
After selecting your login name on the bottom of the screen you will see the desktop options. Choose Ubuntu Classic. You will be back in your familiar Gnome desktop.

I just upgraded and wish I hadn't. I don't understand your answer. Where is the login at the bottom of the screen? I can't get rid of this Unity Desktop fast enough!

---

### Post by Larkspur on 2011-06-20
> **pbhill said:**
> I just upgraded and wish I hadn't. I don't understand your answer. Where is the login at the bottom of the screen? I can't get rid of this Unity Desktop fast enough!

When you're on the login screen, choose your account as normal.  When the password prompt appears, the bar at the bottom will show some session options.  Click on the box which has "Ubuntu" in it and choose the Classic Gnome option.  Log in, and Unity should be gone.

---

### Post by pbhill on 2011-06-20
OK, Got it! I didn't realize I had to restart. I'm back to normal and can navigate around my computer again! Whew!

---

### Post by Dannylee on 2011-06-20
I FIXED IT!!!!!!!!!!!!!
Thanks so much guys, what I did i opened up the Compiz fusion Icon (which I already installed a week ago) and then when i started the icon i went on "Select Window Manager" then I switched from compiz to Metacity.
YAAAAAAAAAAAAAAY!!!!!!!
Thanks everybody for your help. 
I can actually close, maximize and minimize my windows now!

---

### Post by pqwoerituytrueiwoq on 2011-06-20
> **Dannylee said:**
> I did it, but nothing is happening in the terminal, it doesn't give me any response at all for 10 minutes now
that should have started the program that runs the title bar

---

### Post by wildmanne39 on 2011-06-21
Hi, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by Dannylee on 2011-06-21
> **wildmanne39 said:**
> Hi, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

will do sir

---

