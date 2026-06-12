---
title: "Running a command system wide to fix RGBA problem"
date: 2010-02-22
forum: General Help
---

### Post by themusicalduck on 2010-02-22
I'm trying to run a command that will let me run some programs. If I run the command in a terminal, then I can launch the programs from it fine, but not from anywhere except that terminal. This is the command that makes things work:```
export GTK_RGBA_APPS=allbut:exe:checkgmail:swiftfox:firefox
```

This command disables RGBA for the programs listed, which seem to have problems with it. I hoped I could use this command to somehow apply it system wide permanently. I've tried adding it /etc/rc.local and rebooting, but it doesn't work.

I installed RGBA with the guide here [http://www.omgubuntu.co.uk/2010/02/enable-rgba-window-transparency-in.html](http://www.omgubuntu.co.uk/2010/02/enable-rgba-window-transparency-in.html)

Is there a way of doing this? Or am I barking up the wrong tree entirely? Is there a better way to disable RGBA for certain programs?

---

### Post by skymera on 2010-02-22
```
 gedit ~/.profile 
```

copy this into the file

```
export GTK_MODULES=rgba
export GTK_RGBA_APPS=allbut:firefox:firefox-3.5:gksudo:ooffice:soffice 
```

[https://wiki.ubuntu.com/DesktopTeam/LucidRgbaGtk](https://wiki.ubuntu.com/DesktopTeam/LucidRgbaGtk)

I found using Firefox-3.5 didn't work, i added firefox-bin instead.
Banshee also doesn't work with RGBA

---

### Post by mcduck on 2010-02-22
You could just try adding the applications you wish to run without RGBA colors into the Window Rules-plugin in Compiz settings.. :)

---

### Post by themusicalduck on 2010-02-22
Great! Thanks Skymera, your suggestion worked.

---

