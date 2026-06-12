---
title: "xmodmap to remap my keyboard"
date: 2009-07-17
forum: General Help
---

### Post by Richardcavell on 2009-07-17
Hi,

I have a MacBook that has command keys either side of the spacebar. I want them to do something useful. Using xev, I see that the keycodes of the keys are 133 and 134.

In my Startup Applications, I have a command: ```
xmodmap -e "keycode 133 = Pointer_Button2"
``` This allows me to make a middle mouse button press using my left command key. Now I want to map it as a control key. I try: ```
xmodmap -e "keycode 133 = Control_L"
```It doesn't work. Using xmodmap -pke, I notice that my real control key is mapped as:

> keycode  37 = Control_L NoSymbol Control_L NoSymbol Control_LSo now I remap my command key using the same string and get:

> keycode 133 = Control_L NoSymbol Control_L NoSymbol Control_LBut it still won't function as a control key. I have also tried changing it to Control_R. What am I missing here?

TIA, 

Richard

---

### Post by Kraut~salat on 2009-07-17
don't map another keycode to the Control_L key. Instead create a new keysymbol for you special apple key, like
xmodmap -e "keycode 133 = Apple_L"

then you have to add this key to your modifier table by using
xmodmap -e "add Control = Apple_L" 
if you want your special apple key to functions as a control key, or "Shift" for a shift key. The manpages will help you.

Then type
xmodmap -pm

this should show you then that the control modifier will be triggered by Control_L, Control_R and Apple_L now.

That should work

---

### Post by Richardcavell on 2009-07-17
Hi,

I was doing some experimenting and I have concluded that xev and keycode are unnecessary. The Apple Mac's command keys are already mapped as Super_L and Super_R on either a "USA" layout or a "USA Macintosh" layout. So the appropriate commands are:

To map left command key as a control key (note lowercase "c" in "control"):
```
xmodmap -e "add control = Super_L"
```To map right command key as a control key (note lowercase "c" in "control"):
```
xmodmap -e "add control = Super_R"
```To map left command key as middle mouse button:
```
xmodmap -e "keysym Super_L = Pointer_Button2"
```To map right command key as a double-click:
```
xmodmap -e "keysym Super_R = Pointer_DblClick_Dflt"
```and so on.

Richard

---

### Post by taojian on 2010-03-22
This is an old topic but it comes closer than any of the others I've seen to addressing my issue.

That issue is, I can't find a good thorough explanation of how xmodmap is used to change modifier keys. I've looked at the man file and I'm no stranger to Google but...

I'm using an Apple aluminum keyboard on a Dell running 9.10. It works fine, but I want to rearrange my modifier keys. I know that involves manipulating "mods" in xmodmap somehow -- that's what I can't find.

My keyboard's bottom row, from left to right:

control (keycode 37)
option/alt (keycode 64)
command (keycode 133)
space
command (keycode 134)
option/alt (keycode 108)
control (105)

I've set nothing in keyboard preferences, but have used an .xmodmap file to change my two command keys to Alt_L and Alt_R, and the two option/alt keys to Meta_R and Meta_L.

Now xev shows that the proper keys are producing the proper keycodes, my remapping is working, but the effects aren't what I wanted. All keyboard shortcuts that are listed as using Alt+something still use the actual option/alt key, rather than command, which is what I wanted.

For instance, Alt+F10 toggles maximization; if I click that shortcut and type in command+F10 instead, what's recorded is Alt+Mod4+F10, and I need to press BOTH the option/alt and command keys plus F10 to get the action. Presumably this is why there are "remove" statements in people's xmodmap files, but I don't know how to use them.

**tl;dr**  I'd like the machine to think I'm pressing alt when I press command, and think I'm pressing (what is that usually, the win key?) when I press option/alt. I'm good on control.

Any pointers very much appreciated! Here, for the heck of it, is the output of xmodmap -pm:

```

shift       Shift_L (0x32),  Shift_R (0x3e)
lock      
control     Control_L (0x25),  Control_L (0x42),  Control_R (0x69)
mod1        Super_L (0x40),  Super_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Alt_L (0x85),  Alt_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

```

---

### Post by taojian on 2010-03-23
Okay, I've made a bit of progress through brute trial and error and these links:
[http://ubuntuforums.org/showthread.php?t=1035750](http://ubuntuforums.org/showthread.php?t=1035750)
[http://www.linuxquestions.org/questions/linux-software-2/xmodmap-mod-keys-794513/](http://www.linuxquestions.org/questions/linux-software-2/xmodmap-mod-keys-794513/)

My .Xmodmap file looks like this:

```
clear mod1
clear mod4

keycode 133 = Alt_L
keycode 134 = Alt_R

keycode 64 = Meta_L
keycode 108 = Meta_R

add mod1 = Alt_L
add mod1 = Alt_R

remove mod1 = Meta_L
remove mod1 = Meta_R

add mod4 = Meta_L
add mod4 = Meta_R

```

I have no Super key now (and changing the Metas above to Super breaks everything so badly that not even Alt works), but I do have mod4, which is good for some things.

---

### Post by bitteralmond on 2010-07-07
> **Kraut~salat said:**
> don't map another keycode to the Control_L key. Instead create a new keysymbol for you special apple key, like
xmodmap -e "keycode 133 = Apple_L"
I tried that and got:

$ xmodmap -e "keycode 134 = Apple_R"
xmodmap:  commandline:1:  bad keysym name 'Apple_R' in keysym list
xmodmap:  1 error encountered, aborting.
$

> **Richardcavell said:**
> Hi,

I was doing some experimenting and I have concluded that xev and keycode  are unnecessary. The Apple Mac's command keys are already mapped as  Super_L and Super_R on either a "USA" layout or a "USA Macintosh"  layout. So the appropriate commands are:

To map left command key as a control key (note lowercase "c" in  "control"):
```
xmodmap -e "add control = Super_L"
```To map right command key  as a control key (note lowercase "c" in "control"):
```
xmodmap -e "add control = Super_R"
```
What if I have an alternative layout, like Colemak? I tried xmodmap -e "add control = Super_R" on the console and it accepted it, but the right command button still does nothing.

---

### Post by bitteralmond on 2010-07-07
I feel I came a bit closer to mapping my Macbook's right Command button as the right Ctrl button, but I encountered an error.  (I felt like it was partially working this time, because clearing control did disable my left ctrl button, and adding back Control_L did bring it back.)
> $ xmodmap -e "clear control"
$ xmodmap -e "keycode 37 = Control_L"
$ xmodmap -e "keycode 134 = Control_R"
$ xmodmap -e "add control = Control_L"
$ xmodmap -e "add control = Control_R"
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  118 (X_SetModifierMapping)
  Value in failed request:  0x17
  Serial number of failed request:  11
  Current serial number in output stream:  11
$

---

