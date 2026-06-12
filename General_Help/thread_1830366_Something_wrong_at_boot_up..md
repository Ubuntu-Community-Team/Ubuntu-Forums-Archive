---
title: "Something wrong at boot up."
date: 2011-08-21
forum: General Help
---

### Post by kensclark15 on 2011-08-21
I just wiped my hard drive and installed Ubuntu 11.04, nothing else. Whenever my computer starts up I get the HP screen then it goes black and says "Resolution Mismatch." Is something wrong with the bootloader? Everything works fine after that. Also, When I open Terminal it shows that it's open but I can't find it. It's like it's invisible. And sometimes the red "x" button on some windows disappear.

---

### Post by kensclark15 on 2011-08-21
I don't know if this is a good or bad thing.

---

### Post by Thewhistlingwind on 2011-08-21
Functionality disappearing is a bad thing, almost certainly. 

[http://ubuntuforums.org/showthread.php?t=1031844](http://ubuntuforums.org/showthread.php?t=1031844)

Whats your screen resolution?

---

### Post by WyleECoyote on 2011-08-21
could be boot resolution is too low, try editing grub like this:

```
gksudo gedit /etc/default/grub
```

add this:

```
GRUB_CMDLINE_LINUX="splash [color=#FF0000]vga=795[/color]"
```

then:

```
sudo update-grub
```

here is list of resolution:
[https://help.ubuntu.com/community/BootText](https://help.ubuntu.com/community/BootText)

just find what works best with your monitor

---

### Post by kensclark15 on 2011-08-21
My resolution is 1360 x 768

---

### Post by kensclark15 on 2011-08-21
I edited grub and when I closed the window, this was in the terminal:
```
kenneth@kenneth-AY652AA-ABA-s5310y:~$ gksudo gedit /etc/default/grub

(gedit:2620): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.6TUU0V': No such file or directory

(gedit:2620): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2620): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.YQ340V': No such file or directory

(gedit:2620): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```
And on a lot of folders it says I'm not the owner so I can't use them? wth.

---

### Post by WyleECoyote on 2011-08-21
please forgive the late reply I am trying to setup my other comp and been busy, but...

as far as I can tell they are only warnings, and look to me like temp files I usually just ignore them myself but maybe someone knows the fix.

for your resolution I would do vga=792

what folders are you getting complaints from? and can you take screenshot or copy paste into code block here so we can see what may be the problem.

---

