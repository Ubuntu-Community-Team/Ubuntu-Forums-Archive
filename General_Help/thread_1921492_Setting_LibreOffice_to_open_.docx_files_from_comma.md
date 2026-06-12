---
title: "Setting LibreOffice to open .docx files from command line"
date: 2012-02-06
forum: General Help
---

### Post by Kissell on 2012-02-06
Anyone know how to setup Libre Office to open .docx files from the command line?

It is annoying that it won't open word documents by default, and I know I can fix it by right-clicking on them and choosing the program to open them...  but I want to script this so that next time I install Ubuntu it is set correctly without the user having to reconfigure it.

---

### Post by forrestcupp on 2012-02-06
I can't get you all the way there, but [this web site is a good start](http://www.johannes-eva.net/change-the-default-application-ubuntu-linux). You need to figure out a way to edit from a script **/usr/share/applications/default.list**.

This may or may not be the line in my default.list that associates .docx with Writer:
```
application/msword=libreoffice-writer.desktop
```

---

### Post by Kissell on 2012-02-06
That'll do it, I just didn't know where that folder was.

this line will add the correct code from a script to get libre office to open .docx files.

> echo "application/docx=libreoffice-writer.desktop" >> /usr/share/applications/defaults.list

Thanks, couldn't have done it without your help.

---

### Post by Kissell on 2012-02-06
I went ahead and did the code for a bunch more four-letter office extensions...  in case anyone else finds this useful.

```

echo "application/docm=libreoffice-writer.desktop" >> /usr/share/applications/defaults.list
echo "application/dotx=libreoffice-writer.desktop" >> /usr/share/applications/defaults.list
echo "application/dotm=libreoffice-writer.desktop" >> /usr/share/applications/defaults.list
echo "application/xlsx=libreoffice-calc.desktop" >> /usr/share/applications/defaults.list
echo "application/xlsm=libreoffice-calc.desktop" >> /usr/share/applications/defaults.list
echo "application/xltx=libreoffice-calc.desktop" >> /usr/share/applications/defaults.list
echo "application/xltm=libreoffice-calc.desktop" >> /usr/share/applications/defaults.list
echo "application/xlsb=libreoffice-calc.desktop" >> /usr/share/applications/defaults.list
echo "application/xlam=libreoffice-calc.desktop" >> /usr/share/applications/defaults.list
echo "application/xll=libreoffice-calc.desktop" >> /usr/share/applications/defaults.list
echo "application/pptx=libreoffice-impress.desktop" >> /usr/share/applications/defaults.list
echo "application/pptm=libreoffice-impress.desktop" >> /usr/share/applications/defaults.list
echo "application/potx=libreoffice-impress.desktop" >> /usr/share/applications/defaults.list
echo "application/potm=libreoffice-impress.desktop" >> /usr/share/applications/defaults.list
echo "application/ppam=libreoffice-impress.desktop" >> /usr/share/applications/defaults.list
echo "application/ppsx=libreoffice-impress.desktop" >> /usr/share/applications/defaults.list
echo "application/ppsm=libreoffice-impress.desktop" >> /usr/share/applications/defaults.list

```

---

### Post by forrestcupp on 2012-02-07
Have you tested it yet on a system that didn't have the defaults set, and did it work?

---

### Post by Kissell on 2012-02-07
I only tested the .docx files.  
The regular Ubuntu 11.10 64-bit OS didn't open .docx files by default.
adding the first line of code listed above did fix that.  I'm fairly certain then that the others work too, although I don't have any of those other types of files, just the docx.

---

### Post by mkeyes001 on 2012-02-09
so this maybe a silly question, but after you add this line into the defaults list, what is the actual command to run to launch said file?

I access a share quite often that has many .xlsx files that I use, and like you would rather do this from command line, but haven't quit figured it out yet.  any help is appreciated

---

### Post by Kissell on 2012-02-09
> **mkeyes001 said:**
> so this maybe a silly question, but after you add this line into the defaults list, what is the actual command to run to launch said file?

I access a share quite often that has many .xlsx files that I use, and like you would rather do this from command line, but haven't quit figured it out yet.  any help is appreciated

I just wanted to be able to associate the .xlsx file extension with LibreCalc from the command line, so that inside the Gnome or Unity GUI I could double-click a .xlsx file and it would open...  by default it would not.  This solved my problem, as now the installation script I wrote will always fix this problem, so every Ubuntu installation I do will have this fixed.  I could have fixed it from the GUI, but that would have required me to remember to do this, and to manually do it everytime I installed the OS.  Now I can script it so the problem never happens again even after I reinstall the OS.  

If what you're wanting is to open the libreCalc program from the command line, then you can type "libreoffice --calc" and put a path to a file after that if you have a specific file you want it to open...  I think that should work.

---

