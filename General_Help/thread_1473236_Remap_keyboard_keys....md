---
title: "Remap keyboard keys..."
date: 2010-05-05
forum: General Help
---

### Post by dlikhten on 2010-05-05
Hey all,

Just installed a ubuntu netbook remix on my laptop and it is really frustrating developing on it because of the pageup/pagedown/home/end key ****ing up that they did. Anyways, in their infinite wisdom at lenovo, they decided that the most accessible and highly needed keys on the arrow keys using FN modifier would be brightness and volume. So now I am stuck with an FN key next to the control key, and pageup/pagedown above the number keys, AND fn+pageup/fn+pagedown as the Home/End. Basically very annoying given that home/end are greately used by me. All the while the brightness and volume are on the arrow keys which I use frequently.

What I would like to do is remap my Brightness and Volume keys and Pageup/down/home/end keys so that I can do FN+Left = home FN+Right = end FN+Up = pageup FN+Down = pagedown (sort of like Mac mappings).

Is there a tool that allows me to remap keys on a system level so that even gnome thinks I am pressing different keys, thus I get to not have to modify the config on every program??

---

### Post by dlikhten on 2010-05-06
*bump* anyone?

---

### Post by drewsus on 2010-05-06
This looks useful:
[http://forum.compiz.org/viewtopic.php?f=86&t=5290&p=37201](http://forum.compiz.org/viewtopic.php?f=86&t=5290&p=37201)

---

### Post by dlikhten on 2010-05-06
Maybe I am  not understanding. I have tried commands like

xmodmap -e "keymap XF86AudioLowerVolume = Home" but that does not seem to work. How do I discover these keys correctly, and what symbols they are currently mapped to?

Strangely showkey shows home key = 102, end = 107 but the export of xmodmap shows 102 = Muhenkan and 107 = Print... The mappings don't help make 122 and 123 keys work correctly.

showkey does not show what keys the brightness controls are.

I was thinking this should work if I get the symbols right

```


keymap 122 = Home --??
keymap 123 = End --??
keymap 102 = XF86AudioLowerVolume
keymap 107 = XF86AudioRaiseVolume
keymap 232 = Page_Down --??
keymap 233 = Page_Up --??
keymap 104 = XF86MonBrightnessUp
keymap 109 = XF86MonBrightnessDown


```

---

### Post by dlikhten on 2010-05-06
I've experimented and the following seems to be true, which makes no sense to me:

```

xmodmap -e "keycode 110 = Home" # sets the home key to home
xmodmap -e "keycode 110 = Delete" # sets the home key to delete
xmodmap -e "keycode 110 = XF86AudioLowerVolume" # sets the home key to something that does not work
xmodmap -e "keycode 122 = Home" # sets the volume down key to something that does not work
xmodmap -e "keycode 122 = Delete" # sets the volume down key to something that does not work 
xmodmap -e "keycode 122 = XF86AudioLowerVolume" # sets the volume down key to volume down

```

Now what is strange is it appears that only certain keys can be mapped to certain commands. Is there somewhere where it is listed which keys are allowed to map to which commands?

I've discovered the following keycodes

110 = Home
115 = End
122 = Vol Down
123 = vol Up

--

112 = Page Up (Prior)
117 = Page Down (Next)
232 = Brightness Down (might be wrong) -- can't seem to get these to get modified at all
233 = Brightness Up (might be wrong) -- can't seem to get these to get modified at all

---

### Post by dlikhten on 2010-05-07
Anyone knows of a simpler way to do it? Perhaps change my keyboard layout to just do it at a keyboard driver level?

---

### Post by mike555 on 2010-05-07
you could install " xkeycaps" , it will let you change keys (like capslock to l.shift)

---

### Post by dlikhten on 2010-05-07
> **mike555 said:**
> you could install " xkeycaps" , it will let you change keys (like capslock to l.shift)

Does it let me remap all keys? I will give it a shot neways.

How do I determine what keyboard layout I have? It is definately not PC / 105 key / xfree86 us layout, because arrows and such are not correct.

Does not even recognize the buttons correctly for arrows, nor does it even detect: Right arror, volume (up/down), brightness (up/down)

---

### Post by dlikhten on 2010-05-11
anyone?

---

### Post by Matt G Dalian on 2010-05-24
I also would like to do this:

I have a Samsung NC10 Netbook. It's fantastic, except for the lack of Home and End keys, which I use very frequently (but I think most netbook keyboards have this problem).

Right now, the Home and End keys can only be accessed by pressing the blue "Fn" button.
(The keys default to PgUp and PgDown).

I would just like to switch this:
The keys default to Home and End, and when I press Fn I can acccess PgUp and PgDown.

Any ideas on how to do this?

I've attached an image of that part of my netbook keyboard.

---

### Post by dlikhten on 2010-05-29
I have to say, I have another computer with the same layout, honestly it would be much better than my current layout.

Still would love some help with this topic.

---

