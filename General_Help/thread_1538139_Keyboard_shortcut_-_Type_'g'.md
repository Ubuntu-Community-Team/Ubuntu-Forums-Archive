---
title: "Keyboard shortcut - Type 'g'"
date: 2010-07-24
forum: General Help
---

### Post by 98cwitr on 2010-07-24
g went out on my gf's keyboard and im trying to set up a keyboard shortcut to type 'g' 

it's asking for a command and I dont know what the command for an IRQ (or just to type a letter) is. Any help?

I tried 

```
echo 'g'
``` didn't work :(

---

### Post by 98cwitr on 2010-07-25
bump

---

### Post by 98cwitr on 2010-07-26
bump...come on...I was convinced this was simple and i was just an idiot ;)

---

### Post by AlphaLexman on 2010-07-26
Ok, is the 'G' key missing, doesn't work when you press it, or what?
Have you tried an 'on screen keyboard' clickable by the mouse?

Another option might be, Applications, Accessories, Character Map.

---

### Post by jerenept on 2010-07-26
> **98cwitr said:**
> bump...come on...I was convinced this was simple and i was just an idiot ;)

[This]("http://zareason.com/shop/product.php?productid=16162") is probably what you want. Any cheap old one will do.

---

### Post by 98cwitr on 2010-07-27
g key is intact, just doesn't work when I press it. It does press without obstruction or uncommon resistance. That said, a USB keyboard isn't going to work ergonomically for her and character map doesn't let you input a separate key string or macro. Onboard (the on-screen keyboard) gets in the way of things and is a bit cumbersome, from a usability standpoint, for the task. I know she can just copypasta a 'g' off a website, but I would like to set something more statically configured and nonvolatile. Thanks for your help.

---

### Post by ThesaurusRex on 2010-07-27
I was also unable to create a keyboard shortcut which would simply "echo 'g.'" Maybe what you should try is to create a custom keyboard layout.

...But doesn't this seem somewhat unnecessary? Wouldn't it be easier to buy a new keyboard? Or is she using a laptop, which would make buying a new keyboard the more obnoxious choice?

---

### Post by simosx on 2010-07-27
> **98cwitr said:**
> g went out on my gf's keyboard and im trying to set up a keyboard shortcut to type 'g' 

it's asking for a command and I dont know what the command for an IRQ (or just to type a letter) is. Any help?

I tried 

```
echo 'g'
``` didn't work :(

Follow the tip at
[http://ubuntuforums.org/showpost.php?p=9622616&postcount=4](http://ubuntuforums.org/showpost.php?p=9622616&postcount=4)

The keycode for 'g' is 42.

See [http://linux.die.net/man/8/xsendkeycode](http://linux.die.net/man/8/xsendkeycode) on how to get 'G' as well. You need a new shortcut for this.

What these commands do is inject an event that says that the 'g' key has been pressed.

---

### Post by 98cwitr on 2010-07-27
it's a laptop...sorry should have mentioned that

had to install a program called lineakd, and used ```
xsendkeycode 42 1 && xsendkeycode 42 0
``` for the macro and it just keeps typing g until I open terminal and execute xsendkeycode 42 0 again. Using ; instead of && doesn't work either :?

It works in terminal...not as a macro though...wtf

EDIT: tried using ```
xsendkeys "g"
``` no joy there either

---

### Post by simosx on 2010-07-27
> **98cwitr said:**
> had to install a program called lineakd, and used ```
xsendkeycode 42 1 && xsendkeycode 42 0
``` for the macro and it just keeps typing g until I open terminal and execute xsendkeycode 42 0 again :?

Yeah, you need to create a Keyboard Shortcut (in System/Preferences) that will invoke the script that sends the 'g'. Read the URL I gave you on the issue of those '0' and '1' parameters and why they need to match. 

You would create a shortcut for, let's say [Start/Win key] + 6 for 'g' and [Start/Win key] + Shift + 6 for 'G'.

You can also modify your current keyboard layout, which might be easier to do. For this, post the output of 

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

and indicate where you want your 'g' to come from.

---

### Post by 98cwitr on 2010-07-27
> **simosx said:**
> Yeah, you need to create a Keyboard Shortcut (in System/Preferences) that will invoke the script that sends the 'g'. Read the URL I gave you on the issue of those '0' and '1' parameters and why they need to match. 

You would create a shortcut for, let's say [Start/Win key] + 6 for 'g' and [Start/Win key] + Shift + 6 for 'G'.

You can also modify your current keyboard layout, which might be easier to do. For this, post the output of 

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

and indicate where you want your 'g' to come from.

no no, already got all that...what im saying is when I go System->Preferences->Keyboard Shortcuts->Add, name the shortcut, enter the command as ```
xsendkeycode 42 1 && xsendkeycode 42 0
``` and assign ctrl+shift+z; I open a web browser and with the cursor in the URL bar I hit ctrl+shift+z it types
ggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggg
until I hit another key on the keyboard...it's only reading the first part of the command from my command string. I try to put it in single and double quotes and then it doesn't do anything :(

---

### Post by simosx on 2010-07-27
> **98cwitr said:**
> no no, already got all that...what im saying is when I go System->Preferences->Keyboard Shortcuts->Add, name the shortcut, enter the command as ```
xsendkeycode 42 1 && xsendkeycode 42 0
``` and assign ctrl+shift+z; I open a web browser and with the cursor in the URL bar I hit ctrl+shift+z it types
ggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggg
until I hit another key on the keyboard...it's only reading the first part of the command from my command string. I try to put it in single and double quotes and then it doesn't do anything :(

If you notice my script (in two lines), there is a strange 'sleep 0.5' which adds a delay of half a second. The reason I put it is that without this delay, the xsendkeycode fails to run. So, either try to add this strange delay or try my variation of the script.

---

### Post by 98cwitr on 2010-07-27
ok I saved a file named test and put it in my home dir

contents:

> 
#!/bin/sh
sleep 0.5
/usr/bin/xsendkeycode 42 1
/usr/bin/xsendkeycode 42 0


made it executable and set the command string to ~/test. It fails

"Error while trying to run (~/test) which linked to the key (<Mod4>a)"

It does nothing in terminal either.

---

### Post by simosx on 2010-07-27
> **98cwitr said:**
> ok I saved a file named test and put it in my home dir

contents:



made it executable and set the command string to ~/test. It fails

"Error while trying to run (~/test) which linked to the key (<Mod4>a)"

It does nothing in terminal either.

That's strange. In Keyboard Preferences, did you put the full path? It might not like the ~ character for home path. The full path is /home/.../...

---

### Post by 98cwitr on 2010-07-27
> **simosx said:**
> That's strange. In Keyboard Preferences, did you put the full path? It might not like the ~ character for home path. The full path is /home/.../...

freakin right...full path worked...thank dude. We're all good here! + imaginary rep :)

---

### Post by AlphaLexman on 2010-07-27
[http://www.overclock.net/computer-peripherals/491752-good-keyboard-guide.html](http://www.overclock.net/computer-peripherals/491752-good-keyboard-guide.html)
Shows examples of why keys fail. Glad to see you found a solution.

---

### Post by simosx on 2010-07-27
> **98cwitr said:**
> freakin right...full path worked...thank dude. We're all good here! + imaginary rep :)

Nice.

Now add '[SOLVED]' to the title of the post.

---

