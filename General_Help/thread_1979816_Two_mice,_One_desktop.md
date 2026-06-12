---
title: "Two mice, One desktop"
date: 2012-05-14
forum: General Help
---

### Post by myromance123 on 2012-05-14
Hi there.
I have two mice, a Razer Abyssus and a Razer DeathAdder.
The configuration I would like to setup is that the Abyssus would be on the left for my left hand. The DeathAdder would be the one on the right for my right hand.

I use the DeathAdder for gaming, but when my right arm starts to feel sore I would instead use the Abyssus with my left hand.

My question is, would it be possible to have the mouse on the left in a left-handed mode while the mouse on the right would be in a right-handed mode? Simultaneously both operating, but only 1 cursor.
I don't need any extra cursors, the one is fine. It would just be handy that when I need to rest my right arm I can instead use my left hand on the left mouse without having to always go into settings and change it to left or right handed.

I use Ubuntu 12.04.
Apologies in advance, if this is not the correct section to post in. I am unsure if this should have gone into Gaming and Leisure or Hardware and Laptops, since this is more to configuration than a hardware issue.

Also thanks in advance for ANY tips/info or help you can provide me with :guitar:

---

### Post by myromance123 on 2012-05-14
I am guessing this is not possible then?

---

### Post by Vaphell on 2012-05-15
maybe create keyboard shortcuts for
```
gsettings set org.gnome.settings-daemon.peripherals.mouse left-handed true
gsettings set org.gnome.settings-daemon.peripherals.mouse left-handed false
```

or wrap them in a script that detects the current value of the setting and switches to the opposite (toggle on/off)

```
#!/bin/bash

current=$( gsettings get org.gnome.settings-daemon.peripherals.mouse left-handed )
if [ $current = true ]
then
  new=false
else
  new=true
fi
gsettings set org.gnome.settings-daemon.peripherals.mouse left-handed $new

```

i think it should be possible to detect which mouse is moving based on system /dev/input/mouse pseudofile and set the proper value based on that but it's tricky and i haven't figured it out.

---

### Post by bodhi.zazen on 2012-05-15
See 

[https://wiki.archlinux.org/index.php/Multi-pointer_X](https://wiki.archlinux.org/index.php/Multi-pointer_X)

[https://wiki.ubuntu.com/X/MPX](https://wiki.ubuntu.com/X/MPX)

---

### Post by myromance123 on 2012-05-15
@Vaphell
Thank you for the help, but I am unfamiliar with making scripts unless given step-by-step instructions. Still can't wrap my head around scripts.

@bodhi.zazen
Thank you as well. Before I do go and follow that information to make changes, I want to be clear that my intention is to have a SINGLE cursor not multiple cursors. This is because I read elsewhere that focus becomes an issue when you have multiple cursors, and since I game that can become an issue.

I read the article, it seems to be able to give each cursor a focus of its own. Does this mean that if I start a game using the right hand mouse, it should and would only detect that mouse during gameplay? Or is this beyond possibility?

I also read this at the bottom of the article:
> As of 26 September 2010, none of major window managers support multi-pointer.  :confused:

---

### Post by bodhi.zazen on 2012-05-15
You probably can not do what you are wanting. Also "none of major window managers support multi-pointer." - what are the "mafor window managers" ? You might need to use openbox / fluxbox / icewm and start working your way through config files.

---

### Post by myromance123 on 2012-05-15
Thats a shame... Anyhow, thanks for the help.
If there is ever a way to do this, and anyone reading this knows how please do PM me with the information in the future.

Thanks again.

---

### Post by Vaphell on 2012-05-15
my advice - learn to use the mouse in 'normal mode' with left hand :)

My situation is somewhat similar to yours, from time to time i use my offhand if i feel like leaning but the difference is I am very lefthanded and I never bothered with switching buttons around. The world is righthand biased and fighting that never made much sense, I'd have to fiddle with settings every time when using a computer other than my own. Index and middle fingers are of similar strength and precision so it's not that hard to master reverse mode.

---

### Post by thisisnotaname on 2012-08-29
Stumbled on this thread since I was trying to do the same thing. Here's how to do it:

1. Open a terminal (Ctrl+Alt+T or type "terminal" in the dash)

2. Enter: **xinput** (xinput is a tool for viewing and editing settings of input devices)

3. You will see a list of input devices and their IDs. Remember the id of the mouse whose settings you want to change. It should be a one- or low two-digit number. My second mouse has the ID 13.

4. Enter: **xinput list-props 13** (replace 13 with the ID of your second mouse)

5. This will list several properties of your mouse. The one you're interested in is "Button Labels", which looks like this on my computer:
> "Button Left" (135), "Button Middle" (136), "Button Right" (137), "Button Wheel Up" (138), "Button Wheel Down" (139), "Button Horiz Wheel Left" (140), "Button Horiz Wheel Right" (141), "Button Side" (256), "Button Extra" (257)


The important thing is the order of the labels. 1 = left button, 2 = middle button, 3 = right button.

6. Enter: **xinput get-button-map 13** (this will print a numeric list of all buttons of input device 13 and should look like this: 1 2 3 4 5 ...)

7. Copy the numeric list.

8. Type: **xinput set-button-map 13 **, then paste the list. Now, assuming that button 1 is the left button and button 3 is the right button, switch 1 and 3 in the list so the command looks like this and press enter: **xinput set-button-map 13 3 2 1 4 5 6 7 8 9**

9. Changes are effective immediately, but only active for the current session.

10. To make the changes permanent, create a text file, and paste the command, so it looks like this:

> xinput set-button-map 'Logitech USB Trackball' 3 2 1 4 5 6 7 8 9
xinput set-ptr-feedback 'Logitech USB Trackball' 3 5 1

I replaced the ID with the device name, but you can use the ID, too. I also changed the acceleration settings (2nd line). Save the file and make it executable (right click  -> properties -> permissions -> tick "allow executing ...").

11. Add the file to your startup applications (Dash -> Startup Applications Preferences -> Add -> Browse...)

12. If you want to change other properties like acceleration, have a look at --set-prop on the [xinput man page](http://www.x.org/archive/X11R7.5/doc/man/man1/xinput.1.html)

---

### Post by MrPGruber on 2012-09-20
thisisnotaname gives an answer that works for a single user computer, but it is at best a _workaround_ for multiple users.

I have my desktop set up so it requires a password after the screensaver is enabled, and I have multiple users who often have simultaneous desktop logins active.  This means frequent uses of lightdm to switch users, or to reactivate the session after the screen saver has run.  

lightdm appears to put the mouse settings back to the default value.  This results in the lefties having to run the script every time they sit at the computer, which is annoying at best.

A _fix_ would allow me to set the computer up with a left mouse and a right mouse regardless of what is going on with the x-server.  It doesn't need GUI support, there just needs to be a non-volatile method.

Any takers?

---

