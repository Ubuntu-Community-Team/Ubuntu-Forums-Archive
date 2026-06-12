---
title: "File permissions"
date: 2010-12-12
forum: General Help
---

### Post by nocturnal1 on 2010-12-12
I am trying to install a plugin for Inkscape in Ubuntu 10.10. I have downloaded it to the desktop and ran a chmod 777 on the two files but I still can't copy them to the needed folder in Inkscape. I get a permission denied. Please help.

---

### Post by ryadav on 2010-12-12
permission needs to change on destination plug-in folder

a) find owner name of folder, do a 'ls -l'
b) copy as root, sudo cp 
c) then chown -R the files, folder you are copying over, set to owner name from a)

man chown for more details

---

### Post by 3rdalbum on 2010-12-12
You need to copy the files across as root. The easiest way to do this is to open a file browser as root:

gksudo nautilus

in the terminal. Now you can do anything to your computer from that new file browser window, including copying the files. Be careful!

---

### Post by mrkazoodle on 2010-12-12
```
sudo mv SOURCE DESTINATION
```

this wil move files using root privileges
more info on this command: $ man mv

---

### Post by nocturnal1 on 2010-12-12
Thank you [ryadav]("http://ubuntuforums.org/member.php?u=873411"), it was very late when I was trying this. I did:
```

 sudo chmod 777 textext.py
 sudo chmod 777 textext.inx
 sudo chmod 777 Destination 
 sudo cp textext.py Destination 
 sudo cp textext.inx Destination 

```

This worked but the plugin has bugs and still gives an md5 error that others are reporting as well. 
```

~/.[COLOR=black]inkscape[/COLOR]/extensions/textext.[COLOR=black]py[/COLOR]:[COLOR=#FF4500]55[/COLOR]: [COLOR=#008000]DeprecationWarning[/COLOR]: 
the [COLOR=#DC143C]md5[/COLOR] module [COLOR=#FF7700]**is**[/COLOR] deprecated[COLOR=#66CC66];[/COLOR] use hashlib instead
[COLOR=#FF7700]**import**[/COLOR] [COLOR=#DC143C]os[/COLOR], [COLOR=#DC143C]sys[/COLOR], [COLOR=#DC143C]tempfile[/COLOR], [COLOR=#DC143C]traceback[/COLOR], [COLOR=#DC143C]glob[/COLOR], [COLOR=#DC143C]re[/COLOR], [COLOR=#DC143C]md5[/COLOR], [COLOR=#DC143C]copy[/COLOR]
```
I'am going to try modifying the script next as per this site shows:
[http://pascalschulthess.de/inkscape-and-textext-deprecation-warning/](http://pascalschulthess.de/inkscape-and-textext-deprecation-warning/)
When I install Inkscape from Synaptic Package Manager it installs the older 0.47 version but when I install using Software center it installs the latest stable version 0.48. 

I'ts very frustrating I can't use Latex alone to get what I need so using Inkscape is allmost my only option. I could switch to Windows "sorry for the dirty word" and Illustrator.  I tried creating the basic template in Openoffice then the math I need with Latex then converting both to SVG with pdf2svg and assembling them both with Scribus but I loose some editing capability.

---

