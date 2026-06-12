---
title: "Question about KDE and Xubuntu..."
date: 2009-08-07
forum: General Help
---

### Post by knightrider37876 on 2009-08-07
I'm new to Linux and apologize for asking a noobish question. I was looking on [http://kde.org/announcements/4.2/guide.php](http://kde.org/announcements/4.2/guide.php) and the new Xubuntu has some pretty cool graphics and widgets. I installed Xubuntu and mine looks nothing like that. So apparently I need to install KDE? What do I need to do in order to have the cool plasma effects and widgets? Any help would be greatly appreciated!

---

### Post by jaxxstorm on 2009-08-07
You've confused Xubuntu and Kubuntu.

Xubuntu, that you've installed uses the XFCE desktop environment.

Kubuntu, which you need uses the KDE desktop environment.

you can get kubuntu from [here]("http://www.kubuntu.org/")

---

### Post by knightrider37876 on 2009-08-07
Wow... I feel like a complete idiot now. Is there a big difference between the two operating systems besides the GUI?

---

### Post by Universal344 on 2009-08-07
Not to my knowledge, they should all have the same Ubuntu base to them.  However, the default software installed will be different depending on what software is bundled with the desktop environment you're using.  But they all use the same Ubuntu repos so you can reinstall any software you want that isn't bundled.

---

### Post by knightrider37876 on 2009-08-07
So by downloading the newest copy of *Kubuntu*, it should have the new GUI, widgets, etc? What do you mean by repos? I've got a lot to learn about Linux...

---

### Post by martinbaselier on 2009-08-07
the only difference is the desktop environment (DE)

The DE has it's own gui, windows manager and several other tools. You can add a different DE easily. Each of them also have their own libraries for handling graphics and other things, like automount, their own file browser, etc. 

**sudo apt-get install kubuntu-desktop**

When you login, you can then choose kde as the desktop for your current session. 

The two big DEs are gnome and kde. There are also a number of smaller ones. xfce is probably the biggest of them, then come lxde, e17 and a lot of other ones. 

For more info:
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

---

### Post by pmlxuser on 2009-08-07
you can download or if you have already installed xubuntu/ubuntu

you can actually just do

```

$ sudo apt-get install kubuntu-desktop

```

after that you shall have the cool plasm GUI, widgets, etc.

repos mean repository its a place a server (number of servers actually) which host a whole lot of ubuntu software

---

### Post by knightrider37876 on 2009-08-07
Thanks to everyone for replying. That is good to know about the "sudo apt-get install kubuntu-desktop" command. I will try that out. Any other advice for a newbie starting out on Linux?

---

### Post by Universal344 on 2009-08-07
Installing the kubuntu-desktop package will work, but realize that doing so will leave you with a full XFCE (Xubuntu's desktop environment) as well.  Also, if you do just install kubuntu-desktop, it will probably ask you what you want the default display manager to be.  Select KDM if you want KDE's login screen.

---

