---
title: "Insane scrolling"
date: 2009-11-07
forum: General Help
---

### Post by dyltman on 2009-11-07
How can I change the scroll speed? Because at the moment it scrolls insanly quick.

Thanks
edit: I use ubuntu 9.10

---

### Post by dyltman on 2009-11-20
Please anyone?

Sometimes the scrolling works fine but if I go over to my windows 7 and then back to ubuntu again it becomes like this.

---

### Post by P4man on 2009-11-20
can you give some more info? Is this a mouse or touchpad ? What type? Is this only in firefox or in all apps?

---

### Post by dyltman on 2009-11-20
> **P4man said:**
> can you give some more info? Is this a mouse or touchpad ? What type? Is this only in firefox or in all apps?

it's a mouse, Arc™ Mouse Special Edition from Microsoft. This happens for all apps and in firefox

---

### Post by Giblet5 on 2009-11-20
System -> Preferences -> Mouse

Will help you get the pointer speed comfortable.

Firefox -> Edit -> Preferences -> Advanced -> General tab

Set your scrolling options to a comfortable value.

Firefox (enter "about:config" in the address bar) Hit ^F and enter "toolkit.scrollbox.scrollIncrement" set that to a reasonable value, like "20".

---

### Post by dyltman on 2009-11-20
> **Giblet5 said:**
> System -> Preferences -> Mouse

Will help you get the pointer speed comfortable.

Firefox -> Edit -> Preferences -> Advanced -> General tab

Set your scrolling options to a comfortable value.

Firefox (enter "about:config" in the address bar) Hit ^F and enter "toolkit.scrollbox.scrollIncrement" set that to a reasonable value, like "20".

First thing wont let me set the scrolling and firefox is already set on toolkit.scrollbox.scrollIncrement to 20.

the wierd thing is that the scrolling is good sometimes and then when I go over to windows 7 (I'm dualbooting) and then go back again to ubuntu it will scroll about 1/3 of the page when scrolling gently.

---

### Post by P4man on 2009-11-20
you can also edit your /etc/X11/xorg.conf file and add this line:

```
Option "VertScrollDelta" "3"
```

in the  Section "InputDevice"

Change the 6 to whatever you want, its the number of line being scrolled at a time.

---

### Post by dyltman on 2009-11-20
> **P4man said:**
> you can also edit your /etc/X11/xorg.conf file and add this line:

```
Option "VertScrollDelta" "3"
```

in the  Section "InputDevice"

Change the 6 to whatever you want, its the number of line being scrolled at a time.

Section "InputDevice" didn't exist so I added the following

Section "InputDevice"
	Option "VertScrollDelta" "3"
EndSection

at the end but nothing happened

---

### Post by Giblet5 on 2009-11-20
Make that entry look like:

```
Section "InputDevice"
    Identifier     "Arc"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
  # Option         "Emulate3Buttons" "true"
    Option         "VertScrollDelta" "3"
EndSection
```

Uncomment the Emulate3Buttons if you want left+right = middle behavior.


Save it and restart xorg via ```
sudo /etc/init.d/gdm restart
```

---

### Post by P4man on 2009-11-20
3 is the default setting I think. Try 1 or 10 to see if it has any effect at all.

---

### Post by P4man on 2009-11-20
Giblet, my xorg section looks like this:
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         **"Protocol" "auto"**
    Option         "Device" "**/dev/psaux**"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

No idea if either would work or what the difference is...

---

### Post by Giblet5 on 2009-11-20
I grabbed it from a Redhat forum discussion about the Arc mouse with scrolling issues.

I don't have an Arc, but my pal Google knows people who do.

You could be right (probably are).

---

### Post by P4man on 2009-11-20
nah, mine is for a very different mouse, good call googling on Arc, I just wondered. but I checked and there is a /dev/input/mice in ubuntu so Im sure your xorg will work.

Anyway if this fails, the OP should contact microsoft and ask were to download linux drivers :p

---

