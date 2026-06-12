---
title: "Screenshot Problem"
date: 2009-10-19
forum: General Help
---

### Post by PcBoyGeorge on 2009-10-19
[IMG]http://i685.photobucket.com/albums/vv219/Pikadude609/Screenshot-2.png[/IMG]

As you see in the picture above it shows that when I use the built-in screenshot feature in Ubuntu it leaves a faint thing showing the screenshot window there. How can I get this away as it is quite annoying.

---

### Post by -Zeus- on 2009-10-19
What delay are you using?

---

### Post by TheStroj on 2009-10-19
Interesting problem =). Just use the Print Screen button on your keyboard and it shouldn't do that.

---

### Post by P4man on 2009-10-19
probably due to a compiz effect. You could try hitting the pintscreen key on your keyboard (or alt + printscreen to grab the active window) Or install another screengrab program that allows a time out.

edit: hard to believe im still beaten to it lol

---

### Post by PcBoyGeorge on 2009-10-19
> **-Zeus- said:**
> What delay are you using?

What do you mean. Im new to linux so I do not know how to find this or change it. I can use printscreen fine but I would like this way to work aswell.

---

### Post by mike555 on 2009-10-19
set a 2 second delay.......

---

### Post by VCoolio on 2009-10-19
Open gconf-editor (with the alt-f2 box or run it in a terminal; I don't think it's in the applications menu by default), then on the left navigate to apps > metacity > keybinding_commands. Now on the right at the bottom you see two commands: command_screenshot which is for a screenshot of the whole screen (what happens with "printscreen") and command_window_screenshot (what happens with "alt+printscreen"). Change the values on the right and add for example "--delay=3" or "-d 3" at the end to set a 3 second delay. I don't know how fast this is implemented, it may require to login again. For more screenshot options run "gnome-screenshot --help" in a terminal. I like "gnome-screenshot -i": it brings a little dialog where you can choose your options.

---

