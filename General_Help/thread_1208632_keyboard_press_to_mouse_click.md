---
title: "keyboard press to mouse click"
date: 2009-07-09
forum: General Help
---

### Post by pedrom169 on 2009-07-09
is there anyway in ubuntu to make it so when i press "f1" for example it goes to a preset co-corindate on my screen and proforms a mouse click?

Thanks

---

### Post by rainwalker on 2009-07-09
I don't think you could use F1 simply because it's a universal "help" button, but there might be a way to do what you want using Compiz. I'm not sure how, but hopefully this post will bump up your thread so someone else will reply.

---

### Post by jonobr on 2009-07-09
I dont get what you mean.

You want to push a button for it to go to a certain place and do a mouse click, makes it sound like you want to push a button so it runs something
Is that the case?

---

### Post by pedrom169 on 2009-07-12
for example:

i am playing a online text game where i click attack. i want to be able to press a key (like a, b, c etc) or a combination (ctrl a, ctrl b etc) and this makes the mouse cursor move to a set co-ordinate on the screen like 400, 400 and proform a left mouse click which will press the attack button for me.

any better?

---

### Post by pedrom169 on 2009-07-13
bump up to the top.

anybody?

---

### Post by nice_like_rice on 2009-07-13
yeah I know how one sec just finding a link

---

### Post by nice_like_rice on 2009-07-13
Ok, so (as usual) I'm sure there is a much better way of doing this involving something like KDEhotkeys, but one way to do this would be binding a key to an xmacro using xbindkeys like this user did : [http://fixunix.com/x/19649-using-xmacro-xbindkeys.html](http://fixunix.com/x/19649-using-xmacro-xbindkeys.html)


Another useful link [http://ubuntuforums.org/showthread.php?t=968530](http://ubuntuforums.org/showthread.php?t=968530)

Not a pretty way of doing it, but it should work fine :)

Say if you have any problems setting it up.

edit: it might be possible to do this directly with xbindkeys, I'll post again later...

---

### Post by pedrom169 on 2009-07-13
how would i put in the file to set it so like

f1 = mouse click at a certain co-ordinate?
f2 = same
f3 = same

Thanks

---

### Post by nice_like_rice on 2009-07-13
Ok so here we go :)

First, you must install xmacro and xbindkeys

```
sudo apt-get install xmacro xbindkeys
```

Next, you must create a file called ".xbindkeysrc" in your home directory (if you type xbindkeys and follow the instructions there, I think it creates one for you with some command like xbindkeys --default or something), and edit the file. This file should be completely empty apart from the following:

```

"echo 'MotionNotify 100 100 ButtonPress 1 ButtonRelease 1'| xmacroplay :0.0"
    m:0x0 + c:67
    F1
"echo 'MotionNotify 100 100 ButtonPress 1 ButtonRelease 1'| xmacroplay :0.0"
    m:0x0 + c:67
    F2
"echo 'MotionNotify 100 100 ButtonPress 1 ButtonRelease 1'| xmacroplay :0.0"
    m:0x0 + c:67
    F3
"echo 'MotionNotify 100 100 ButtonPress 1 ButtonRelease 1'| xmacroplay :0.0"
    m:0x0 + c:67
    F4

```

Now, you must stop xbindkeys from running, and start it again. (It was running twice with me?)

```

killall xbindkeys
killall xbindkeys
xbindkeys

```

Now it should work. Notice in the configuration file there are two numbers, in my case "100 100". These are the x and y coordinates of where the click should be, you should change these accordingly ;)


*It is possible to use xmacrorec to get the coordinates of a click, but for some reason I can't get it working today*

---

### Post by pedrom169 on 2009-07-13
it is not working for me. did it work for you?

---

### Post by nice_like_rice on 2009-07-14
Yes, it worked perfected for me. What problems are you having with it?

---

### Post by pedrom169 on 2009-07-14
i did what you said killall xbindkeys

ran xbindkeys in terminal

and tried pressing the keys and they wasnt moving the curser.

---

### Post by PGScooter on 2009-07-14
It worked for me, but only for F1. The others did not work. I tried changing the order, and making sure the syntax was right, but F2 through F4 are being difficult.

---

### Post by PGScooter on 2009-07-14
strange! when I put the command ```
xbindkeys_show
``` it shows all of the entries as having F1 (even though in the .xbindkeysrc they have F1,F2,F3,F4). Is this a bug or am I misunderstanding xbindkeys? What does that command show for you guys?

---

### Post by PGScooter on 2009-07-14
after deleting the line ```
m:0x0 + c:67
``` everything worked fine for me. nice_like_rice, what does that line of code do?

---

### Post by nice_like_rice on 2009-07-15
m:0x0 + c:67 specify the modifiers for that specific key - I have a german keyboard, that may have interfered with it. If you run 

```
xbindkeys -k
```

and then press, for example, F1, it will tell you the code you need to put in that file to bind to that specific key, that was how I got that code.

Sorry for the late reply :)


Pedrom - the click is almost instant, are you sure it's not clicking and you're not noticing or something (because it's clicking in an arbitrary place?). Otherwise, try removing the lines PGScooter mentioned, and if that still doesn't work, try "xbindkeys -k" to find out the code you need. 

david

---

### Post by PGScooter on 2009-07-15
ah, you're right, that must be it. My xbindkeys -k when I put "F1" just shows an "F1". Be careful though, you can't use a lowercase f.

---

### Post by nice_like_rice on 2009-07-15
Ok good :) my fault, didn't realise there were differences across keyboards (or maybe mine is just strange or something).

---

### Post by PGScooter on 2009-07-15
no worries, now I learned something new and we have a suggestion for the developer (xbindkeys_show should have given an error, but it did not). He hasn't emailed me back about my suggestion regarding case-insensitivity (control works instead of Control but f1 does not work instead of F1) so I don't know if he wants suggestions or maybe he's not even working on it anymore.

---

### Post by pedrom169 on 2009-07-16
that it is just not clicking. do i need something else running. when i type xbindkeys in terminal nothing happens and even if i type killall xbindkeys it says "xbindkeys: no process killed" as if its not running

---

### Post by pedrom169 on 2009-07-31
This is all sorted now. My own fault

SOLVED

---

