---
title: "CTRL + V in terminal??"
date: 2009-10-23
forum: General Help
---

### Post by PerfectReign on 2009-10-23
Is there any way I can enable the standard CTRL+C for copy and CTRL+V for paste in the terminal window?

Since I'm forced on occasion to enter the command line for various operations - such as VirtualBox upgrades after a kernel update - I want to simply paste commands. However, I have to remember - and tell my distance friends/family whom I'm supporting - that the standard CTRL+V they've been using since the '80s doesn't work.  

What can be done?

---

### Post by Shpongle on 2009-10-23
use shift too :-)

---

### Post by drs305 on 2009-10-23
And don't forget if you are using a mouse you probably have the option to just highlight the line anywhere then middle click anywhere to paste (terminal or not).

Outside a terminal: CTRL-c, CTRL-v
Inside terminal: CTRL-SHIFT-c, CTRL-SHIFT-v

---

### Post by Jayferd on 2009-10-23
If you're running the same commands over and over again, you may want to consider just writing a script.  In your favorite text editor (i just use gedit), make a file like "myscript.sh" with the contents:
```

#!/bin/bash
sudo run really long command with lots of parameters

```
Then make it executable with chmod:
```

chmod +x myscript.sh

```
If you want to really be a hax0r, you can even make an alias for it by putting a softlink into /usr/bin:
```

sudo ln -s myscript.sh /usr/bin/myscript

```
Then you can just type "myscript" and it'll run the thing.

Have fun!

Peace,
--Jay

---

### Post by PerfectReign on 2009-10-23
Thank you for all the answers.

I do run the "myscript" thing for running one command at work. I just double-click, the terminal opens, the script runs, and it closes.

So, is there any way not to have to use SHIFT+CTRL+V ?  Can i modify some command file somewhere?

---

### Post by vinutux on 2009-10-23
mmm.......helpful discussions.........

---

### Post by alphaniner on 2009-10-23
> **PerfectReign said:**
> So, is there any way not to have to use SHIFT+CTRL+V ?  Can i modify some command file somewhere?

I doubt there's any file you can modify.  Maybe if you compiled your own version of xterm...

I don't know if it will help any, but do you know you can use CTRL+R to search your command history?

---

### Post by kanikilu on 2009-10-23
> **PerfectReign said:**
> So, is there any way not to have to use SHIFT+CTRL+V ?  Can i modify some command file somewhere? CTRL+V is already taken as a control character in BASH:
> Ctl-V

When inputting text, Ctl-V permits inserting control characters. For example, the following two are equivalent:

echo -e '\x0a'
echo <Ctl-V><Ctl-J>

[http://tldp.org/LDP/abs/html/special-chars.html#CONTROLCHARREF](http://tldp.org/LDP/abs/html/special-chars.html#CONTROLCHARREF)

---

### Post by Giblet5 on 2009-10-23
> **kanikilu said:**
> CTRL+V is already taken as a control character in BASH:


[http://tldp.org/LDP/abs/html/special-chars.html#CONTROLCHARREF](http://tldp.org/LDP/abs/html/special-chars.html#CONTROLCHARREF)

What's wrong with Shift+Ins?

That's standard too. And it works.

---

### Post by P4man on 2009-10-23
kanikilu beat me to it. There is a reason why you have to add the shift in the terminal. Control v and control c already have a very different meaning, and one that predates any concept of a GUI or copy/paste :)

---

### Post by Giblet5 on 2009-10-23
Ctrl+V is "Verbose Mode" in bash's default (vi mode) command line editor. (technical note: The next character is not to be interpreted by readline(3C). See 'man bash' and read the section about READLINE.)

You should use Shift+Ins.

It's standard on ... everything.

It works.

---

### Post by kanikilu on 2009-10-23
> **Giblet5 said:**
> What's wrong with Shift+Ins? You mean *other* than it takes two hands, versus one for SHIFT+CTRL+V? :P

---

### Post by Giblet5 on 2009-10-23
> **kanikilu said:**
> You mean *other* than it takes two hands, versus one for SHIFT+CTRL+V? :P

How typical. You're losing an argument (woefully, I might add) so you start cheating by using logic and reason. ;)

---

### Post by P4man on 2009-10-23
Not really. There is a right shift key too, more than close enough to insert to be used with one hand. Then again after all these years I can hit control V blindfolded being piss drunk and having my arm in a cast, and shift +ins.. well not quite that easy. There is always middle mouse button though. Not just one hand, one **finger**. Try that with your  keyboard shortcuts :P

---

### Post by Giblet5 on 2009-10-23
> **P4man said:**
> Not really. There is a right shift key too, more than close enough to insert to be used with one hand. Then again after all these years I can hit control V blindfolded being piss drunk and having my arm in a cast, and shift +ins.. well not quite that easy. There is always middle mouse button though. Not just one hand, one **finger**. Try that with your  keyboard shortcuts :P

G15 gaming keyboard.

18 macro keys on the left, times four banks.

One key = Shift+Ins

Another key = ```
sudo find ./ -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; sudo find ./ -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; echo "It's all mine now..."
```

---

### Post by kanikilu on 2009-10-23
:lolflag:

Though I gather not everything supports the SHIFT+CTRL+V shortcut, so it certainly doesn't hurt to know about SHIFT+INS. I actually forgot about that one myself, and also didn't realize it works on Windows as well....learn something everyday.

Heh, P4man, good point about the right shift, didn't think about that since it's kind of an awkward combination for me...but would probably work just fine for southpaws ;)

Wish the middle mouse button worked for me, that would be *much* quicker...my stupid expensive mouse changes the scroll from an indexed click to a smooth scroll when pressed :mad:

---

### Post by P4man on 2009-10-23
> **kanikilu said:**
> 
Wish the middle mouse button worked for me, that would be *much* quicker...my stupid expensive mouse changes the scroll from an indexed click to a smooth scroll when pressed :mad:

You also got a logitech MX revolution ?
If so, do you have any idea how to remap the search button (which acts like a keypress in xev) to the middle mouse button ?
Sorry to go off topic, [but ive been looking for that solution]("http://ubuntuforums.org/showthread.php?t=1274424") for a long time

---

### Post by Giblet5 on 2009-10-23
> **P4man said:**
> You also got a logitech MX revolution ?
If so, do you have any idea how to remap the search button (which acts like a keypress in xev) to the middle mouse button ?
Sorry to go off topic, [but ive been looking for that solution]("http://ubuntuforums.org/showthread.php?t=1274424") for a long time

I don't have my MX anymore. It got ..... broken... By my head... Pro Tip: When the wife says "You never listen to me!" the CORRECT reply is "Yes, dear. I'm sorry." and not "Huh?"

But I got the buttons to generate ButtonX events using an entry in xorg.conf:
```
....
Section "InputDevice"
    Identifier     "MX700"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "9"
EndSection
.....
```

---

### Post by P4man on 2009-10-23
> **Giblet5 said:**
> I don't have my MX anymore. It got ..... broken... By my head... Pro Tip: When the wife says "You never listen to me!" the CORRECT reply is "Yes, dear. I'm sorry." and not "Huh?"

But I got the buttons to generate ButtonX events using an entry in xorg.conf:
```
....
Section "InputDevice"
    Identifier     "MX700"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "9"
EndSection
.....
```

awsome.. Ill try that after my download completed. thanks !

Since the OP's question is answered Ill just continue hijacking this thread, and make a suggestion: contact logitech customer service. My MX broke down after about about 3 years, I had no idea if it was still covered, I had no receipt, but I called then anyway. When I explained it broke down, I had no purchase receipt, it was 2 or 3 years old they told me: "its probably still covered, it has 3 year warranty so just send us some pictures of the mouse showing the serial number. Then physically destroy the mouse, ;make a picture and send us those." I had to use a heavy hammer to do any visible damage lol, sent the pics and 4 days later I had a brand new MX revolution in my mail.

**edit**: on closer inspection that xorg wont do me any good, Read [my thread]("http://ubuntuforums.org/showthread.php?t=1274424") the search button behaves differently from all other mouse buttons. They all work btw. just search is a key somehow

---

### Post by kanikilu on 2009-10-23
Yeah, MX Rev. I imagine it could be done with xmodmap, but I haven't the faintest idea how to actually do it.

A quick search turned up this post that might help:

[http://ubuntuforums.org/showpost.php?p=6273040&postcount=2](http://ubuntuforums.org/showpost.php?p=6273040&postcount=2)

I guess just use the keycode you found the search button to be...?

I haven't tried this since I'm not in "native" Ubuntu here (VBox) and xev doesn't register any of the addition buttons on the mouse.

> Then physically destroy the mouse, ;make a picture and send us those." I had to use a heavy hammer to do any visible damage lol, sent the pics and 4 days later I had a brand new MX revolution in my mail. LOL!

---

### Post by P4man on 2009-10-23
> **kanikilu said:**
> 
A quick search turned up this post that might help:

[http://ubuntuforums.org/showpost.php?p=6273040&postcount=2](http://ubuntuforums.org/showpost.php?p=6273040&postcount=2)



My hero! That actually Works woohoo. I googled like weeks to find that!

---

### Post by kanikilu on 2009-10-23
I'm definitely no expert, but my Google-foo is strong :D

---

### Post by MasterProg on 2009-10-23
I've always used context menu to do that... :)

I think I've learned something today (c)

---

### Post by Marlonsm on 2009-10-23
What's up with people here... they like to do stuff the hard way. :P

Just open the terminal, go to Edit > Keyboard Shortcuts and set "Paste" to Ctrl+V.

---

### Post by flipper9 on 2009-10-23
> **Marlonsm said:**
> What up with people here... they like to do stuff the hard way. :P

Just open the terminal, go to Edit > Keyboard Shortcuts and set "Paste" to Ctrl+V.

There is an easier way.  Just hold down the SHIFT key along with Ctrl+V.  Then you don't even have to do that.

---

### Post by Marlonsm on 2009-10-23
> **flipper9 said:**
> There is an easier way.  Just hold down the SHIFT key along with Ctrl+V.  Then you don't even have to do that.

The problem is to remember that always you paste something in the terminal.

---

### Post by Vaphell on 2009-10-23
i got so used to copy/paste by select+middle click that i am annoyed when I try to use that combo in windows :D how could they not implement it? :/

---

### Post by PerfectReign on 2009-10-23
> **Giblet5 said:**
> What's wrong with Shift+Ins?

That's standard too. And it works.
I've been using CTRL+V as paste since being on a Mac in the '80s. It is also good for Wintendo and KDE and GNOME.

---

### Post by PerfectReign on 2009-10-23
> **Marlonsm said:**
> What's up with people here... they like to do stuff the hard way. :P

Just open the terminal, go to Edit > Keyboard Shortcuts and set "Paste" to Ctrl+V.
You rock, man!!

I had tried something like this in Konsole and never found anything. I figured same was for the GNOME terminal.

:popcorn:

---

