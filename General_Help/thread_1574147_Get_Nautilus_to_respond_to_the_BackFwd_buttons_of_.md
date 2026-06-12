---
title: "Get Nautilus to respond to the Back/Fwd buttons of my mouse"
date: 2010-09-13
forum: General Help
---

### Post by finny388 on 2010-09-13
Nautilus goes back and forward with alt-left and alt-right.

Just like firefox only firefox responds to my corresponding mouse buttons.

How can I get Nautilus to do that?

If I can't get Nautilus itself to do that, I thought I could bind the buttons to alt-left and alt-right in CCSM. But I don't know how to enter keystrokes as a command.

Any ideas?

---

### Post by finny388 on 2010-09-20
:(

---

### Post by finny388 on 2010-09-25
^

---

### Post by finny388 on 2010-09-29
anyone?

---

### Post by finny388 on 2010-10-06
really?

---

### Post by stinkeye on 2010-10-06
If you can't  find a solution to this you may want to have a look at **easystroke**, 
which allows you to associate keystrokes to mouse gestures.

---

### Post by meijer.o on 2010-10-06
I added this < xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7" > to Startup Applications. I have an Logitech mouse with tilting wheel. You can test in in gnome-terminal.

best regards,

Otto Meijer

---

### Post by finny388 on 2010-10-07
> **stinkeye said:**
> If you can't  find a solution to this you may want to have a look at **easystroke**, 
which allows you to associate keystrokes to mouse gestures.

I installed but it doesn't seem to allow associating keystrokes to mouse buttons.

---

### Post by finny388 on 2010-10-07
> **meijer.o said:**
> I added this < xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7" > to Startup Applications. I have an Logitech mouse with tilting wheel. You can test in in gnome-terminal.

best regards,

Otto Meijer

I tried  in terminal```
xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"
```but nothing happened. What is it suppose to do?

---

### Post by stinkeye on 2010-10-07
Open up easystroke preferences
  Expand additional buttons and click on the add button.
Down the bottom, tick **instant gestures**.
Click the mouse button you want to modify inside the box.

Open the actions tab and
add an entry of type key and put in your keystrokes.
Click on record stroke and then click the mouse button you added and it should look like the second pic.

---

### Post by finny388 on 2010-10-07
Thanks

It doesn't see the back/fwd buttons.
It does see left/right buttons (as 1 and 3)

It didn't see the middle button either.

:confused:

---

### Post by finny388 on 2010-10-07
I noticed the empty dropdown on the Add window.

I picked button 2 and Instant Gestures and it added to the Addition Buttons list.

I then added 4,5,6.

Then I went to the Actions tab, added Nautilus with Add Application.
Then Add Action, with Key, Alt-Left.
Then Record Stroke, the dialog box comes up but does not react when I press the mouse's back button or any other button (left, right).

strange

---

### Post by stinkeye on 2010-10-07
Works fine here with a logitech G5.
Make sure firefox and nautilus are closed, restart easystroke and try again.
May help?????

You could just map the keys to a gesture instead of a button.

---

### Post by MiniMe on 2010-10-15
Just a quick thanks for sharing the info about easystroke. Works very well for me. 

In case it helps, there's also some helpful documentation at: [http://sourceforge.net/apps/trac/easystroke/wiki/Documentation](http://sourceforge.net/apps/trac/easystroke/wiki/Documentation)

---

### Post by finny388 on 2010-10-15
thanks MiniMe
I'll take a look when I have a minute

right now I'm in the process of moving and my place is a disaster

hopefully back to trouble shooting in the next few weeks

:P

---

