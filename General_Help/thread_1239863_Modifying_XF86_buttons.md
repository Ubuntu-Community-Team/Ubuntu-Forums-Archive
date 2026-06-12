---
title: "Modifying XF86 buttons"
date: 2009-08-14
forum: General Help
---

### Post by Lostin60's on 2009-08-14
I am running Jaunty on an HP laptop, using a USB keyboard.  I have a lot of mods to my xmodmap that I am making.  Changing mouse clicks to key presses, launching apps and such.  

I pretty well have it worked out, as it is mostly changing kesyms. However to mod an XF86 key, I need to assign a different command to it. I have not figured that one out yet. For instance, hitting my "E-mail" button brings up evolution, which is ok, except I use zimbra, so I need to change the command from "evolution" to "zdesktop".

"My Computer" brings up my home folder, rather than the root folder.  I,m just trying to add some personal touches.  I am sure there is a file where the XF86 buttons are defined, but I can't find it.

Any and all help will be appreciated.

---

### Post by Finalfantasykid on 2009-08-14
Have you tried going to Preferences > Keyboard Shortcuts?  There you can change what all the XF86 buttons do.

EDIT:  Actually it looks like the problem might actually be that zimbra is not your default mail reader.  Try going to Preferences > Preferred Applications and changin it there

---

### Post by CatKiller on 2009-08-14
> **finalfantasykid said:**
> actually it looks like the problem might actually be that zimbra is not your default mail reader.  Try going to preferences > preferred applications and changin it there

+1

---

### Post by Lostin60's on 2009-08-14
> **Finalfantasykid said:**
> Have you tried going to Preferences > Keyboard Shortcuts?  There you can change what all the XF86 buttons do.

EDIT:  Actually it looks like the problem might actually be that zimbra is not your default mail reader.  Try going to Preferences > Preferred Applications and changin it there

In System > Preferences > Keyboard Shortcuts you can change the keybindings for an action i.e. <CTRL> + c to launch calculator rather than XF86Calculator.  However it still launches the same calculator. If I want a different calculator, I have to change the value of XF86Calclator.

I have changed defaults in preferences. But I need to do more.  For instance I don't have an XF86WWW button.  I do have an XF86Home button. I want to make it launch Firefox.  So, I need to change the value of XF86Home to Firefox.

I am going to try to do it with aliases, that may work, but I really want to find the file that defines the XF86 buttons. Or a file that defines keyboard shortcuts.

Thanks for trying, but I need to keep working on it.

---

### Post by CatKiller on 2009-08-14
You seem to be confused. The keyboard shortcuts are editable. You just click in the box and press the button or buttons that you want to do something. You could set "F" to launch Firefox if you wanted, although I wouldn't recommend it.

The programs that get launched are the ones that you've set in your preferred applications. So whatever button combination you've got set as "Launch web browser" will start whatever you've got set as your preferred application for Web Browser.

You don't need to mess about with aliases.

---

### Post by Lostin60's on 2009-08-14
> **CatKiller said:**
> You seem to be confused. The keyboard shortcuts are editable. You just click in the box and press the button or buttons that you want to do something. You could set "F" to launch Firefox if you wanted, although I wouldn't recommend it.

The programs that get launched are the ones that you've set in your preferred applications. So whatever button combination you've got set as "Launch web browser" will start whatever you've got set as your preferred application for Web Browser.

You don't need to mess about with aliases.

OK, I am not confused, I am just not stating my issues clearly. I used poor examples. Through keyboard shortcuts, and preferred apps I have XF86Tools launching Rhythmbox, XF86Mail launching Zimbra, and XF86Home launching Firefox.

Suppose, though, that I want my the My Computer key (the name on my keyboard) to launch ```
nautilus /
``` instead of ```
nautilus ~/
``` as it does now.  I know I can do this in Compiz > Commands, but I would prefer not to.

The reasons for wanting to do these things is that due to an injury, I type way to slow.  I want to get away from the mouse as much as possible.  I can do a lot with xmodmap. I believe that Mode_switch is a press to start/press to stop key, or can be made so. then I can assign mouse button symcodes to <Mode_switch> + <some key>.

I can't, however do that for the XF86 keys, without trying to find a keysym for an action e.g. launch oowriter, and bind it to a key combination. And I am not sure that would work.

The easiest thing would be to find where actions are assigned to the XF86 keys, and mod that file.  If you have another alternative, I would be happy to hear it.  I am trying to make this as "painless" as possible for myself..lol.

---

### Post by CatKiller on 2009-08-14
That makes a bit more sense. I don't know where the configuration for the parts that aren't exposed through GConf (and so available for the Preferred Applications tool) are stored. It's possible that they're currently hard-coded in in some fashion. I believe (from a little bit of reading on the subject) that it's gnome-settings-daemon that interprets the media keys, and it's nautilus that acts on them. Since they're both tightly integrated into Gnome, I haven't managed to find any interface information for how they interact. It's also the case that if you try to set the keyboard shortcut to one of the media keys coupled with a modifier it causes a gnome-settings-daemon crash.

Metacity also has generic command capabilities; you don't need to be using Compiz to do it.

I don't really know what else to suggest. Good luck in your search for mouse-free computing. There is a way to make the mouse move with the cursor keys, but I'm not sure that that would especially help you.

Sorry I couldn't be more help.

---

### Post by Lostin60's on 2009-08-14
> **CatKiller said:**
> That makes a bit more sense. I don't know where the configuration for the parts that aren't exposed through GConf (and so available for the Preferred Applications tool) are stored. It's possible that they're currently hard-coded in in some fashion. I believe (from a little bit of reading on the subject) that it's gnome-settings-daemon that interprets the media keys, and it's nautilus that acts on them. Since they're both tightly integrated into Gnome, I haven't managed to find any interface information for how they interact. .

Metacity also has generic command capabilities; you don't need to be using Compiz to do it.

I don't really know what else to suggest. Good luck in your search for mouse-free computing. There is a way to make the mouse move with the cursor keys, but I'm not sure that that would especially help you.

Sorry I couldn't be more help.

And there-in lies the story.  LOL.  I too can't figure out where the files are.  I was under the impression, though, that nautilus was just a file manager.

As to > It's also the case that if you try to set the keyboard shortcut to one of the media keys coupled with a modifier it causes a gnome-settings-daemon crashwhy would one even do that?? Those keys are gonna do what they do.  And making a 2 key shorcut to what is already a one key shortcut, kinda defeats the purpose.

In keymap there are several keycodes to launch apps, and they are all referred to by XF86foo. I haven't figured keymap out as well though. Changes are made more easily in xmodmap.  

In xmodmap all you need to do is copy the output of xmodmap -pke, modify it, and tell xmodmap to use it as default.  If I can find a way to do that in keymap, my problems are solved.

Thanks for your help and input.  Check back now and again, and I will post my results. When all is said and done, it may be worth writing a tutorial for.

---

### Post by CatKiller on 2009-08-14
> **Lostin60's said:**
> I was under the impression, though, that nautilus was just a file manager.

Well, it **is** Gnome's file manager, so it does a bunch of other things as part of that. It draws the Desktop background, for one thing, and it's scriptable. It's able to use scripts to burn cds, for example, and execute things on events, like mounting a cd. How much is nautilus itself and how much is the scripts or the rest of the Gnome stack is kinda fuzzy.

> 
As to why would one even do that?? Those keys are gonna do what they do.  And making a 2 key shorcut to what is already a one key shortcut, kinda defeats the purpose.Because if you could use modifier keys with the special media keys then you could have, for example, XF86MyComputer launch Nautilus' default location, but Alt+XF86MyComputer launch Nautilus at some other location, like /. I can't imagine why you would want to use one button for more than one thing... :)

And crashing gnome-settings-daemon let me know what it was that was interpreting the key presses.

> 
When all is said and done, it may be worth writing a tutorial for.Definitely. The internals are quite interesting to know, even if that knowledge doesn't end up helping anyone on these forums (although it generally does come in useful here). When it's not your own problem to solve, though, it's difficult to keep the focus. I wish you good fortune.

EDIT: I don't know much about keymaps directly, but the XF86 keyboard symbols are apparently defined in [XF86keysym.h]("http://wiki.linuxquestions.org/wiki/XF86_keyboard_symbols") in the Xorg source code. Perhaps that would be useful information in your quest to set up a keymap for them, even if we haven't found where else they're interpreted.

---

### Post by gr4viton on 2011-01-27
very interesting thread :)..
The XF86 keys can be recognized with another modifier at least some of them.
(ASUS U30JC - Ubuntu 10.10)
Though I don't know how to do it with xbindkeys (which is the way which I would like to catch them).
The media player Audacious(2)'s Global Hotkey plugin "hotkeys.so" did recognized Control+Fn+XF86foo when I tried!
I wanted to set up Control+Fn+(Play/Pause,Stop,VolumeUp/Dn ...) to control only audacious not the gnome volume and media-control.
Although it sucks, because every Control+Fn+... works, but the Control+Fn+PreviousSong is not recognized by audacious..

I wonder why is the "Fn" key not just another modifier. The life would be so much easier !:KS

Is there any way to setup Fn + "not XF86 key" in xbindkeys?
Is there a way to setup Fn + "XF86 key" in xbindkeys? 
On my laptop it only recognizes XF86Tools, which is in my opinion miss-named because the key which generates it is "TouchpadToggle" so the key should generate "XF86TouchpadToggle"

---

