---
title: "Bizarre keyboard behavior with Control key"
date: 2010-08-02
forum: General Help
---

### Post by aysiu on 2010-08-02
I'm trying to set up a dual-boot on a friend's Dell e1405. It seems to work perfectly... except for one really weird thing. I just don't get it at all. Control-C, Control-V, and Control-X do not work in any application.

Here are the odd things about it: [list][*]Cut, copy, and paste all work if you select them from the menu with the mouse.[*]The Control key definitely works, as I can use Control-A to select all, and Control-Alt-arrow key to switch desktops.[*]I did a little Google searching. Someone mentioned it might be Compiz, but I tried turning off Compiz, and the same behavior was present with vanilla Metacity.[*]I tried changing the keyboard layout to a bunch of other things. Same behavior.[/list] I'm kind of baffled here.

Two questions:

1. Has anyone else experienced this?
2. Any ideas for how to fix it?

---

### Post by Smart Viking on 2010-08-02
Well if you have not, you might look if there is some keyboard shortcut that overwrites the functionality, but i guess you have checked that already and it would be very weird if there was any, just a thought. :)

---

### Post by aysiu on 2010-08-02
> **Smart Viking said:**
> Well if you have not, you might look if there is some keyboard shortcut that overwrites the functionality, but i guess you have checked that already and it would be very weird if there was any, just a thought. :) I actually haven't checked that. That's a good suggestion. My gut is saying that isn't the case, since it's an otherwise stock Ubuntu installation... I'm pretty sure Control-X, Control-C, and Control-V are cut, copy, and paste, respectively, but I'll be sure to just double-check anyway.

Good idea.

Any others to try?

---

### Post by Telengard C64 on 2010-08-02
Most keyboards have two control keys, and they can be read separately. Did you try both?

Just a shot in the dark. This really is puzzling.

---

### Post by Raymond2201 on 2010-08-02
another random shot in the dark, Ubuntu maybe did not pick out the correct location of the CTRL key:

you can check this in Keyboard Preferences> Layout >options

expland "Ctrl Key Position".


hope it helps

Forget that i guess as the Ctrl Key does work with other options :)

---

### Post by aysiu on 2010-08-02
> **Telengard C64 said:**
> Most keyboards have two control keys, and they can be read separately. Did you try both?

Just a shot in the dark. This really is puzzling. Yeah, that behavior's rather odd as well.

The left control key combined with X, Y, aod C doesn't work at all. So if I have text highlighted and press left-Control and C, the text will stay highlighted, but nothing will copy to the clipboard. But the right control key will be almost invisible with X, Y, and C, so if I have text highlighted and press right-Control and C, it'll erase the highlighted text and replace it with a *c*

---

### Post by Telengard C64 on 2010-08-02
Can you use Ctrl+c (either left or right) to cancel a command in the terminal?

I'm just wondering because it seems like you've only tried to use it for copy.

---

### Post by aysiu on 2010-08-02
> **Telengard C64 said:**
> Can you use Ctrl+c (either left or right) to cancel a command in the terminal?

I'm just wondering because it seems like you've only tried to use it for copy.
I haven't tried it to cancel a command, but I did try Control-X to save a text document in Nano, and that didn't work. I'll try it to cancel a command.

---

### Post by Telengard C64 on 2010-08-03
> **aysiu said:**
> I haven't tried it to cancel a command, but I did try Control-X to save a text document in Nano, and that didn't work. I'll try it to cancel a command.

Let us know whether or not Ctrl+c can be used to cancel a command in terminal.

After that, I'm curious to know whether Ctrl+c will work in the TTYs. You should be able to get to a TTY by Ctrl+Alt+F*n* (where *n* is a digit 1 through 6), but since the Ctrl key seems unreliable that may not work. As an alternate way into the TTY you can reboot and login with "text only" or "console only" mode (or whatever it is called) so that no desktop will be loaded.

I'm just wondering exactly how deep in the system this problem extends. If the control key combinations (ie Ctrl+c) work as expected in the TTY then I think we need to look into the desktop environment for the cause.

---

### Post by Irony on 2010-08-03
Does Control+C work in windows? (You mentioned dual boot)

---

### Post by aysiu on 2010-08-03
Thanks to all for the suggestions. I'm still really confused here.

So, first of all, if I go into the Keyboard settings and add Caps Lock as an additional Control key, then I can use Caps Lock to copy and paste... but not cut. It also can cancel commands from the terminal... but not from TTY.

I'm also having trouble booting into Windows, which is a problem, because at the Grub menu, the arrow keys and Enter key don't work either (they work fine during the Gnome session). Maybe there's something weird in the BIOS settings?

---

### Post by aysiu on 2010-08-03
> **Irony said:**
> Does Control+C work in windows? (You mentioned dual boot)
Okay, I was finally able to boot into Windows (it was a BIOS setting... something about having the Scroll lock on by default in POST... why?)

And the problem occurs in Windows, too. So... broken keyboard? I guess the real way to tell would be to use a USB keyboard (which I don't have handy right now).

---

### Post by Telengard C64 on 2010-08-03
> **aysiu said:**
> something about having the Scroll lock on by default in POST... why?)

It depends on the BIOS manufacturer, but in general having such a setting is preferable to not having. I think it may have been more important to MS-DOS than Windows though, since Windows can bypass the BIOS completely and setup the hardware any way it likes.

> And the problem occurs in Windows, too

That tells us a great deal. This is either broken hardware or broken BIOS.

If you want to do further testing then I suggest using a live CD to test the hardware for basic functionality and compatibility. By doing so you will eliminate the possibility that the version of grub on the hard disk is doing something weird.

So test with the Ubuntu live CD, but also test with the FreeDOS live CD if you like. (Nothing special about FreeDOS, but it isn't Linux and it isn't Windows.)

---

### Post by aysiu on 2010-08-03
I don't think I'm going to try FreeDOS right now, but I did run the live CD and it was the same problem, so I think it might be a hardware issue or something (Windows, Ubuntu installed, Ubuntu live CD).

I also updated the BIOS, but the problem persisted.

---

### Post by Telengard C64 on 2010-08-03
Try a different keyboard if possible.

---

### Post by aysiu on 2010-08-03
> **Telengard C64 said:**
> Try a different keyboard if possible.
Yeah, that'd be good to test, but it's not very practical, as this is a built-in laptop keyboard.

---

### Post by Telengard C64 on 2010-08-03
> **aysiu said:**
> this is a built-in laptop keyboard.

I wonder what might happen if you plug in a USB keyboard?

---

