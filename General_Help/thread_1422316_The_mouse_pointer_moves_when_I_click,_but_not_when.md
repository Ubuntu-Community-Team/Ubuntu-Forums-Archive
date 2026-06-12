---
title: "The mouse pointer moves when I click, but not when I circle with it"
date: 2010-03-05
forum: General Help
---

### Post by suntom on 2010-03-05
Ok, funny title - got your attention? Good.

Now, this might be a little hard to explain, because I had a hard time Google it and find someone with a similar problem (I found none).

**The problem**: Whenever I'm running a game, like Nexuiz for example, and whenever I click, no matter where, the mouse pointer jumps from the top left to the bottom right.

I noticed it only jumps one time if I don't release the mouse button, but when I release it, it jumps again - so it always jumps two times.

**BUT!** If I circle with the mouse a little bit, like quickly, and then click on the mouse button - it's working and it ain't moving by itself.

*Sounds weird, huh?*

But I manged to get into Nexuiz to test if it was only at the menus, but no - whenever I try to fire my weapon it's like my character has a panic attack because of a bee or something, and he's like trying to shoot it (by looking in funny directions).

Short story, I end up shooting behind me instead of the target that **was** in front of me (but is now behind be, because I've turned, or the mouse did).

*Still with me? Good.*

So, this problem of mine don't happens when I'm at my desktop nor Firefox, like literally nowhere except for when I'm going to play a game.

It kinda seems that it happens when I get into an application that requires a lot of my graphic card, but I don't know.

**What I've tried to fix my problem**:

[LIST]
[*]Deactivate Compiz
[*]Remove Compiz completely
[*]Update my graphic drivers
[*]Install all updates for Ubuntu
[*]Use different mouse (all USB)
[*]Use a different USB-port
[*]Yelling at the screen
[/LIST]
Nothing worked, and I'm starting to get kinda frustrated.

**My information**:

[LIST]
[*]Desktop computer
[*]Ubuntu 9.10 (gnome)
[*]Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz 64-bit
[*]ATI Radeon HD 4670
[/LIST]
Guess thats the details needed, ask me for any others if I've missed anything.

Now, I have no clue of what to do - I've tried searching for an solution, and I really don't want to just give up on it and install the system all over again.

Suggestions?

---

### Post by mechro on 2010-03-05
Have you got an /etc/X11/xorg.conf file? If so, what does it have for InputDevice/mouse?

---

### Post by suntom on 2010-03-05
> Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection
This is how my xorg.conf file looks like.

---

### Post by suntom on 2010-03-05
I've tried to enter the following into my xorg.conf file, but it did not give me any results.
> Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

---

### Post by mechro on 2010-03-05
OK, nothing in there that would help.

You may be stuffed because of the ATI card :-|

Two suggestions...

If you have a PS2 socket on your computer get yourself a USB/PS2 adapter and plug the mouse in the PS2 socket.

I understand Nexuiz has two commands to launch it (glx or sdl?). Does this help...

[http://www.ubuntumagazine.net/?p=1984](http://www.ubuntumagazine.net/?p=1984)

---

### Post by suntom on 2010-03-05
Now thats a quest - to get a PS2-adapter.

Will get back here with my results when, and if, I find one.

---

### Post by AndrooUK on 2010-03-07
Maybe your mouse itself is malfunctioning.

I just tried swapping my mouse to an old one, because the cursor was moving by itself until I moved the mouse quickly from side to side. Now it works fine.

---

### Post by huangweiqiu on 2010-03-07
virus? you know, this is one classical symbol of virus in windows world, linux world also has virus

---

### Post by suntom on 2010-03-07
Well, I've tried other USB-mices (lol?), but the same thing happen, even when I connected them to the PS2-port with an adapter.

**But!**

Now the funny thing, I found my old Logitech mouse and gave it a try in the USB port - now everything is working smooth.

So, I didn't get the same results with my Logitech mouse as I did with the others (non Logitechs) which is kind of strange, or just a coincidence. 

And I totaly don't think it's any sort of virus, so the conclusion is that either all of the ones I testet was malfunctioning and not the good ol' Logitech.

---

