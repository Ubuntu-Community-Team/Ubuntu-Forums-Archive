---
title: "rdesktop fullscreen mode in gnome"
date: 2010-02-24
forum: General Help
---

### Post by capybara! on 2010-02-24
Dear all,

I just installed Ubuntu Karmic X86 and have some trouble with the full screen mode in rdesktop. From gnome-display-properties, I know that my screen resolution is 1280x1024 (5:4). Before, it always worked with 
```
rdesktop -D -K -g 1024x576 -z server.com
```
or with 
```
rdesktop -g 100% server.com
```
But when using those commands, I still have now the top and bottom panel of my gnome desktop.

When I use 
```
rdesktop server.com -f
```

I get into fullscreen mode, but I can only exit with ctrl+alt+return or something like that. In my previous installation (Hardy), I could easily switch between two dektops with ctr+alt+right and ctr+alt+left, like as usual in gnome, with one desktop running regular gnome and the other one running rdesktop in fullscreen mode. 

Does anyone know a solution for that?

Thanks in advance..

---

