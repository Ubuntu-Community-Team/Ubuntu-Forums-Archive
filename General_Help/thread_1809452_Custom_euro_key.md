---
title: "Custom euro key"
date: 2011-07-21
forum: General Help
---

### Post by GrandVizier on 2011-07-21
On my keyboard I have a key specifically for €, but it doesn't work in Ubuntu. The key is located next to the up and left arrow keys, and now that I moved to Ireland, it would be real handy to have it available.

I had a peak at /usr/share/X11/xkb/symbols/us
which contains 
```
partial alphanumeric_keys
xkb_symbols "euro" {

    name[Group1]= "USA - With EuroSign on 5";

    include "us(basic)"

    include "eurosign(5)"

    include "level3(ralt_switch)"
};
```

I also looked around at /usr/share/X11/xkb/symbols/eurosign, but I haven't figured out how to make this change. When I go to System->Preferences->Keyboard Shortcuts and make the attempt to assign the € key to an action, it comes up as: "Alt+KP Insert".

So what can I add to the xkb/symbols file to make the € key output the € symbol?

---

### Post by Frogs Hair on 2011-07-21
Language Support  > Regional Formats  allows you to change denominations and date formats used in the region you live .

---

### Post by peter d on 2011-07-21
Alt Gr + 4 works for me.Thus: €

---

### Post by GrandVizier on 2011-07-21
Right, I'm familiar with the Region settings. For now, I'm happy with my currencies and dates as they are.
And currently Alt Gr doesn't seem to be configured differently than Alt.

But the reason I asked the question is because my keyboard has a specific key for €. The key has no other function and right now it doesn't work, thereby making it a waste of space. And since I'm using € symbol more often in my writing, it would be handy to have the key doing what it's suppose to.

---

### Post by enimeizoo on 2011-07-21
I think you didn't pick the right keyboard model (or maybe just layout) in your configuration. Did you try a few ones to see if that makes a difference?

Or you could have a look at xmodmap and xev. Your can remap your keyboard as you wish with those tools. And it is distribution-independent.

Hope it helps!

---

### Post by GrandVizier on 2011-07-27
I think you're on to something with the xmodmap and xev - but I'm not sure I'm understanding the output I'm getting 

when I run xev and click the € key 

I get a KeyPress event for: keycode  64 = Alt_L Meta_L Alt_L Meta_L
then a KeyPress/KeyRelease of: 
keycode  90 = KP_Insert KP_0 KP_Insert KP_0
keycode  87 = KP_End KP_1 KP_End KP_1
keycode  88 = KP_Down KP_2 KP_Down KP_2
keycode  80 = KP_Up KP_8 KP_Up KP_8
before the KeyRelease event of  keycode  64 = Alt_L Meta_L Alt_L Meta_L

all that action happens with a simple press/release of the € key - in comparison with the up arrow, I simply get a KeyPress/KeyRelease of keycode 111 = Up NoSymbol Up

does that make sense? any idea how I configure xmodmap to handle all those events for one action?

---

### Post by enimeizoo on 2011-07-27
> **GrandVizier said:**
> I think you're on to something with the xmodmap and xev - but I'm not sure I'm understanding the output I'm getting 

when I run xev and click the € key 

I get a KeyPress event for: keycode  64 = Alt_L Meta_L Alt_L Meta_L
then a KeyPress/KeyRelease of: 
keycode  90 = KP_Insert KP_0 KP_Insert KP_0
keycode  87 = KP_End KP_1 KP_End KP_1
keycode  88 = KP_Down KP_2 KP_Down KP_2
keycode  80 = KP_Up KP_8 KP_Up KP_8
before the KeyRelease event of  keycode  64 = Alt_L Meta_L Alt_L Meta_L

all that action happens with a simple press/release of the € key - in comparison with the up arrow, I simply get a KeyPress/KeyRelease of keycode 111 = Up NoSymbol Up

does that make sense? any idea how I configure xmodmap to handle all those events for one action?

Well, your euro key is probably a special key, not handled like it should be. So my guess is that it is a kernel/driver/keyboard model issue. 
Can you post the whole xev output for a single press of the euro key, just in case?

Or your key is a macro key. I heard that you can get unicode characters with several key combination involving alt and numeric chars. Something like holding alt, and typing the unicode value. I wouldn't be surprised if the unicode value of the euro symbol is 0128. 

Unfortunatly, I have no knowledge about macro keys. I'm gonna do a little bit of search, but I don't promise anything.

---

### Post by GrandVizier on 2011-07-28
xev output for € key

```
KeyPress event, serial 36, synthetic NO, window 0x6000001,
    root 0xae, subw 0x6000002, time 195460324, (41,36), root:(42,93),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x6000001,
    root 0xae, subw 0x6000002, time 195460329, (41,36), root:(42,93),
    state 0x8, keycode 90 (keysym 0xff9e, KP_Insert), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6000001,
    root 0xae, subw 0x6000002, time 195460335, (41,36), root:(42,93),
    state 0x8, keycode 90 (keysym 0xff9e, KP_Insert), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x6000001,
    root 0xae, subw 0x6000002, time 195460340, (41,36), root:(42,93),
    state 0x8, keycode 87 (keysym 0xff9c, KP_End), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6000001,
    root 0xae, subw 0x6000002, time 195460345, (41,36), root:(42,93),
    state 0x8, keycode 87 (keysym 0xff9c, KP_End), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x6000001,
    root 0xae, subw 0x6000002, time 195460351, (41,36), root:(42,93),
    state 0x8, keycode 88 (keysym 0xff99, KP_Down), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6000001,
    root 0xae, subw 0x6000002, time 195460356, (41,36), root:(42,93),
    state 0x8, keycode 88 (keysym 0xff99, KP_Down), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x6000001,
    root 0xae, subw 0x6000002, time 195460365, (41,36), root:(42,93),
    state 0x8, keycode 80 (keysym 0xff97, KP_Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6000001,
    root 0xae, subw 0x6000002, time 195460367, (41,36), root:(42,93),
    state 0x8, keycode 80 (keysym 0xff97, KP_Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6000001,
    root 0xae, subw 0x6000002, time 195460372, (41,36), root:(42,93),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

you're right about the ALT+128 producing € - the same goes for the $ being generated with ALT+36 - and since the keyboard has a $ key next to the € key, here is the xev output from the $ key

```
KeyPress event, serial 36, synthetic NO, window 0x6600001,
    root 0xae, subw 0x6600002, time 187165096, (31,31), root:(32,88),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x6600001,
    root 0xae, subw 0x6600002, time 187165101, (31,31), root:(32,88),
    state 0x8, keycode 90 (keysym 0xff9e, KP_Insert), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6600001,
    root 0xae, subw 0x6600002, time 187165106, (31,31), root:(32,88),
    state 0x8, keycode 90 (keysym 0xff9e, KP_Insert), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x6600001,
    root 0xae, subw 0x6600002, time 187165112, (31,31), root:(32,88),
    state 0x8, keycode 90 (keysym 0xff9e, KP_Insert), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6600001,
    root 0xae, subw 0x6600002, time 187165117, (31,31), root:(32,88),
    state 0x8, keycode 90 (keysym 0xff9e, KP_Insert), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x6600001,
    root 0xae, subw 0x6600002, time 187165122, (31,31), root:(32,88),
    state 0x8, keycode 89 (keysym 0xff9b, KP_Next), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6600001,
    root 0xae, subw 0x6600002, time 187165128, (31,31), root:(32,88),
    state 0x8, keycode 89 (keysym 0xff9b, KP_Next), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x6600001,
    root 0xae, subw 0x6600002, time 187165135, (31,31), root:(32,88),
    state 0x8, keycode 85 (keysym 0xff98, KP_Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6600001,
    root 0xae, subw 0x6600002, time 187165138, (31,31), root:(32,88),
    state 0x8, keycode 85 (keysym 0xff98, KP_Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6600001,
    root 0xae, subw 0x6600002, time 187165144, (31,31), root:(32,88),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```
which works out to be:
keycode  64 = Alt_L Meta_L Alt_L Meta_L
keycode  90 = KP_Insert KP_0 KP_Insert KP_0
keycode  90 = KP_Insert KP_0 KP_Insert KP_0
keycode  89 = KP_Next KP_3 KP_Next KP_3
keycode  85 = KP_Right KP_6 KP_Right KP_6

---

### Post by enimeizoo on 2011-07-28
Does the $ key work?

Anyway, the easiest 'fix' would be to let alone that key, and add the EuroSign keysym to another key. Like alt_GR+e .
To to that, check ```
xmodmap -pke | grep "e E"
```.
Create a .xmodmap file (if it doesn't already exists), and put the line you got from the last command.
Replace the fifth keysym by 'EuroSign'
Run ```
xmodmap .xmodmap
```
Check if you can get the euro key with altGR+e.

Then, depending on what desktop environment you have, it will or will not offer you to load it when you will reboot (I know gnome and kde will, not sure about unity and xfce). If it doesn't, you can create a .profile file that will be run on login. Put the 'xmodmap .xmodmap' command in, and you're done.

Just in case, you have a full list of available keysyms in the /usr/include/X11/keysym.h file. You can assign up to 6 keysyms to a keycode. You can get them using combinations of shift, altGR, and ModeSwitch. By default, the ModeSwitch keysym isn't assigned to anything, though, so unless you add it manually, you only have access to out 4 of 6 keysyms (the first two, and the last two). 

I still have no Idea how to modify macro keys. It might even be hardwired, actually...
Hope it helps.

---

### Post by awillson5 on 2012-10-18
for me Alt+2...by regular us keyboard

---

### Post by pietsnot on 2012-12-02
> **peter d said:**
> Alt Gr + 4 works for me.Thus: €

thanks Peter D :)

---

