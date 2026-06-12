---
title: "Can not get to the Desktop, no GUI."
date: 2009-09-06
forum: General Help
---

### Post by pyjimbo on 2009-09-06
I can not get to my desktop, there is no GUI. The reason I think is here in this other thread, cross posting is not the intent because I want to go about this as a startup problem. Response time is too slow there, so can we go about this here as a startup problem?

[http://ubuntuforums.org/showthread.php?t=1259022](http://ubuntuforums.org/showthread.php?t=1259022)

**How can I edit Ubuntuone out of my boot/startup process?**

I tried failsafe mode but it didn't work.
[LIST]
[*]Failsafe session mode does not work via the login screen, I get the same result it just sits at the desktop.
[*]Failsafe mode selection via GRUB was removed with the startupmanager tool, I can not access it.
[/LIST]

Thank you for your patience in advance, I'm just super stuck.

---

### Post by NoaHall on 2009-09-06
1) Have you tried "Ctrl + alt + 1" then using "startx" (or just use a terminal if it comes up)

2) If that fails, use "top" to determine which process is Ubuntuone, then use "killall name" , for example "killall ubuntuone"

---

### Post by pyjimbo on 2009-09-06
> **NoaHall said:**
> 1) Have you tried "Ctrl + alt + 1" then using "startx" (or just use a terminal if it comes up)

2) If that fails, use "top" to determine which process is Ubuntuone, then use "killall name" , for example "killall ubuntuone"

I tried that, it doesn't work. The problem persists. Ubuntuone-client package has been removed but I still get stuck with no GUI, its weird. There is no ubuntuone process using *top*.

---

### Post by Scunizi on 2009-09-06
You might also try.. sudo /etc/init.d/gdm start .. if that doesn't work try installing the desktop again with sudo apt-get install ubuntu-desktop

---

### Post by NoaHall on 2009-09-06
I think it's called something like ubuntuone-client-applet.
So then it's "killall ubuntuone-client-applet"

Are you one hundred percent sure it's ubuntuone? Have you done anything recently to change your graphics cards drivers? What graphics card are you using?

---

### Post by pyjimbo on 2009-09-06
> **NoaHall said:**
> I think it's called something like ubuntuone-client-applet.
So then it's "killall ubuntuone-client-applet"

Are you one hundred percent sure it's ubuntuone? Have you done anything recently to change your graphics cards drivers? What graphics card are you using?

I tried to kill ubunutone-client-applet and there was no process for it.

All I get at the desktop is a notification in the top right corner that Ubuntuone is updating, or even finished updating.

I am using an nVidia 7600 on my desktop and Intel graphics on my Macbook. I have not touched the drivers in weeks since I did a fresh install.

---

### Post by pyjimbo on 2009-09-06
> **Scunizi said:**
> You might also try.. sudo /etc/init.d/gdm start .. if that doesn't work try installing the desktop again with sudo apt-get install ubuntu-desktop

None of those techniques worked.

---

### Post by NoaHall on 2009-09-06
Try installing the kde interface and trying to see if it's the same perhaps?

---

### Post by pyjimbo on 2009-09-06
> **NoaHall said:**
> Try installing the kde interface and trying to see if it's the same perhaps?

When I log into KDE it shows the gray KDE background, then it pops to the orange Ubuntu background I was using in Gnome, then I'm stuck like before.

---

### Post by pyjimbo on 2009-09-06
I am going to reformat my machines after I backup data. Not much on them anyway.

Thanks for your help.

---

