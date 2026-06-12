---
title: "7zip and rar"
date: 2006-04-25
forum: General Help
---

### Post by frup on 2006-04-25
downloaded some files in these formats and can't access them :(
downloaded p7zip in synaptic... worked fine... but i dont know how to open it etc... .7z files still got the gnome foot (which tends to mean file not supported right?)

is there anyway i can edit the standard archive manager to understand these formats... is it as simple as downloading a "codec" type thing?

thanks :D

---

### Post by dpicker on 2006-04-25
Is there nothing new in the applications menu?

See if typing "p7zip" or "p7zip --help" in terminal says anything.

I would install and try myself but i'm on windows at the moment :p

To get rar support I think you need to type:

sudo apt-get install rar
sudo ln -fs /usr/bin/rar /usr/bin/unrar

and then .rar archives should open up in the normal archive manager app.

---

### Post by frup on 2006-04-25
no nothing new in the menu.

plain command 7z works but i can't open the file

tried 7z l filename.7z in command cant work it.

---

### Post by cgjones on 2006-04-25
[QUOTE=frup]no nothing new in the menu.

plain command 7z works but i can't open the file

tried **7z l filename.7z** in command cant work it.[/QUOTE]

Is that a pipe or a lowercase L between 7z and the filename? In either case, I don't think you need it.

---

### Post by frup on 2006-04-25
no it was that means list files in dir... but you got me working at it again (i was trying to install winrar in wine badly lol..) and i did 7z l "filename.7z" and it worked... its lowecase L not pipe... now i gota find solution to rar

---

### Post by justleen on 2006-04-25
theres rar support too... not sure which package (@work) but do a sudo apt-cache search rar for it. (after i installed that i could simply right click > Unpack here.. the files)

---

### Post by frup on 2006-04-26
well i foud unrar or something... doesnt handle rar 3.0 though :S
o well

---

### Post by ice60 on 2006-04-30
i use the winrar program.
[http://www.rarlab.com/download.htm](http://www.rarlab.com/download.htm)
[http://www.rarlab.com/rar/rarlinux-3.6.b2.tar.gz](http://www.rarlab.com/rar/rarlinux-3.6.b2.tar.gz)

when it's installed you can extract by right-clicking, or -
```
rar e *filename*
```
if it's password protected both extraction ways will just ask you to fill in the password. :D 

it says it's trial software, but i think it's a very long trial :cool:

---

### Post by AnRuaRi on 2006-04-30
rar support is privided easily.
The instructions are in the ubuntu beginners gude. It worked no problem for me.

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2513073](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2513073)

it says

2.	

How do I install RAR Archiver (rar)?
	

   1.

      Read How do I add Universe and Multiverse?
   2.

      Install the rar package with Synaptic (See How do I use Synaptic to install packages?)

      Utilities (multiverse) > rar

   3.

      sudo ln -fs /usr/bin/rar /usr/bin/unrar

   4.

      Applications->Accessories->Archive Manager

---

### Post by Ramses de Norre on 2006-04-30
sudo apt-get install unrar-nonfree
You can use .rar files with archive manager then.

---

