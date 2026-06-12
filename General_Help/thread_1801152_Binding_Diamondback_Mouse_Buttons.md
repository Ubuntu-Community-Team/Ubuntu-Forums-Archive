---
title: "Binding Diamondback Mouse Buttons"
date: 2011-07-10
forum: General Help
---

### Post by Cryocrat on 2011-07-10
Hey, so I've got a Razer Diamondback mouse and I want to change what some of the buttons do. The mouse has the normal three buttons that every mouse has, as well as two more on each side. The scroll wheel button, and one on each side do nothing. I'd like to get the scroll wheel button to work as page up, the back right side button as paste, and the back left side button as F5. I've done a little research on this and found to edit my xorg.conf file, but this where I ran into a problem. The mouse entry in my xorg file looks like this:

```
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

```I'm assuming that since this chunk is commented out that if I edit anything it won't make any difference, even if I uncomment it. And I wouldn't know what exactly to put to achieve what I want if it wasn't commented. I've looked at the console-setup thing it mentions here but I'm not what to do with that. So I'm fairly well lost. So any ideas?

Edit: Oh, forgot to mention, I'm running Ubuntu 11.04. Let me know if there's any other info you need.

---

