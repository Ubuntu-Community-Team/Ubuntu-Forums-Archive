---
title: "Really bizarre behavior from Ubuntu suddenly"
date: 2012-01-30
forum: General Help
---

### Post by lavadisco on 2012-01-30
Tonight I go to turn on my laptop, and all programs open with no close/maximize/minimize buttons and no task bar at the bottom. I open up a terminal window, at which point my color scheme switches from my custom scheme to a boring grey one - again, just by opening a terminal window. Anyway, once the terminal is up I type "compiz --replace" (something I found on this forum) and then the close/max/min buttons show up. I go to click on my appearance menu item to change the color back, and just the act of clicking it reverts me back to my custom color scheme. I don't even have to select it once the appearance window comes up. So all of that is pretty weird. But there's more - I have a link on my menu bar to an important folder that's in my /home/user folder. The properties of the link are: file:///home/user/myfolder, it's worked for a long time now so I know it's correct. However, since all this weirdness started happening, instead of opening up myfolder in nautilus when I click the link, it starts playing all the mp3 files in that folder one after the other. Just to check that it's not the link, I follow the main menu all the way through to "places" and choose "myfolder", and the same thing happens. Eventually, my trackpad arrow freezes and I can no longer use it. However, I can still alt-tab around and type stuff. 

What on earth is happening here? I reinstalled Compiz and Nautilus, but it didn't do anything. It's the same story every time I restart. A Win7 install that I have on the other partition works fine. The only thing I did today that might be the cause of this is I uninstalled a bunch of multimedia apps using the software center. But nothing that should have affected the system. Any help is appreciated.

---

### Post by kcirrab on 2012-01-30
What version of Ubuntu?

Have you dropped you computer?

---

### Post by sunfromhere on 2012-01-30
I'm tempted to accuse Compiz, as I've had similar behavior (albeit on Debian, Gnome2 and Compiz).

What Compiz Settings do you use, can you try booting without them, or even removing Compiz and check if the behavior persists?

---

### Post by lavadisco on 2012-01-30
Nope, didn't drop the computer. Sorry, I neglected to mention that I am using 11.04 Natty. I'll try removing Compiz completely when I get home tonight and see what happens.

---

### Post by lavadisco on 2012-01-31
Update: Uninstalled Compiz, but nothing changed. I am totally baffled here.

---

### Post by Bucky Ball on 2012-01-31
Recent update or package upgrade?

---

### Post by lavadisco on 2012-01-31
About 2 months ago, I ran a script that updated my regular Ubuntu install to Dreamstudio. I instantly regretted doing it, because it broke my system initially, but I eventually managed to get it running and it's been great since then. But yesterday I uninstalled some of the numerous multimedia apps that came with it (not system stuff) and that's when all this started happening. Would an update to 11.10 fix this?

Another symptom - my desktop icons have disappeared and right-clicking on the desktop does nothing.

---

### Post by lavadisco on 2012-02-01
Bump.

Tried uninstalling Compiz and using Metacity, and also the opposite, but it didn't help at all. No matter what, I always have to restart my window composite manager to get my window dressings back.

With regard to the lack of desktop icons, I added Nautilus to my startup programs and that seemd to fix it - don't know how permanent a solution that is though.

No luck whatsoever with the panel folder icons opening mp3 files.

Anybody have any more advice?

---

