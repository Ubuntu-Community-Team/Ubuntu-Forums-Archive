---
title: "Running a new X window made Nautilus all funky (picture included)"
date: 2012-02-13
forum: General Help
---

### Post by chousho on 2012-02-13
Hey!
So I was looking at how to run a new X window to play games at full screen, to avoid having them affect currently opened programs.

I ran this command:
```
sudo xinit ~/desura/desura %U -- :1
```

Which opened up a new window. However ctrl+alt+F7 brought me back to my original X window which now looks like this:
[[IMG]http://i.imgur.com/ZfYuKl.jpg[/IMG]](http://i.imgur.com/ZfYuK.jpg)
The icons are gone, the folder tabs are pretty ugly, and it seems familiar to when I tried to run Firefox on KDE (which I think was a GTK issue?).

How do I go about getting the theme for Nautilus back to how it should look (default, look)?

---

### Post by papibe on 2012-02-13
Looks like the same problem. Take a look at [this]("http://ubuntuforums.org/showthread.php?t=1920006").

Regards.

---

### Post by HiImTye on 2012-02-13
you might have made root take over some of your files. to fix it try
```
sudo chown -R <yourusername> /home/<yourusername>/
```

---

### Post by chousho on 2012-02-13
> **papibe said:**
> Looks like the same problem. Take a look at [this]("http://ubuntuforums.org/showthread.php?t=1920006").

Regards.
Ah, the killall nautilus worked! Thank you <333

> **HiImTye said:**
> you might have made root take over some of your files. to fix it try
```
sudo chown -R <yourusername> /home/<yourusername>/
```

Thanks for the help, too! When I tried that, it threw:
```
chown: cannot access `/home/chousho/.gvfs': Permission denied
```
So I wasn't exactly sure.

Thank you both :)

---

### Post by HiImTye on 2012-02-13
> **chousho said:**
> ```
chown: cannot access `/home/chousho/.gvfs': Permission denied
```
.gvfs are network shares you have mounted, so no worries about permissions there, they should be set dynamically

edit: they could also be locked out if you still have the other one loaded *and* have network shares mounted there, I guess youll find out lol

---

