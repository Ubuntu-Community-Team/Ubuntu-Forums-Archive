---
title: "&quot;Home&quot; loads Evolution instead of moving about the document"
date: 2010-03-03
forum: General Help
---

### Post by kittybrat on 2010-03-03
I just did a clean install of Ubuntu 9.10 Karmic last night (completely wiping out Jaunty), and since the install, my "Home" key hasn't worked right.  To be more specific, it's the Home button that exists in within the 6 keys: Insert, Home, Page Up, Delete, End, Page Down - not the Home button within the number pad.

The other keys work properly, but Home keeps loading Evolution.  I removed Evolution to see if it would stop, but of course it didn't.  (I didn't think that would work, but it was worth a shot.)

I can't seem to find any help online... can anyone here help me?  I didn't have this problem with Jaunty nor with Intrepid, so I'm at a loss.

This keyboard is very similar to the one I am using: [http://www.mikecase.net/ModelM/IBM-Model-M-Keyboard.jpg](http://www.mikecase.net/ModelM/IBM-Model-M-Keyboard.jpg)
A big difference between that one and mine is that I have the windows buttons on mine, so I guess it's a bit newer than in the link.


Thanks.

---

### Post by Swagman on 2010-03-03
Doesn't do anything on my system either (9:10)

btw.. Evolution has dependencies. Removing Evolution may well have b0rked other things on your system.

---

### Post by kittybrat on 2010-03-03
> **Swagman said:**
> Doesn't do anything on my system either (9:10)

btw.. Evolution has dependencies. Removing Evolution may well have b0rked other things on your system.

Yeah, I'm sure... like what, though?  Everything it removed with it looked like it only went to Evolution.

---

### Post by Alexandre Putt on 2010-03-03
Funny. What is the "launch email client" shortcut assigned to on your computer?

---

### Post by philinux on 2010-03-03
> **kittybrat said:**
> Yeah, I'm sure... like what, though?  Everything it removed with it looked like it only went to Evolution.

It only removes evo now. Previously it would have borked a system. Not now though.

Check system>prefs>keyboard shortcuts.

---

### Post by kittybrat on 2010-03-03
> **philinux said:**
> It only removes evo now. Previously it would have borked a system. Not now though.

Check system>prefs>keyboard shortcuts.

Oh okay... yeah, I wated to remove it on Jaunty or Intrepid, but I remember being scared off.  This time it didn't cause an alarm.  Thanks.

As far as my original question...
I checked the keyboard shortcuts.  It said FX86Mail, which I changed to Scroll Lock (since I couldn't remove the shortcut)... but even after that, Home didn't work.  I went back in and clicked Home for a shortcut, and it displayed FX86Mail again.

I looked through the rest of the options in there, but I can't seem to find an area to make the Home button do what it's supposed to do.  Any more advice?

---

### Post by Alexandre Putt on 2010-03-03
Is the keyboard/button actually working right? Can you verify that? The easiest way may be to check if it works the right way outside of X11.

---

### Post by kittybrat on 2010-03-03
> **Alexandre Putt said:**
> Is the keyboard/button actually working right? Can you verify that? The easiest way may be to check if it works the right way outside of X11.

The keyboard is working right, yes.  I would assume the button is working right.

---

### Post by Alexandre Putt on 2010-03-03
> **kittybrat said:**
> The keyboard is working right, yes.  I would assume the button is working right.

Well, I'd still check if pressing it produces the right results. Just press Ctrl-Alt-F1, login, start a text editor you're familiar with, and test it. Press Alt-F7 to return. This will prove that the key is functioning correctly.

---

### Post by kittybrat on 2010-03-03
> **Alexandre Putt said:**
> Well, I'd still check if pressing it produces the right results. Just press Ctrl-Alt-F1, login, start a text editor you're familiar with, and test it. Press Alt-F7 to return. This will prove that the key is functioning correctly.

Okay, did as you suggested - it doesn't seem to work.

---

### Post by Alexandre Putt on 2010-03-03
> **kittybrat said:**
> Okay, did as you suggested - it doesn't seem to work.

Aha! So it may be the keyboard. But you may also want to check whether the 'home' key generates the right scan code. 

I can't remember the right utility for that, but the closest I can find with apropos on my computer is [FONT="Courier New"]testkeys[/FONT] from one of SDL packages.

The scan code it reports for 'home' is 0x6e 0x0. 

Perhaps you should try it out and see if you get the same. If yes, then this has to be a problem with key mapping. If not, it's the keyboard.

---

### Post by kittybrat on 2010-03-06
> **Alexandre Putt said:**
> Aha! So it may be the keyboard. But you may also want to check whether the 'home' key generates the right scan code. 

I can't remember the right utility for that, but the closest I can find with apropos on my computer is [FONT="Courier New"]testkeys[/FONT] from one of SDL packages.

The scan code it reports for 'home' is 0x6e 0x0. 

Perhaps you should try it out and see if you get the same. If yes, then this has to be a problem with key mapping. If not, it's the keyboard.

I'm sorry, I'm not really sure what you're talking about with the SDL packages.  :-\  I've been using Ubuntu for a year now, but I'm still quite fuzzy with the things I don't use often. :-\

---

### Post by Alexandre Putt on 2010-03-07
> **kittybrat said:**
> I'm sorry, I'm not really sure what you're talking about with the SDL packages.  :-\  I've been using Ubuntu for a year now, but I'm still quite fuzzy with the things I don't use often. :-\

Just open the terminal and enter [FONT="Courier New"]testkeys[/FONT]. If the command is not found, you will be told the name of the package which contains it. Then all you need is to install this package by typing its name in Synaptic or the usual command line apt-get stuff.

If you still have a trouble, just post again, I'll explain in more detail.

---

### Post by kittybrat on 2010-03-07
> **Alexandre Putt said:**
> Just open the terminal and enter [FONT="Courier New"]testkeys[/FONT]. If the command is not found, you will be told the name of the package which contains it. Then all you need is to install this package by typing its name in Synaptic or the usual command line apt-get stuff.

If you still have a trouble, just post again, I'll explain in more detail.

Thanks for the instruction.

This is what I got when I hit the home key with testkeys:
> ITEM_ID_XY SDLK_UNKNOWN 0xdf 0x0  
ITEM_ID_XY SDLK_UNKNOWN 0xdf 0x0

---

### Post by Alexandre Putt on 2010-03-07
> **kittybrat said:**
> Thanks for the instruction.

This is what I got when I hit the home key with testkeys:

This looks like the keyboard is physically not working right. I cannot guarantee that, though, but this is the most probable conclusion one can arrive at.

---

### Post by kittybrat on 2010-03-07
> **Alexandre Putt said:**
> This looks like the keyboard is physically not working right. I cannot guarantee that, though, but this is the most probable conclusion one can arrive at.

Do you know why it would work before my clean install, but not after?

---

### Post by Alexandre Putt on 2010-03-07
Are you sure it worked before? If you use an IBM keyboard, I think it may not be very new. It is not uncommon with old keyboards for one or two keys to stop working. The only thing that puzzles me is why you actually get a scan code at all when you press this button.

There are two ways to finally verify the problem: either borrow a keyboard for a day from someone, or boot from a CD / floppy with a different system and see how the key works. (e.g. freedos or Ubuntu CD will do).

---

### Post by kittybrat on 2010-03-07
> **Alexandre Putt said:**
> Are you sure it worked before? If you use an IBM keyboard, I think it may not be very new. It is not uncommon with old keyboards for one or two keys to stop working. The only thing that puzzles me is why you actually get a scan code at all when you press this button.

There are two ways to finally verify the problem: either borrow a keyboard for a day from someone, or boot from a CD / floppy with a different system and see how the key works. (e.g. freedos or Ubuntu CD will do).

I am positive it worked before - I use the home key quite a lot... which is why it's hindering me now. D:  (I'm the type that doesn't like to use a mouse more than I have to.)

Thanks for the help.  If I ever find a solution, I'll report back. :)

---

### Post by senorian on 2010-04-23
i
A couple of days ago the home/end keys, the page up and down keys, the arrow up and down keys all stopped or became erratic
I thought that it was my old keyboard, so I bought a new one--same problems 
.
So I loaded DSL as a live cd and now all keys work

(Iam typing this on the live cd)
One of the recent Ubuntu 9.10 updates may have borked something).
I hope they fix it soon

---

