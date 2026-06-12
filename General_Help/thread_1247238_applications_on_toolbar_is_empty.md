---
title: "applications on toolbar is empty"
date: 2009-08-22
forum: General Help
---

### Post by Rich1540 on 2009-08-22
shut down laptop and when i restarted everything was the same except the applications on toolbar ,when i click on it nothing ! how do get this back it had ,wine video and audio ,command and everything but i cant find how to get these programs back?
applications is still there ,but no programs are in there empty 

ubuntu 9.04 
laptop acer aspire 5515
ubuntu is great till this happened but if it wasnt for problems it wouldnt be any fun

---

### Post by ks07 on 2009-08-22
> **Rich1540 said:**
> shut down laptop and when i restarted everything was the same except the applications on toolbar ,when i click on it nothing ! how do get this back it had ,wine video and audio ,command and everything but i cant find how to get these programs back?
applications is still there ,but no programs are in there empty 

ubuntu 9.04 
laptop acer aspire 5515
ubuntu is great till this happened but if it wasnt for problems it wouldnt be any fun
They might have just been hidden. Try right clicking the applications button, then choose 'Edit Menus'. You should be able to check the boxes next to the menu items you want to appear, unless you somehow deleted them completely.

---

### Post by Rich1540 on 2009-08-22
must have deleted some how ,tryed to edtit menus and nothing comes up ,how do i add them back in?

---

### Post by ks07 on 2009-08-22
> **Rich1540 said:**
> must have deleted some how ,tryed to edtit menus and nothing comes up ,how do i add them back in?
[COLOR=Silver]Sadly, I don't know any quick way of restoring your menus. What you can do is use the New Menu and New Item buttons to manually add _everything_ back. You could try that, but I'm guessing there is a lot more elegant and faster way to solve this problem. Any takers?

[COLOR=Black]EDIT:
COUGH COUGH

Try the revert button at the bottom of the menu editor? lol
[/COLOR][/COLOR]

---

### Post by Rich1540 on 2009-08-22
tryed to add new applications button and edit menus on that one but nothing shows so that didnt work! menu editor dosent show up?

---

### Post by ks07 on 2009-08-22
> **Rich1540 said:**
> tryed to add new applications button and edit menus on that one but nothing shows so that didnt work! menu editor dosent show up?
Sorry, misread your earlier post. If you can't get the menu editor to run, I'm lost as for what to do.

Try running it through the terminal in case it is showing any error messages by running ```
alacarte
```

---

### Post by Rich1540 on 2009-08-22
cant even find the terminal it was under the applications

---

### Post by ks07 on 2009-08-22
> **Rich1540 said:**
> cant even find the terminal it was under the applications
*facepalm* You start to take things for granted lol.

Press Alt-F2 then type gnome-terminal and you should be set.

---

### Post by Rich1540 on 2009-08-22
and this is what i got /Error stating file '/home/free/gnome terminal': No such file or directory
and when i type alacarte it flashes up and then gone in the run application!

---

### Post by ks07 on 2009-08-22
> **Rich1540 said:**
> and this is what i got /Error stating file '/home/free/gnome terminal': No such file or directory
and when i type alacarte it flashes up and then gone in the run application!
Hmm weird.

Are you sure you typed gnome-terminal as opposed to gnome terminal (it needs a dash not a space).

---

### Post by Rich1540 on 2009-08-22
gnome-terminal with dash and it just flashed and gone ?

---

### Post by ks07 on 2009-08-22
> **Rich1540 said:**
> gnome-terminal with dash and it just flashed and gone ?
Your problem seems to be more serious than it first seemed if we can't even open a terminal window... The fact that it flashed up shows you must have ran it correctly, it just crashes.

This looks like it goes way beyond the scope of my knowledge. I think you may have to wait for one of the forums gurus to come lend you a hand. Sorry I can't be of any help. :(

---

### Post by Rich1540 on 2009-08-22
thanks for the help greatly appreciate anyway!
hopefully i can get this fixed everything else is working perfectly!

---

### Post by Rich1540 on 2009-08-22
reinstalled gnome-terminal threw package manager and ran run application, now i have this up now what do i do to get programs back in applications if at all possible ?

---

### Post by Rich1540 on 2009-08-22
okay more info , i uninstalled wine completely and then later i shut down laptop to go to bed i think this is my starting problem didnt relize this till i got googleing and i seen wine ! so im thinking

---

### Post by Rich1540 on 2009-08-22
when i uninstalled wine i must have deleted everything in applications ,found menus file and nothing in it how do iput the files back in ?any more help would be greatly appreciate it!

---

### Post by ks07 on 2009-08-23
I guess I'll see what I can do, you seem a bit desperate atm :P. Short of uploading my gnome menu file(s) for you to use, you could try running
```
alacarte
```
in the terminal now that you can get it running. If it won't load it should at least spew out some error codes that we can work from.

---

### Post by Rich1540 on 2009-08-23
this is wfree@free:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0
free@free:~$ 
hat i got !

---

### Post by ks07 on 2009-08-23
> **Rich1540 said:**
> this is wfree@free:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0
free@free:~$ 
hat i got !
Well I just did a search for some of those errors it returned (god knows what they mean) and I came across this bug report on launchpad. Seems it was fixed only by a reinstall...

[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/182586](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/182586)

I have uploaded a copy of my applications.menu file if you want to try to workaround the problem. Other than that I can't think of any other way to solve it. I copied this from /etc/xdg/menus, so placing it there may fix your problem. *You probably want to back up whatever is there before overwriting it.

EDIT: Should have said, you need to delete the .txt extension off the end.

---

### Post by Rich1540 on 2009-08-23
Thank you so much! i will try this and see what happens will come back with the results! appreciate the help will do when i get home!

---

### Post by drs305 on 2009-08-23
If your menu is completely empty, try renaming the $HOME/.config/menus folder. A new default one should be created when you log in.

---

### Post by Rich1540 on 2009-08-23
like i was told and it worked like a charm thank you drs305 and thanks for sticking with me ks07 !!

Reading ,learning and still losing sleep dont get any better than this !!

thanks everyone appreciate the help!

---

