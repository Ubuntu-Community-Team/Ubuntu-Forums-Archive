---
title: "alt-tab shortcut mysteriously broken"
date: 2009-12-30
forum: General Help
---

### Post by robgwin on 2009-12-30
[edit: fixed by reboot. whatever...]

On Karmic 9.10 with the default Gnome desktop, and I can't make Alt+Tab work for ANY function under System > Preferences > Keyboard Shortcuts. Specifically I want to assign it to "Move between windows, using a popup window", but really it just doesn't work on anything. From what I've read this is usually a compiz conflict, but I am NOT running compiz, and my Visual Effects are set to "None".

When I select a shortcut to edit and press Alt+Tab it does correctly say "Alt+Tab", so I know it's recording the key correctly. And every other key combo seems to work fine for any shortcut, including other combinations with the Alt key, like Alt+Q. Only Alt+Tab fails to execute any shortcut its assigned to.

I've never tweaked xmodmap files, I've dabbled *slightly* with the keyboard layout options -- but have reverted everything to default settings just to make sure.

Anyone got any tips on where I could start troubleshooting this? I'm not sure where to look at this point...

Thanks a ton,
rob

---

### Post by robgwin on 2009-12-30
oh for the... after I posted that I figured I'd reboot as a measure of sheer desperation, and alt-tab works fine now. geeeeez, I'm a dork. And still in the dark about the problem, but I don't care anymore cause it works (sounds like windows all over again! ;)

---

### Post by lasleym on 2009-12-30
Lordy!  I have (HAD) the EXACT problem.  So, I guess there's two dorks out there in Ubuntu-land.  Thank you this worked.  I did have to adjust my shortcuts after the restart - but now my alt+tab works LIKE IT SHOULD.  

Thank you for helping reset my keyboard shortcut alt+tab!
:D
:)
:lolflag:

---

### Post by teryret on 2010-11-01
Thanks for the visual effects tip robgwin!  I was having a very similar problem in lucid.  For me no hotkey setting in keyboard shortcuts would bring up a terminal, and alt-tab didn't work, yet ctrl+alt+l worked as did a few others.  Per your research that it could be related to visual effect settings I checked there and found that zero of the three radio buttons were selected!  Once I selected Normal effects (I'm sure None and Extra would have also worked) all of my hotkey woes immediately disappeared!

---

### Post by Kangarooo on 2011-04-28
If you want to reset the keyboard shortcuts remove the directories global_keybindings, keybinding_commands, window_keybindings from the directory ~/.gconf/apps/metacity and logout/login (not necessary persé, but it sure is the easiest route).

---

