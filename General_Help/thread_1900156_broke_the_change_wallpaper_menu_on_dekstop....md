---
title: "broke the change wallpaper menu on dekstop..."
date: 2011-12-25
forum: General Help
---

### Post by Adrianzo on 2011-12-25
I've been uninstalling software and libraries... and I might have removed something that I shouldn't have.

(i.e. Acurl)

does anyone knows how to correct this? When I go to change desktop background the window in the screenshot popups... <see attachment>

Thx.

---

### Post by gandaran on 2011-12-25
try
```
sudo apt-get install lubuntu-desktop
```
(if its lubuntu you have)

---

### Post by Adrianzo on 2011-12-25
yes, I've lubuntu.

Is there any log of the sudo apt-get remove commands I've done this afternoon? that could help me.

PS: after reboot the 'change desktop wallpaper' menu is working again. Anyway CAN I see a LOG of all the shell commands I've Run? Or can I enable one? (for future problems) Thx!

---

### Post by amjjawad on 2011-12-30
Sorry for the late reply, I got your PM but I've been sick and still with slow recovery. I'll do my best though.

When you are on LXTerminal, use your cursor key (Up) and that will give you the last command you ran. You can do that again to see the other previous command, etc.

---

### Post by Dennis N on 2012-01-05
> **Adrianzo said:**
> yes, I've lubuntu.

Is there any log of the sudo apt-get remove commands I've done this afternoon? that could help me.

PS: after reboot the 'change desktop wallpaper' menu is working again. Anyway CAN I see a LOG of all the shell commands I've Run? Or can I enable one? (for future problems) Thx!

Probably too late for this time, but for future use:

To see the recent (last several hundred) commands entered into the terminal, just type **history** at the command prompt. They are all numbered. To execute any of them, use the list number preceded by an exclamation mark.

Example: to run the 370th command in the list, type **!370**

If you want a printed list, typing: 

**history > ~/command-list.txt**

will create a file 'command-list.txt' of the output saved to your home folder.

---

