---
title: "searching for a '.lit' reader"
date: 2010-04-25
forum: General Help
---

### Post by bashphoenux on 2010-04-25
I think the title itself is pretty self explanatory! anyways I have couple of .lit files and I am searching for a good reader for that !
any one know of a nice reader for Kubuntu ???

---

### Post by blueridgedog on 2010-04-25
Probably best to convert it:

An online tool:

[http://ebook.online-convert.com/](http://ebook.online-convert.com/)

Several windows tools that may run in wine:

[http://wiki.mobileread.com/wiki/E-book_conversion](http://wiki.mobileread.com/wiki/E-book_conversion)

---

### Post by sandyd on 2010-04-25
try [_convlit_]("apt:/convlit")

and yes, I originally wrote the name of the executable, which was **** (no pun intended, really), but someone banned that word?

---

### Post by bashphoenux on 2010-04-25
but isn't there  an application ???? a native app or something??\I somehow don't have luck with wine!

---

### Post by sandyd on 2010-04-26
> **bashphoenux said:**
> but isn't there  an application ???? a native app or something??\I somehow don't have luck with wine!

as said above, use the program convlit, or convert it through the site.

---

### Post by StuartN on 2010-04-26
> **bashphoenux said:**
> but isn't there  an application ???? a native app or something??\I somehow don't have luck with wine!

Calibre should read and convert .lit files that do not have DRM.

---

### Post by bashphoenux on 2010-04-26
> **StuartN said:**
> Calibre should read and convert .lit files that do not have DRM.
thanks will try Calibre

---

### Post by bashphoenux on 2010-04-26
i got this error while trying to install calibre mate 
Failed to run pkg-config: None for: poppler
Failed to run pkg-config: None for: poppler-qt4
Traceback (most recent call last):
  File "setup.py", line 13, in <module>
    import setup.commands as commands
  File "/home/abhinav/calibre/setup/commands.py", line 28, in <module>
    from setup.translations import POT, GetTranslations, Translations, ISO639
  File "/home/abhinav/calibre/setup/translations.py", line 14, in <module>
    from setup.build_environment import pyqt
  File "/home/abhinav/calibre/setup/build_environment.py", line 150, in <module>
    popplerqt4_inc_dirs = poppler_inc_dirs + [poppler_inc_dirs[0]+'/qt4']
IndexError: list index out of range 				

any idea on what's wrong???

---

### Post by StuartN on 2010-04-27
> **bashphoenux said:**
> Failed to run pkg-config: None for: poppler
Failed to run pkg-config: None for: poppler-qt4

I have installed Calibre in Ubuntu 10.04 and was previously using it in 9.10. I did not have errors during installation in either distribution.

I do not know what those error messages mean, but I would start by installing Poppler again.

I see that I have libpoppler-glib4, libpoppler5 and poppler-utils installed, so perhaps something that you had previously installed partially fulfilled the dependencies for Calibre. Check that these three are installed and up-to-date.

---

### Post by bashphoenux on 2010-05-01
thanks
sudo apt-get install cailbre did the job for me :) 
thanks once again

---

### Post by terrydiehard on 2010-05-15
Here's an easy fix. This applies specifically for Ubuntu 10.04. Shouldn't vary that much for Fedora, etc.

1) Click Application
2) Click Ubuntu Software
3) Select Get Software
4) Type "Calibre" without the inverted commas in the Search Box
5) Click install

There you go. You can use Calibre to read ".lit" files. The steps above may vary slightly for you however just remember the software that you are looking for is "Calibre". Another route you may choose to install software is by using "Terminal" where you may use the "sudo apt-get install _____" command.

After Calibre is installed you can click on "applications" then go to "office". Click "calibre". In the "Calibre" software you will see "add books". Click "add books". Then navigate through the "file system" to get your book or just go to a mounted drive.

Oh yeah you will see your e-book added to your "Calibre" library. To view book just right click on the book you selected and click view.

Terry

---

