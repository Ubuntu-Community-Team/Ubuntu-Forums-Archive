---
title: "Make firefox use &quot;different file manager&quot; when opening download folder from firefox"
date: 2012-07-07
forum: General Help
---

### Post by Tigerbloodz on 2012-07-07
I'm running Ubuntu but I'm using fluxbox so I have to run nautilus as  "nautilus --no-desktop" so it won't take screw over fluxbox.

How do I make it so after downloading something in firefox, when I  right-click and use "open containing folder" make it use "nautilis  --no-desktop".

*I  hope this is posted in the right forum.*

---

### Post by Dilyan on 2012-07-07
I am not sure if this will help, but this is the voodo applied by KDE folk to use Dolphin instead of Nautilus.

In the console, see what this will show:
```
cat /usr/share/applications/defaults.list | grep inode
```
Most probably, it will show:
```
inode/directory=nautilus.desktop
```
Now, open the file in your editor (in this example, /usr/share/applications/nautilus.desktop) as root, and modify the section
```
Exec=nautilus
```
to show
```
Exec=nautilus --no-desktop
```
instead.

I would be curious if this actually works for somebody :D

---

### Post by Tigerbloodz on 2012-07-07
Thank you, that did the trick!

---

### Post by Tigerbloodz on 2012-07-09
I also have the same issue with Transmission. Any ideas on that (*I thought the solution would work for everything)*?

---

### Post by Tigerbloodz on 2012-07-09
It seems after a reboot this solution no longer works, for some reason. The file still says nautilus --no-desktop but it's just not working like it did before the reboot.

---

