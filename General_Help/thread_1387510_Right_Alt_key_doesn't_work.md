---
title: "Right Alt key doesn't work"
date: 2010-01-21
forum: General Help
---

### Post by Th3Professor on 2010-01-21
[LEFT][FONT=Verdana]I run "xev" and left alt reads "Alt_L" while right alt reads "ISO_Level3_Shift".[/FONT]

[FONT=Verdana]I tried googling it and found this:[/FONT]

[FONT=Verdana]> The culprit is as VF said: in /etc/X11/xorg.conf the option ' Option[/FONT]> 
[FONT=Verdana]"XkbOptions" "lv3:ralt_switch" ' is written, and it should not be.

Workaround:
Edit that file with sudo privileges and put a '#' in front of the line ' Option 
"XkbOptions" "lv3:ralt_switch" '
Save open documents and restart X (Ctrl+Alt+Backspace)[/FONT][FONT=Verdana][FONT=Verdana]

[/FONT][/FONT][FONT=Verdana]That didn't fix it.

I have a fresh install of Ubuntu Studio 9.10.

I also tried setting Keyboard Preferences, "Keyboard Layout Options", "Alt/Win key behavior", to "Alt and Meta are on Alt keys"... but that didn't work. So I put it back how it was.

There is, however, this interesting thing in the keyboard layout options window:

"Key to choose 3rd level" > "Right Alt" (is check-marked/enabled)

What the hell is "3rd level"? lol Anyway, I tried disabling it and it *automatically re-enabled*! (When I re-opened that window it was checked again).

So how do I get right-alt key to work?

And what the heck is the reason for it not working anyway? :-p

I want my "Alt_R" back! ;)

Thanks!

EDIT-
Okay I set keyboard layout options to "right alt never uses 3rd level". My right-alt works now.
But what the heck is "3rd level"? At the moment it's not enabled. What purpose would anybody have for some "3rd level" function (whatever it is)?
[/FONT][/LEFT]

---

### Post by Th3Professor on 2010-01-23
[LEFT][FONT=Verdana]I run "xev" and left alt reads "Alt_L" while right alt reads "ISO_Level3_Shift".[/FONT]

[FONT=Verdana]I tried googling it and found this:[/FONT]

[FONT=Verdana]> The culprit is as VF said: in /etc/X11/xorg.conf the option ' Option[/FONT]> 
[FONT=Verdana]"XkbOptions" "lv3:ralt_switch" ' is written, and it should not be.

Workaround:
Edit that file with sudo privileges and put a '#' in front of the line ' Option 
"XkbOptions" "lv3:ralt_switch" '
Save open documents and restart X (Ctrl+Alt+Backspace)[/FONT][FONT=Verdana][FONT=Verdana]

[/FONT][/FONT][FONT=Verdana]That didn't fix it.

I have a fresh install of Ubuntu Studio 9.10.

I also tried setting Keyboard Preferences, "Keyboard Layout Options", "Alt/Win key behavior", to "Alt and Meta are on Alt keys"... but that didn't work. So I put it back how it was.

There is, however, this interesting thing in the keyboard layout options window:

"Key to choose 3rd level" > "Right Alt" (is check-marked/enabled)

What the hell is "3rd level"? lol Anyway, I tried disabling it and it *automatically re-enabled*! (When I re-opened that window it was checked again).

So how do I get right-alt key to work?

And what the heck is the reason for it not working anyway? :-p

I want my "Alt_R" back! ;)

Thanks!

EDIT-
Okay I set keyboard layout options to "right alt never uses 3rd level". My right-alt works now.
But what the heck is "3rd level"? At the moment it's not enabled. What purpose would anybody have for some "3rd level" function (whatever it is)?
[/FONT][/LEFT]

---

### Post by Th3Professor on 2010-01-24
[FONT=Verdana]what the heck is "3rd level"?

At the moment it's not enabled.

What purpose would anybody have for some "3rd level" function (whatever it is)?[/FONT]

---

### Post by Th3Professor on 2010-01-24
bump!

Is there a reason 'level 3' or '3rd level' should be re-enabled?

---

### Post by tgalati4 on 2010-01-24
I have an ibm thinkpad t43p.  It's missing the "windows" key, also known as the Super key or meta key.  I added some .Xmodmap commands to change my right_alt key to mimic the Super key.  (I was trying to get Gnome-Do to work, and it needs the Super key.)

Under xev it shows it as ISO_Level3_Shift.  Gnome-Do still doesn't come up with Super--Spacebar, so I still have some work to do.

I don't know what Level3 is, but it looks like you chose a keyboard layout without a "windows" key and it is making the substitution for you.  Try changing the keyboard layout and reboot X or logout and log back in to see if that fixes it.

So basically, I have the opposite problem as you.  I have a working Alt_Right and I want to change it to a functioning Level3 key.

---

### Post by Th3Professor on 2010-01-24
> **tgalati4 said:**
> I have an ibm thinkpad t43p.  It's missing the "windows" key, also known as the Super key or meta key.  I added some .Xmodmap commands to change my right_alt key to mimic the Super key.  (I was trying to get Gnome-Do to work, and it needs the Super key.)

Under xev it shows it as ISO_Level3_Shift.  Gnome-Do still doesn't come up with Super--Spacebar, so I still have some work to do.

I don't know what Level3 is, but it looks like you chose a keyboard layout without a "windows" key and it is making the substitution for you.  Try changing the keyboard layout and reboot X or logout and log back in to see if that fixes it.

So basically, I have the opposite problem as you.  I have a working Alt_Right and I want to change it to a functioning Level3 key.

I went with the default/automatic keyboard selection process at install (running 9.10).

I have a [Razer Lycosa]("http://reviews.cnet.com/keyboards/razer-lycosa/4505-3134_7-32640959.html") keyboard. Any ideas on which keyboard layout I should use in Linux/Ubuntu Studio 9.10 for that keyboard?

---

### Post by tgalati4 on 2010-01-24
Look in the keyboard settings dialog box.  There are several to choose from.  Try looking for the Razor brand, or just pick a few generic ones.

Otherwise, add a few commands to .Xmodmap to remap the key.  Search the forums for xmodmap.

---

### Post by Th3Professor on 2010-01-25
No razer or lycosa listings in the keyboard lists for keyboard settings/layouts/etc.

I googled razer lycosa xmodmap and ...the closest thing that came up in google search was *this* thread. LOL! Google's really updating their search bot things fast these days!

Anyway, I'm using a generic layout now I think. I don't know why the right-alt wasn't working. It is now but that "3rd level" stuff is totally alien to me.

---

### Post by tgalati4 on 2010-01-25
If you spend some time learning the xmodmap bindings, you can program all of your extra.keys.  Then publish your key bindings here.  At least google will find it.

---

### Post by viranaso on 2010-06-21
The purpose of a third-level chooser key is to provide another key which acts like a Shift key to give further options. For example, some of us type a lot in Esperanto so we can use the third level key to give accented letters, for instance: g G &#285; &#284; using G, Shift G, RightAlt G and RightAlt Shift G respectively. The keyboard layout system gives each user the option of which key to use for the third level, and fourth level with the Shift key. I use the LeftWin key rather than RightAlt, which may be more commonly used for this purpose.

If you don't need a third-level chooser key then deselect it/them using the keyboard layout manager.

See also: [http://ubuntuforums.org/showthread.php?t=914137](http://ubuntuforums.org/showthread.php?t=914137)

---

### Post by mbaum on 2010-10-28
Hey,
i had the same problem and foud a solution:

use xev in your bash to find out which keycode your right alt-key has. You do this, by simply running xev without any parameter, hit your right alt-key and close xev by clicking on the "x" in the window that appears.

> xev

then you can see some output in the bash, with information on the keys you pressed. the interesting section (in my case) is the following:

> KeyPress event, serial 36, synthetic NO, window 0x4400001,
    root 0x13c, subw 0x0, time 2066740, (1416,785), root:(1421,835),
    state 0x0, keycode 108 (keysym 0xff20, Multi_key), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: True

In particular:

> keycode 108 (keysym 0xff20, Multi_key)

which is saying that the right alt-key has keycode 108 and is mapped to "Multi_key" (which i dont know, what it is).

doing the same with my left alt-key, i found out, that it is mapped to ISO_Level3_Shift .

you can change the mapping by the following execution of xmodmap:

> xmodmap -e "keycode 108 = ISO_Level3_Shift"

it may be possible, that your alt-key has a different keycode, thats why i explained the process of finding out, what your keycode is.

good luck,
Manuel

PS:
i later found this post, with a solution that might also work, but i didnt test it:
[http://ubuntuforums.org/showthread.php?t=383454](http://ubuntuforums.org/showthread.php?t=383454)

---

