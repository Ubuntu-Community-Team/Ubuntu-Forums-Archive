---
title: "Utility to kill selected window"
date: 2010-01-03
forum: General Help
---

### Post by rpaskudniak on 2010-01-03
Greetings.

Before I was forced to delete (actually rename) my .gnome2 directory in order to get a fresh start, I had an icon on my panel (task-bar? SSSsssss :)  ) that would kill the next window that I clicked.  Useful when a program stops responding.

My problem: Rebuilding my panel, I don't recall the name of that utility.  I had originally copied it off one either the Applications menu or the System menu but I can't find it now.

My questions:
[LIST=1]
[*]What is the name of that *_kill-next-clicked-window_* utility?
[*]What directory (presumably some place under .gnome2) holds the links to the programs on the panels?  My search under the renamed .gnome2 directory yields a lot of nearly empty directories and nothing I can identify as my objective.  (In case I get it into my head to manually edit the panel - not likely.)
[*]Why can't I simply as one *blessed* question per post? :confused:
[/LIST]
Thanks much.

---

### Post by sisco311 on 2010-01-03
```
xkill
```
If memory serves Ctrl+Alt+Esc is the default shortcut to launch it.

---

### Post by chewearn on 2010-01-03
"Force Quit" ?

---

### Post by rpaskudniak on 2010-01-03
Sisco,

Your xkill suggestion basically works and, in fact, I have added it to my system admin menu.  But I don't think that was it, for a couple of reasons:
[LIST]
[*]The utility I had used had its own icon, though I didn't pay attention to what it was. xkill does not seem to have its own icon; it was assigned a generic-looking thing.  I arbitrarily assigned it one that looks like the >POW< in comic books.
[*]It has an undesirable side effect: I tested it by killing a terminal window.  It killed all 3 terminal windows I had open.
[/LIST]

As for chewearn's "force quit".  Sounded promising until I showed that there is no "force quit" command in bash.  Is there another utility I need to know of?  (Wouldn't surprise me; I'm sure there are more commands that I don't know than commands I do know. :redface: )

---

### Post by sisco311 on 2010-01-03
*Force Quit* is a panel applet. Right click on the panel -> Add to panel -> Force Quit -> Add

---

### Post by rpaskudniak on 2010-01-03
Cisco,
Thanks MUCH!!  That was it, down the familiar icon!

Interestingly enough, however, it has the same undesired side effect I mentioned earlier: If I try to close one terminal window, it closes them all.  I'd say that's a little bug, with I may report in launchpad.

I will mark this thread as [SOLVED].

Again, thanks.

---

### Post by MooPi on 2010-01-03
You can create a desktop icon for xkill. Right click on your desktop and create launcher. For command=xkill. then choose and appropriate icon from the list and off you go. Xkill comes without any bugs. It will just shut down whatever is indicated.

---

### Post by rpaskudniak on 2010-01-04
Moopi,
I envy your ability to be so concise.  You made a couple of points in 2 lines where I expend whole paragraphs to make one.  Still, I went with Sisco's suggestion.  It is apparent that the force-kill is a wrapper for xkill.

> You can create a desktop icon for xkill. Right click on your desktop and create launcher. For command=xkill. then choose and appropriate icon from the list and off you go.
It is just as easy for me to create a panel icon for it; as I mentioned earlier in this thread, I had already added one to the [FONT="Courier New"]*System->Administration->System Admin Tools*[/FONT] menu.  I am not a fan of cluttering my desktop with icons, albeit my Windows desktop would lose me some credibility on that point.:^o

> Xkill comes without any bugs. It will just shut down whatever is indicated.
Initially, I was going to argue this point.  As I saw it, closing multiple instances of the same program [when I wanted to close only one] is a bug.  In the case of firefox, all browser windows are being controlled by one process so such [mis]behavior is understandable and I would expect all firefox windows to close if I kill one of them this way.  Besides, in my experience, if one browser window locks up, all are locked up, so you must kill them all.  But that should not be the case with terminal windows.

Then I got to thinking a bit more deeply, a vice I occasionally indulge, and testing.

It appears that while I have many bash windows open, all are child processes to [FONT="Courier New"]gnome-terminal[/FONT].  And xkill is not smart enough to kill only the bash running at that window; it kills gnome-terminal.  Thus, kill one and you kill all.  Thus,  this disagreeable behavior is not the fault of xkill but a side effect of the overly elegant design of gnome-terminal.

FWIW, IMHO, terminal windows should not be so inexorably linked.  After all, I can use Force Quit to kill one [FONT="Courier New"]putty[/FONT] window without hurting the other.

As I stated above, this thread is SOLVED.  The can of worms I just opened is better addressed in the Launchpad.

Thanks for the help and the brain food.

---

### Post by Saiko Berry on 2010-01-04
They arnt. Get urxvt. They arn't linked together.

---

