---
title: "How to make Ubuntu recognize my alt key as alt and not as iso_level3_shift"
date: 2011-01-03
forum: General Help
---

### Post by not_the_geekiest on 2011-01-03
I tried using ```
xmodmap -e "keycode 108 = AltR"
``` (and 64 for the left alt) in order to change the key but I would only be able to do key combinations (alt-shift) with the right alt key and when I restated my computer it would go back to how it was before. How can I make Ubuntu recognize my alt key as alt and not as iso_level3_shift and have it stay that way?

---

### Post by TeoBigusGeekus on 2011-01-03
You can save the command as a script, make it executable and add it to your startup scripts.

---

### Post by not_the_geekiest on 2011-01-03
> **TeoBigusGeekus said:**
> You can save the command as a script, make it executable and add it to your startup scripts.

How would I do that?
If I where to do that I would still have the problem with my left alt key.

---

### Post by TeoBigusGeekus on 2011-01-03
```
#!/bin/bash
xmodmap -e "keycode 108 = AltR"
xmodmap -e "keycode 64 = AltL"
```
Save this into a file in your home folder with any name you want, lets say altscript.
Make it executable
```
chmod +x ~/altscript
```
Go to Administration>Preferences>Startup applications and create a new entry.
Name it whatever you want and give as its command
```
sh /home/yourusername/altscript
```
Reboot and you should be fine.

---

### Post by not_the_geekiest on 2011-01-03
should I really include the # before !/bin/bash?

---

### Post by TeoBigusGeekus on 2011-01-03
> **not_the_geekiest said:**
> should I really include the # before !/bin/bash?

Yes.

---

### Post by not_the_geekiest on 2011-01-03
I tried that and it didn't work. However, when manually entering the command into the terminal it works.

Ps. I made a mistake it is Alt_R not AltR, but I changed that in the file.

---

### Post by TeoBigusGeekus on 2011-01-03
Change AltL to Alt_L too.

---

### Post by not_the_geekiest on 2011-01-04
Yes I did that.

I have an executable file named "altscript" located in my home folder with the code ```
#!/bin/bash
xmodmap -e "keycode 108 = Alt_R"
xmodmap -e "keycode 64 = Alt_L"
```
in it. I also have under system > preferences > startup applications an application that runs "sh /home/my_name/altscript".

Did I do something wrong?

---

