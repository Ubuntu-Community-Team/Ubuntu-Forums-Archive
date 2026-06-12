---
title: "GIMP 2.8 does not show in 12.04 Laucher or Alt-Tab when Open"
date: 2012-05-09
forum: General Help
---

### Post by Donalb on 2012-05-09
I updated GIMP to 2.8 as one fo the first tasks after installing 12.04 yesterday.

When GIMP is opened it doesn't show in the Launcher NOR does it show when I use Alt+Tab to cycle through open apps. In fact if I was to Display Desktop  GIMP will no longer be visible.

---

### Post by zboubi on 2012-05-09
same here with a fresh 12.04 install

---

### Post by eulu on 2012-05-09
same here.. ubuntu 12.04 64-bit.. (Uninstalled 2.6 and installed 2.8.. )

---

### Post by wilee-nilee on 2012-05-09
You all can reset unity to the stock install state try that.

alt-f2 then type unity --reset

can be run in the terminal as 

```
unity --reset & exit
```

---

### Post by eulu on 2012-05-09
awesome thanks!

---

### Post by Donalb on 2012-05-10
Unity reset also works for me. Marked as solved. Thanks!

---

### Post by eulu on 2012-05-11
The unity reset works temporarily, however the problem returns after a system restart. Not the ideal situation to have to reset unity and redo desired user settings after every reboot..

---

### Post by deallas on 2012-05-12
I have the same problem with Mysql Workbench

---

### Post by fragos on 2012-05-12
Just a matter of note, the name of the GIMP executable in 12.04 is gimp-2.6 and you may need to change the gimp.desktop file to execute gimp-2.8. You'll find that .desktop file in /usr/share/applications. You won't see any file names in nautilus that end in .desktop. Do an Alt-F2 and type:

    gksudo gedit /usr/share/applications/gimp.desktop

Now you'll be able to view and edit this file if necessary. the lines you want to examine are:

    Exec=gimp-2.8 %U
    TryExec=gimp-2.8

They should be 2.8 as above but may still be 2.6 in which case you should change them. If you edited it, open nautilus /usr/share/applications, find the gimp launcher and drag it to the launch bar -- your done.

---

### Post by rkrdo on 2012-05-22
> **fragos said:**
> Just a matter of note, the name of the GIMP executable in 12.04 is gimp-2.6 and you may need to change the gimp.desktop file to execute gimp-2.8. You'll find that .desktop file in /usr/share/applications. You won't see any file names in nautilus that end in .desktop. Do an Alt-F2 and type:

    gksudo gedit /usr/share/applications/gimp.desktop

Now you'll be able to view and edit this file if necessary. the lines you want to examine are:

    Exec=gimp-2.8 %U
    TryExec=gimp-2.8

They should be 2.8 as above but may still be 2.6 in which case you should change them. If you edited it, open nautilus /usr/share/applications, find the gimp launcher and drag it to the launch bar -- your done.

I have it like that in my .desktop file but it still won't show up gimp, unity --reset did the trick

---

### Post by Scoobin on 2012-05-22
unity --reset did not work at all for me, even without rebooting.

---

