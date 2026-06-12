---
title: "Terminal size using nautilus-open-terminal"
date: 2010-05-06
forum: General Help
---

### Post by Alex Farber on 2010-05-06
I managed to set default terminal size when it is executed from the menu, by editing Launcher Properties command line:
gnome-terminal --geometry 132x43

Is it possible to do the same when terminal window is executed by nautilus-open-terminal from context menu?

---

### Post by dcstar on 2010-05-06
> **Alex Farber said:**
> I managed to set default terminal size when it is executed from the menu, by editing Launcher Properties command line:
gnome-terminal --geometry 132x43

Is it possible to do the same when terminal window is executed by nautilus-open-terminal from context menu?

The terminal is opened with the default profile, simply change the default profile if you always want to open in that size.

---

### Post by akakingess on 2010-05-06
> **dcstar said:**
> The terminal is opened with the default profile, simply change the default profile if you always want to open in that size.

Thanks for the tip dcstar, would you mind telling me where/which config file is the one to edit for the terminal?

---

### Post by false_chicken on 2010-05-06
Open a terminal and select Edit > Profile Preferences

---

### Post by akakingess on 2010-05-06
Dang, that makes me feel like I can't see the forest through the trees!!! ;)

---

### Post by philinux on 2010-05-06
> **akakingess said:**
> Dang, that makes me feel like I can't see the forest through the trees!!! ;)

It's new in lucid.

---

### Post by akakingess on 2010-05-06
> **philinux said:**
> It's new in lucid.

Whew, thank goodness, that makes me feel a little less stupid ;)

---

### Post by Alex Farber on 2010-05-06
I don't see how terminal size can be changed in the Profile Preferences dialog (Ubuntu 9.10).

---

### Post by akakingess on 2010-05-06
> **Alex Farber said:**
> I don't see how terminal size can be changed in the Profile Preferences dialog (Ubuntu 9.10).

As Philinux stated in the post before yours, it is new in 10.04...

---

### Post by philinux on 2010-05-06
> **Alex Farber said:**
> I don't see how terminal size can be changed in the Profile Preferences dialog (Ubuntu 9.10).

Previous releases used to remember if you changed it by resizing the window. But with Karmic I think you had to resort to the terminal, no pun intended.

```
gksudo gedit /usr/share/vte/termcap/xterm

Line 10
```

---

### Post by akakingess on 2010-05-06
BTW, @ Alex Farber, I didn't mean for my response to you to sound rude, it's just really early and the kids are already giving me a headache ;)

---

### Post by mcduck on 2010-05-06
> **Alex Farber said:**
> I don't see how terminal size can be changed in the Profile Preferences dialog (Ubuntu 9.10).

In 9.10 and older versions your best option is to change the terminal command in System/Preferences/Preferred Applications and add the --geometry" option to the command. That allows you to set the default size & location for the terminal.

---

### Post by Alex Farber on 2010-05-06
Thanks to all, editing /usr/share/vte/termcap/xterm file solved the problem. Good to know also about Preferred Applications.

---

### Post by tommpogg on 2010-05-19
I could not change the terminal default size by editing /usr/share/vte/termcap/xterm in Ubinti 9.10.

I opened the file using gvim and edited the line :co#80:it#8:li#24:\ but nothing happened.
Can anyone tell why?

By the way, the solution System/Preferences/Preferred Applications worked fine!

---

### Post by wojox on 2010-05-19
Did you close every terminal? What parameters did you set it to? Remember just change the first and last number.

---

