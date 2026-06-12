---
title: "keyboard shortcut to run a terminal"
date: 2009-12-31
forum: General Help
---

### Post by Preserved Killick on 2009-12-31
Hi all.  I hope someone knows the answer to this.  I have been starting a terminal with a keyboard shortcut for a few years.  It was the 'start' button on a Microsoft keyboard.  This key is between Ctrl and Alt on the left side of the keyboard.  Now that I've upgraded to 9.10, I can't assign the 'start' key to the 'run a terminal' shortcut.  

I'm habitually tapping the start key for a new terminal window but now of course it doesn't do anything.  Anyone here know what I can do to add this keyboard shortcut with 9.10?

Thanks!

killick

---

### Post by pastalavista on 2009-12-31
Open System--> Preferences--> Keyboard Shortcuts. Under the Desktop category is an entry "Run Terminal" where you can set your key.

Edit: I see you can't use the Windows key (Mod4) by itself. I set mine to Mod4 + z. Have to use an extra finger I guess.

---

### Post by x33a on 2009-12-31
are you able to use the key in windows (if you are dual booting)? 

i use ```
left_ctrl+`
``` and this works pretty well for me.

---

### Post by Preserved Killick on 2009-12-31
Hi guys.  Thanks for replying.  What is a Mod4 key?  

I am not dual booting.  This box hasn't ever had Windows.  I used the 'start' key this morning with ubuntu 8.04, but it's not working in 9.10.  Could there be some advanced keyboard setting?  I will investigate.  New ideas are still welcome!  

Thanks,

killick

---

### Post by x33a on 2009-12-31
mod4 key is the windows key.

try ```
xmodmap
```

to see the mappings of your keys.

---

### Post by Preserved Killick on 2009-12-31
OK, I started playing with the Prefs > Keyboard > Layouts.

I don't have a Microsoft Comfort Curve 2000 keyboard-- I have a Microsoft Basic.  But the 'Basic' model wasn't listed so I tried Comfort Curve.  Under Layout Options I changed the Alt/Win key behavior from default to "Add the standard behavior to the Menu key," not knowing what that would be.  The 'start' key still does nothing, but now the 'Menu' button -- between the alt and ctrl buttons on the RIGHT side will open a terminal.  Fine.  I will have to get used to using my other hand.

Thank you,

-- killick

---

