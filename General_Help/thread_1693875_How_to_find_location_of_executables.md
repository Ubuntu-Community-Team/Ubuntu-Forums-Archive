---
title: "How to find location of executables?"
date: 2011-02-23
forum: General Help
---

### Post by W-Unit on 2011-02-23
Hi there, *nix noob here

I just installed the xubuntu-desktop package on my netbook (running UNR), and I've got one major complaint about xfce.
I can't right-click on icons in the Applications menu and add them to the launcher!
Instead I have to know the location of the executable for the application, so that I can right-click the panel, add a launcher, and then type the location of the executable in and manually select an icon for it... what a pain.
Of course it probably wouldn't be a pain if I could find everything. In Windows, if I want to know the location of a program that's running, I just open Task Manager, right-click the application, and select Properties. Is there some equivalent or command-line way of finding the location of a running application in Linux?

A few I'd like to know the location of are:
1) Gnome System Monitor
2) Terminal
3) Swiftfox
... and I'll probably think of others.


Even though I'm using XFCE, I figured this fell under the "all variants" category since my main question is just how to find the locations of executables... sorry if it's mis-filed.

Thanks for any help!! :)

---

### Post by TeoBigusGeekus on 2011-02-23
```
which nameofprogram
```
will give you the location of the executable of the program

---

### Post by Habitual on 2011-02-23
edited for dorkness. :)

---

### Post by W-Unit on 2011-02-23
Thanks :)

What about the terminal? **which Terminal** doesn't seem to give me anything....

---

### Post by cariboo on 2011-02-23
That's because there is no program named terminal. Almost all the executables are located in /usr/bin. I don't have Xubuntu installed on anything at the moment, but I believe it uses rxvt for a terminal.

---

### Post by TeoBigusGeekus on 2011-02-23
Cause there probably isn't any program called terminal.
If you use gnome terminal
```
which gnome-terminal
```
If you use xterm
```
which xterm
```
and so on.

---

### Post by Vaphell on 2011-02-23
you can try ```
locate <keyword> | grep /usr/bin
```

it will find all items with <keyword> in name and filter out everything that is not in /usr/bin. Of course it won't help if the keyword is completely unrelated to the name of file.

---

### Post by TeoBigusGeekus on 2011-02-23
*

---

