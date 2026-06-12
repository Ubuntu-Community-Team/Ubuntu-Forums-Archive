---
title: "the error of installing software that written in python"
date: 2010-07-01
forum: General Help
---

### Post by hua_ on 2010-07-01
for example,i want to install a texteditor  called Editra,i done it like the following

first, i install the Editra

sudo apt-get install Editra  - success ,its version is 0.5.30

second,i run it in Terminal

Editra - it can work,but with the error infos "(python:1682): Gtk-CRITICAL **: gtk_widget_add_accelerator: assertion `GTK_IS_WIDGET (widget)' failed"

third,i used command line "dpkg -L Editra", and found that the Editra is installed under /usr/share/pyshared/Editra,so i created the .desktop like this

sudo gedit /usr/share/applications/Editra.desktop 

[Desktop Entry]
Encoding=UTF-8
Name=Editra
Comment=the Best TextEditor
Exec=/usr/share/pyshared/Editra
Icon=/usr/share/pyshared/Editra/pixmaps/editra.png
Terminal=false
Type=Application
Catergories=Development

it showed, and i clicked it for running,but it told me error infos

Could not launch 'Editra'
Failed to execute child process "/usr/share/pyshared/Editra" (Permission denied)

not just Editra,so many software that written in python have the same question,such as tortoisehg...

so ,can anybody fix this for me?

---

### Post by flick on 2010-07-01
Most executables in Linux distros are found in /usr/bin/

for editra :

/usr/bin/editra

I just installed editra and ran it from the terminal using the above line, seems to run fine.

---

### Post by hua_ on 2010-07-02
thanks for your answer
i think i can run it on command line
but i can not run it by /usr/share/pyshared/Editra

---

