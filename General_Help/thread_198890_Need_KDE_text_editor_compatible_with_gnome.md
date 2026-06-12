---
title: "Need KDE text editor compatible with gnome"
date: 2006-06-17
forum: General Help
---

### Post by OBnascar on 2006-06-17
I have one work computer with Ubuntu 6.06 and another one with Kubuntu 6.06. I want to copy text files from one computer to the second computer using a USB 2.0 flash drive. I did not realize Kate was not compatable with the gnome text editor.

What can I do to resolve this ? Is there a text editor that is compatible in KDE and  gnome ?

---

### Post by weijie90 on 2006-06-17
> I want to copy text files from one computer to the second computer using a USB 2.0 flash drive.

I don't see how a simple text file can be incompatible among kate and gedit.

---

### Post by aysiu on 2006-06-17
Of course, they're compatible. I've used Mousepad, Kate, Kwrite, and Gedit on the same text file before.

A text file is a text file. Hell, I've used Windows' Notepad on a file I've created with Kate. There's no need for compatibility. If it ends with a .txt extension, any text editor can edit it.

It sounds more like permissions issues to me than "compatibility."

---

### Post by OBnascar on 2006-06-17
[QUOTE=weijie90]I don't see how a simple text file can be incompatible among kate and gedit.[/QUOTE]

I agree, and that is why it surprised me. Maybe there is something else wrong ? But I surely would not know what it would be !

---

### Post by aysiu on 2006-06-17
[QUOTE=OBnascar]I agree, and that is why it surprised me. Maybe there is something else wrong ? But I surely would not know what it would be ![/QUOTE]
You probably just don't have permission to edit the file. Can you *cd* to the directory where it is and then post back here the output of this command? ```
ls -al
```

For example, if your text file were called *blahblahblah.txt* and it was on your desktop: ```
cd ~/Desktop
ls -al
``` Then post back the line that includes *blahblahblah.txt*.

---

### Post by scxtt on 2006-06-17
> Need KDE text editor compatible with gnome[size=5]vi[/size]

[size=1]sorry, couldn't resist[/size] ...

---

### Post by OBnascar on 2006-06-17
This is embarrassing, but I tried  a different USB 2.0 flash drive and now it works ! 

I will check out the other drive tomorrow and see what the deal was with it.

thanks all

---

### Post by Patrick-Ruff on 2006-06-18
Vi is a pain in the *** to use if I may say so.

---

### Post by scxtt on 2006-06-18
[QUOTE=Patrick-Ruff]Vi is a pain in the *** to use if I may say so.[/QUOTE]i'm inclined to disagree ... i can see why people dislike it, but if you're using vim, it can be one of the fastest ways to edit text files ... you just have to use it enough, maybe not always use a GUI environment ...

---

### Post by NoWhereMan on 2006-06-18
you should tell us what you mean with "not compatible". I don't think is a permission issue, because usb flash drives are vfat, and they don't store permissions... I guess it may be an encoding issue, maybe? kde expects the file to be iso-nnnn while gedit saves in utf? (that would be strange either, anyway...)

---

### Post by aysiu on 2006-06-18
[QUOTE=NoWhereMan]I don't think is a permission issue, because usb flash drives are vfat, and they don't store permissions... [/QUOTE] While FAT doesn't *store* permissions, it can deny you permissions if it's not mounted correctly.

---

