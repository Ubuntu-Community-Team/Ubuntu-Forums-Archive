---
title: "Assign a european letter to keyboard in Ubuntu?"
date: 2010-08-03
forum: General Help
---

### Post by algomedic on 2010-08-03
Hi,

Fairly new to Ubuntu and this may be a stupid question, but is it possible to assign a key on the keyboard to make a specific letter - eg. Ü?

Thanks

---

### Post by Yuri sss on 2010-08-03
> **algomedic said:**
> Fairly new to Ubuntu and this may be a stupid question, but is it possible to assign a key on the keyboard to make a specific letter - eg. Ü?
The most simple way would be to add the German keyboard layout, switch to it and then press the key that produces the Ü (the key just right of the P).
If you don't know where a key is located on the keyboard layout, you can use the on-screen keyboard **Kvkbd**. If you don't have it, you can install it with:
```
sudo apt-get install kvkbd
```

Another solution would be to create an xkbd configuration file which handles custom keyboard mappings, but that requires a certain expertise and isn't beginner-friendly at all.

---

### Post by David Andersson on 2010-08-03
You can use xmodmap. If you for example want Ü on AltGr + U first check what keycode U has, and the general layout of keycode settings:

```
xmodmap -pke
```

```
xmodmap -pke | grep -wi u
```

If keycode for U is 30, and if there generally are 4 and 8 keysyms for a keycode (like mine is) then define AltGr + U like this, in a terminal:

```
xmodmap -
keycode  30 = u U u U udiaeresis Udiaeresis udiaeresis Udiaeresis
Ctrl-D
```

Now AltGr-u and AltGr-Shift-U should give ü and Ü respectively. If that works, create a file named .Xmodmap in your home directory and add just the keycode line in that file:

```
keycode  30 = u U u U udiaeresis Udiaeresis udiaeresis Udiaeresis
```

(This might or might not apply to the current Ubuntu: If the new key suddenly stop working, you may need to go to the keyboard settings in the preference menu and tell Ubuntu not to be picky about keyboard layout settings. Otherwise it tends to soon restore the layout as set in the graphical tools and forget about the settings in xmodmap.)

Edit: Now I have tested on a real Ubuntu 9.10-system, and I could not make the above work with US Layout. With Swedish layout it works, but you have to have an AltGr key. If the keyboard has no AltGr key I thought shift+alt or shitf+ctrl or ctrl+alt could be used instead, but none of those combinations acts like AltGr for me. There was 6 keysyms instead of 8. So the keysyms could be "u U u U udiaeresis Udiaeresis".

---

### Post by rob_38 on 2010-08-03
asciitable.com

Nice and easy!!!

---

### Post by Zorgoth on 2010-08-03
I have a custom xkb keyboard layout that I use.  You may want to check the relevant language's keyboard layout as it may be identical to the standard one except that the right alt key becomes a third level switch - it it isn't identical, you could just make it so by modifying the configuration file (doing that would be pretty easy).  You can view all layouts with "System > Preferences > Keyboard" and you can find the configuration files in /usr/share/X11/xkb/symbols.  They will have 2 letter names, like 'pl' for Polish.

---

### Post by simosx on 2010-08-04
> **algomedic said:**
> Hi,

Fairly new to Ubuntu and this may be a stupid question, but is it possible to assign a key on the keyboard to make a specific letter - eg. Ü?

Thanks

The typical solution would be to select a keyboard layout that supports typing that letter. For example, for my keyboard layout, I can type ÖÄËÜŸ&#7785; etc. Tell us your keyboard settings to help select a layout for you,

[INDENT]gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/INDENT]

You can also edit your current keyboard layout and replace any existing character with Ü. Again, provide the output of the gconftool-2 command for help.

---

### Post by algomedic on 2010-08-04
layouts = [us]
 options = [grp	grp:alts_toggle]
 model = 


Thanks

---

### Post by simosx on 2010-08-05
> **algomedic said:**
> layouts = [us]
 options = [grp	grp:alts_toggle]
 model = 


You are using the standard US layout.
The layout comes from the file /usr/share/X11/xkb/symbols/us.
You can edit the file with
[INDENT]
gksudo gedit /usr/share/X11/xkb/symbols/us[/INDENT]

Notice the first section that starts with

[FONT="Courier New"]default
partial alphanumeric_keys modifier_keys
xkb_symbols "basic" {

    name[Group1]= "USA";

    // Alphanumeric section
    key <TLDE> {    [     grave,    asciitilde  ]   };
    key <AE01> {    [     1,    exclam      ]   };
    key <AE02> {    [     2,    at      ]   };
    key <AE03> {    [     3,    numbersign  ]   };
    key <AE04> {    [     4,    dollar      ]   };
.....................
[/FONT]

For example, the 'key <AE01>' line is about the key that produces '1!'.
Ü has Unicode code U00DC (open Character Map in Accessories and find the Unicode codepoint value).
So, if you want to replace '!' with Ü, you can change the line

[FONT="Courier New"]    key <AE01> {    [     1,    exclam      ]   };[/FONT]

with 

[FONT="Courier New"]    key <AE01> {    [     1,    U00DC      ]  };[/FONT]

I notice that you use Alt+Alt to switch layouts using the keyboard. Does this work for you? If not, visit the Keyboard Preferences/Layouts/Layout Options and change the shortcut.

Good luck!:popcorn:

---

### Post by quinnten83 on 2010-08-05
I use keyboard layout US International with dead keys.
Ü = " and then hitting shift u.
that might be the easiest solution for you.
you can change your keyboard layout in System >preferences> keyboard, tab layout.

---

### Post by corncob on 2010-08-05
The way I make Ü is by pressing 'compose key' + U + ".  I set my compose key in System>Preferences>Keyboard>Layout>Options.  If I want a ß (like in 'Grüße'), I type 'compose key" +s+s.   I printed my list out from [http://docs.sun.com/app/docs/doc/806-4743/6jdq6q2n7?a=view](http://docs.sun.com/app/docs/doc/806-4743/6jdq6q2n7?a=view)

---

