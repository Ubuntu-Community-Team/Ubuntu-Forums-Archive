---
title: "web page scrolling with wheel"
date: 2009-07-01
forum: General Help
---

### Post by de049 on 2009-07-01
Hi,

How can i set my mouse scroll wheel to do just that when surfing a Firefox page?

At the moment, if i use my mouse scroll wheel, i get to either my previous or next pages in my browsing history - that sucks!

How can i change this behaviour?

My Ubuntu is 9.04

thanks!

de049

---

### Post by Aearenda on 2009-07-01
The default behaviour in 9.04 is what you are seeking. Are you sure your shift key is not stuck?

---

### Post by de049 on 2009-07-01
:-) 110% sure no sticky keys are causing this.  This is an 8.04 which has eventually upgraded to 9.04.

any ideas where i can reset this scroll to do what i need it to?

thanks

---

### Post by CatKiller on 2009-07-01
> **de049 said:**
> any ideas where i can reset this scroll to do what i need it to?

Open up about:config and change the mousewheel.withnokey.action key to 0. More information [here]("http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries#Mousewheel..2A").

---

### Post by Aearenda on 2009-07-01
Looks like CatKiller's link is being mangled by the forum software - it should be ```
http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries#Mousewheel..2A
```You'll have to copy/paste this.

---

### Post by CatKiller on 2009-07-01
Actually, yours isn't either. I don't know where those <b>s are coming from.

EDIT:

> **Aearenda said:**
> You'll have to copy/paste this.

Actually, you can highlight the text and then drag-and-drop to the tab bar to open a URL in a new tab. Quite neat.

---

### Post by de049 on 2009-07-02
ok, so now i'm confused.  Checked the about:config and the entry suggested is already set to 0, and scrolling number of lines is set to 1.

What could this be then?  I must stress that no keyboard key is sticky, this must be some misconfig somewhere.

please help some1.

thanks

---

### Post by Aearenda on 2009-07-02
Let's see what code the mouse is giving to X. Do this:

1. Start a terminal from Applications->Accessories.
2. Type this and press enter: ```
xev | grep button
```
3. Move the mouse over the small window that appeared and then move the wheel up once and down once.
4. Press Alt and F4 to close the small window.
5. Paste the output in the terminal in your reply here. It should look something like this:```
user@computer:~$ xev | grep button
    state 0x0, button 4, same_screen YES
    state 0x800, button 4, same_screen YES
    state 0x0, button 5, same_screen YES
    state 0x1000, button 5, same_screen YES
```

---

### Post by de049 on 2009-07-02
Hi,

here's the output.  Hope it explains it all.....

Note i scrolled up first, then down.  Only one scroll in each case, as you suggested.

    state 0x10, button 4, same_screen YES
    state 0x810, button 4, same_screen YES
    state 0x10, button 8, same_screen YES
    state 0x10, button 9, same_screen YES
    state 0x10, button 5, same_screen YES
    state 0x1010, button 5, same_screen YES
    state 0x10, button 8, same_screen YES
    state 0x10, button 9, same_screen YES

---

### Post by Aearenda on 2009-07-02
Hmmm
0x10 button 4 is Numlock on, up start; 0x810 button 4 is Numlock on, up stop.
I have no idea why your mouse is generating buttons 8 and 9 at this point (unless your mouse has side buttons that you are accidentally pressing).

0x10 button 5 is Numlock on, down start; 0x1010 button 5 is Numlock on, down stop.
Again, button 8 and 9 should not be present at this point.

I have verified that mouse button 8 does indeed go back in history in Firefox, and mouse button 9 goes forwards. This is the cause of your problem.

Do you have another mouse to try, to see if you get the same results?

Also, does your mouse have a tilting wheel, such as some Logitech mice?
And, please show the output of the command ```
xmodmap -pp
```

---

### Post by de049 on 2009-07-02
There are 32 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
        6              6
        7              7
        8              8
        9              9
       10             10
       11             11
       12             12
       13             13
       14             14
       15             15
       16             16
       17             17
       18             18
       19             19
       20             20
       21             21
       22             22
       23             23
       24             24
       25             25
       26             26
       27             27
       28             28
       29             29
       30             30
       31             31
       32             32

My mouse is a Logitech Trackman Wheel mouse, the one with the red trackball.  No tilt wheel on this.

I thought it could have been the scroll lock because i use it to switch PCs on my KVM.  However, it does nothing different when pressing the srcoll lock key.

The mouse must be fine coz i worked on this same PC before with a Windows install, and also works 100% ok with my other  windows PC which is connected to the same KVM.

What you think of the output above, any clues revealed there?

i really appreciate your time!

thanks

---

### Post by Aearenda on 2009-07-02
The xmodmap output just shows a standard system, with no buttons redefined.

You mentioned the magic letters 'KVM'...

Please try the 'xev | grep button' test with the mouse plugged directly into the computer, not through the KVM, just to verify whether the KVM is adding to this.

I think it should be possible to tell Ubuntu to suppress the button 8 and 9 messages, but I'll need to do some research and testing on that.

UPDATE: Please post the mouse section of /etc/X11/xorg.conf, if there is one - something like this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

```


And another edit: It looks like setting physical buttons 8 and 9 to trigger fake buttons 10 and 11 using xmodmap might work. Try this:
```
xmodmap -e "pointer = 1 2 3 4 5 6 7 10 11 8 9"
```
It should take effect immediately. If it works, you could add a script that does this to your startup programs.

---

### Post by de049 on 2009-07-03
wow, u cracked it!!!  That piece of code does the business.

I shall add it as a startup item right away.  I am so grateful for this help.

You've been amazing, really appreciate your time.

de049

---

### Post by Aearenda on 2009-07-03
Glad to hear it! You are welcome.

---

