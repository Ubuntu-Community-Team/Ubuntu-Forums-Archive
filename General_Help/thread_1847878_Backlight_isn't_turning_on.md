---
title: "Backlight isn't turning on"
date: 2011-09-21
forum: General Help
---

### Post by metalmine on 2011-09-21
Dear Linux community,
     I am new to the OS and I have just installed it as dual-boot on my laptop. However, whenever I boot into Ubuntu(the latest version) the OS works perfectly except from the fact that I can only see if i squint my eyes since the Backlight isn't turned on no matter what I try. 

Sincerely and not an idiot,
Metalmine

---

### Post by sammiev on 2011-09-21
Hi metalmine, have you tried hitting the Ctrl and F7 buttons at the same time? Well the Ctrl button is down just keep tapping F7 until your back light is bright enough. :)

---

### Post by metalmine on 2011-09-21
> **sammiev said:**
> Hi metalmine, have you tried hitting the Ctrl and F7 buttons at the same time? Well the Ctrl button is down just keep tapping F7 until your back light is bright enough. :)

I will try right now. Thank you.

---

### Post by sammiev on 2011-09-21
> **metalmine said:**
> I will try right now. Thank you.

Sorry... It's the Fn and F7 button. :( Give this a try and post back. :)

---

### Post by patryk77 on 2011-09-21
> **sammiev said:**
> Sorry... It's the Fn and F7 button. :( Give this a try and post back. :)

This actually depends on the laptop's model...

On my Sorny Vaio it's Fn+F5/F6 to decrease/increase brightness.

Look for a little sun or a lightbulb in a different color (mine are blue, the same color as the Fn key)

Also, check under System/Preferences/Power Management. There are options there to set the brightness settings.

If none of those help, open a terminal and post the output of
sudo lshw

This will give a list of the hardware on your machine.

Also, a description of your laptop would be helpful.

On a slightly unrelated note, you should take a look at this to know not to run commands blindly (but don't worry, lshw is safe):
[http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54)

And finally, welcome to the forums and Ubuntu :)

---

### Post by metalmine on 2011-09-21
Thanks ill try :)

---

### Post by metalmine on 2011-09-21
oh wait..........a minute.....whats a terminal? @patrik77

---

### Post by patryk77 on 2011-09-21
The Terminal is like the Command Prompt in Windows.

Under Gnome it would be in the Applications / Accessories / Terminal menu. In Unity (the default interface in Ubuntu 11.04) I have no idea where it is, but in the menu somewhere.

---

### Post by metalmine on 2011-09-22
> **patryk77 said:**
> The Terminal is like the Command Prompt in Windows.

Under Gnome it would be in the Applications / Accessories / Terminal menu. In Unity (the default interface in Ubuntu 11.04) I have no idea where it is, but in the menu somewhere.

I can't edit grub with gedit... :( and i forgot my root password :(

---

### Post by Quackers on 2011-09-22
You won't need your root password, just your user password.
What hardware is this on?

---

