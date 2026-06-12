---
title: "MATLAB - a long title in a plot makes compiz go haywire"
date: 2009-07-15
forum: General Help
---

### Post by ububot on 2009-07-15
This is a long-standing issue I've had, and completely reproducible. If I make a plot in MATLAB, and then go insert -> title, and type a very long title that goes off the edge of the plot's window, my screen flashes a bunch of times, artifacts show up all over the place, etc. (I'm attaching 5 screenshots of the craziness.)

I am running jaunty with compiz enabled, dell d830 with nvidia drivers. The newest compiz and drivers are able to "recover" somewhat, and if I do ctrl-alt-F1 and then back (ctrl-alt-F7), I can still use my computer, though with a lot of artifacts on the screen. Previous versions of compiz / nvidia drivers the only way to get back is to do a hard shut down. The problem does not exist when running on metacity. I don't get any errors in a shell if I run matlab from a terminal.

I asked Mathworks about it but they're not going to do too much right now because they blame it all on compiz/java, but I haven't seen any compiz problems this bad. Either way, hopefully there is a compiz/java fix to it.

To reproduce:
1. start matlab
2. plot(1:10)
3. insert -> title -> enter something really long that goes off the plot's window edge
4. Watch as graphics goes haywire
5. Hopefully tell me how to fix it!

Thanks in advance!

---

### Post by XCan on 2009-07-16
I just tried it. It indeed messes up everything, I had to drop to console and kill matlab to kill off most of the artifacts. Have you asked this in mathwork's forum? 

Anyway, a simple workaround which I just tried is simply not to use Matlab's GUI tools (they suck anyway and produce inconsistent figures) and use title('your title here').

---

### Post by ububot on 2009-07-16
I have not posted in Mathematica forums, but I've spent a good deal of time back and forth with Mathworks tech guys themselves, and they did not know how to fix it.
It is true that not using the GUI gets around the problem, but often it is easiest to use the GUI (that's why it's there, right :) ). It's also sort of embarrassing, I have to admit, when someone borrows my computer for a quick plot and then crashes everything... and then I find myself defending linux again, etc. In any case, I would love to find a fix.

---

### Post by XCan on 2009-07-16
True that, the gui is there to 'appear' to make things easy (in the case of Matlab). :D I just find it totally rediculess that it changes the format/size/layout and what not when exporting figures if one uses the GUI. Anyway, that's another discussion.

Unfortunately, I don't have a solution for this, but I think you should ask an admin to move this thread to the Educational part of the forum, as I believe there are far more users, relatively, using Matlab there. :)

---

### Post by ububot on 2009-07-16
hm, okay. You mind telling me how to do that, this is my first time actually starting a thread on the forums.
... I agree, anytime I have a final plot I want to make, the best way to do it is not through the gui, but in the in between steps it's nice to have it working...

---

### Post by ububot on 2009-08-04
XCan, I have just tried a second to contact an administrator via the "contact us" link at the bottom of the page - I hope this is the correct way of requesting a move to the Educational part of the forums. I got no response the first time, and it has been a few weeks. 

In the meantime, if there is anybody who has an idea of how to fix this problem, please post!

---

### Post by 3Miro on 2009-08-04
I tried it, I cannot change the title. No pop-up shows up for me when I go to Insert -> Title. (9300M + 1.80 drier + 8.10 + compiz)

Have you tried to play around with the compiz settings, i.e. disable windows decorations and other stuff like that. The problem may be related to something along those lines.

---

### Post by ububot on 2009-08-04
There's no popup for insert -> title, there just appears a little white rectangle spot above the plot with a cursor in it.
As for playing around with compiz settings, I have not tried to go through and turn off individual settings, but I know that running metacity instead of compiz the problem goes away.

---

### Post by ububot on 2009-08-12
Anybody else with this problem?

---

