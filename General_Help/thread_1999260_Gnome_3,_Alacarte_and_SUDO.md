---
title: "Gnome 3, Alacarte and SUDO"
date: 2012-06-07
forum: General Help
---

### Post by Rikeshar on 2012-06-07
Hey guys, I was wondering if anyone would be able to help.

I'm trying to create a launcher under Gnome 3, using Alacarte (Main Menu) that will run a script. Within the script is a sudo command and I'd like to be able to run this particular script without having to enter in my sudo password.

The script I have is fairly simple and is named launchDwarftherapist.sh:

```
#!/bin/bash
cd /home/zach/Games/"Dwarf Therapist"
sudo ./DwarfTherapist
```

From a terminal window I can type:
```
sh /home/zach/Games/launchDwarftherapist.sh
```
And it works fine, though it does ask me for my sudo password.

I created a launcher in alacarte with that same line and it doesn't do anything.

How can I make it so that I can run this particular script without having to type in my sudo password?

---

