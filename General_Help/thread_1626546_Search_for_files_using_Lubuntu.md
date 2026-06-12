---
title: "Search for files using Lubuntu"
date: 2010-11-20
forum: General Help
---

### Post by tomreid on 2010-11-20
Hi

I'm running Lubuntu from a live CD on a very old (approx 8 years) system which has a broken install of Win XP on it's hard drive.

When I navigate to the files on the hard drive using Lubuntu's file manager I'm not seeing the files I'd like to recover. 

I can't see a "search for files or folders" option in Lubuntu. Is there one? Does anyone know how to do this?

I've pretty much exhausted all the possibilities around clicking pn folders on it's HD.

cheers

---

### Post by Austin25 on 2010-11-20
If you don't mind using the command line, try using find.
For instance, to search for all the files with *foo *in it on the whole filesystem, then use:
```
find / -name '*foo*'
```
To search for a file named *foo.txt* in your home directory, use:
```
find ~/ -name 'foo.txt'
```
If you want to check out some other stuff, try:
```
man find
```

---

### Post by kakashi_12 on 2011-10-26
what about through the GUI

---

### Post by amjjawad on 2011-10-26
> **kakashi_12 said:**
> what about through the GUI
```
sudo apt-get update && sudo apt-get install catfish
```

---

### Post by amjjawad on 2011-10-26
Wiki Page updated

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_Search_for_Files_in_Lubuntu_using_GUI_application](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_Search_for_Files_in_Lubuntu_using_GUI_application)

---

### Post by croque on 2011-10-26
I've used Recoll for a long time and really like it. Very powerful and fast searches. It has a GUI but can also be used from the command line. It's in the repositories and seems to work well in Lubuntu 11.10. More info here:

[http://www.lesbonscomptes.com/recoll/](http://www.lesbonscomptes.com/recoll/)

From the website: "[I]Recoll can index an **MS-Word** document stored as       an **attachment** to an **e-mail message** inside       a **Thunderbird folder** archived in a **Zip file**       (and more...). It will also let you open a copy of the file       without any fuss. There is little that will remain hidden on        your disk :)" 
[/I]

---

### Post by kakashi_12 on 2011-10-27
thank you.

---

