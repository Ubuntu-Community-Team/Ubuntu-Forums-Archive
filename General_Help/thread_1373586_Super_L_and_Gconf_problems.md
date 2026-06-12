---
title: "Super_L and Gconf problems"
date: 2010-01-05
forum: General Help
---

### Post by jellyxbean on 2010-01-05
So whilst talking with a friend on our recent switch to ubuntu we realized the windows key or 'Super_L" is useless unless you program it to a button. He wanted it for his panel button. I wanted it for a more simple Alt+tab. One button doing the function of two so thus after searching the webs I found a means with terminal using gconf-editor then going to apps then metacity then global keybindings there was a option called switch_windows_backward and I tried switching that which worked till a restart. So then I made a script and added it to my start up list. with this code
gconftool-2 --set /apps/metacity/global_keybindings/switch_windows_backward--type string "Super_L"

well this idea worked for a few but now it does not. now even in going into the Gconf editor if I attempt to change the option there it doees not change from the disabled option and the editor wont let me add Super_L to any of my options.

So I am asking for a work around to this. or if there is any.

---

### Post by lyall on 2010-01-05
jellyxbean

If you could post you file should could look at it and see what is going on.

good luck and have fun learning

---

### Post by jellyxbean on 2010-01-05
#!/bin/bash
xinput set-int-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 8 0 3 0 0 1 2 3 &> /dev/null

gconftool-2 --set /apps/metacity/global_keybindings/switch_windows_backward--type string "Super_L"

  
thats my startup script the first part fixes a middle click issue I had and the second part is obviously the portion I want to have make the window_backward put onto my windows key

---

### Post by jellyxbean on 2010-01-08
hoping someone can help me out here =|

---

