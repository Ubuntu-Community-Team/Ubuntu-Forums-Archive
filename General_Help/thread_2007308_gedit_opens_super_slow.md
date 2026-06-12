---
title: "gedit opens super slow"
date: 2012-06-20
forum: General Help
---

### Post by mathiflip on 2012-06-20
hi,

I'm using ubuntu 12.04 with unity. For the last few weeks when opening a simple textfile in gedit, it opens extremely slow. 10-15 seconds is no exception.

I googled for a solution and found this:
```
http://ubuntuforums.org/showthread.php?t=938208
```But this solution doesn't work for me.

If I open just gedit, for example from dash, it opens instantly. But when I right click on a textfile and open it with gedit, it's soooooo slow.

I hope someone can help me out.

Thanks alot,

---

### Post by spikoley on 2012-06-20
Open gedit from the Terminal.  It might show some errors in the Terminal.  If it does, post them here.

```
gedit
```

---

### Post by mathiflip on 2012-06-22
thanks for the reply spikoley,

However opening gedit from terminal gives no errors. And it opens instantly.
I also tried opening a file in gedit from terminal

```
gedit cv.tex
```

And it also opens instantly without errors.
Then I went to the documents folder in Nautilus, and I try to open the tex file from there with gedit, and then it opens sloooooow again.

It seems it's only a problem when I open a file from the GUI.

---

### Post by spikoley on 2012-06-22
I have no idea what it could be.  Since plugins have been known to cause this issue, I think it's worth a shot playing around with them.

My gedit opens fine from Nautilus.  Here are the 5 plugins I have checked:

Document Statistics
File Browser Panel
Insert Date/Time
Modelines
Spell Checker

Try checking and unchecking them to see if it makes a difference.  Other than that, I have no idea what else to try.

---

### Post by mathiflip on 2012-07-02
First of all, sorry for the late answer.

I turned all the plugins off and still the problem occurs.
I think I got to get used to it.

Thanks anyway!

---

### Post by cortman on 2012-07-02
> **mathiflip said:**
> First of all, sorry for the late answer.

I turned all the plugins off and still the problem occurs.
I think I got to get used to it.

Thanks anyway!

In a terminal run

```
cat /usr/share/applications/gedit.desktop
```

Post the output here. Thanks!

---

### Post by mathiflip on 2012-07-06
```

[Desktop Entry]
Name=gedit
GenericName=Text Editor
Comment=Edit text files
Keywords=Plaintext;Write;
Exec=gedit %U
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
Icon=accessories-text-editor
Categories=GNOME;GTK;Utility;TextEditor;
X-GNOME-DocPath=gedit/gedit.xml
X-GNOME-FullName=Text Editor
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.4.1
X-GNOME-Bugzilla-ExtraInfoScript=/usr/share/gedit/gedit-bugreport
Actions=Window;Document;
X-Ubuntu-Gettext-Domain=gedit

[Desktop Action Window]
Name=Open a New Window
Exec=gedit --new-window
OnlyShowIn=Unity;

[Desktop Action Document]
Name=Open a New Document
Exec=gedit --new-window
OnlyShowIn=Unity;

```

---

### Post by mathiflip on 2012-08-09
I'm still having this problem. Any ideas?

---

