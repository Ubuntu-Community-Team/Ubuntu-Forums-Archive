---
title: "Having problems with Smeg or Alacarte? Here's a fix."
date: 2006-03-11
forum: General Help
---

### Post by magnusbb on 2006-03-11
Hello everyone,

I had some serious issues with the Ubuntu menu editor in GNOME recently (Smeg / Alacarte). It didn't open, and when running it in terminal I got a ton of errors, ending with:

```
File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 290, in compile
    exec("""
  File "<string>", line 6
    elif :
         ^
SyntaxError: invalid syntax
```

But, I found a fix during some heavy googling.

Do a:
```
sudo gedit /usr/lib/python2.4/site-packages/xdg/Menu.py
```

and jump to somewhere around line 290 (probably 296). Replace the text:
```
elif %s:
```

with

```
elif (%s):
```

And save the file.

Try running smeg or alacarte again, and see what happens. It works here!

Alacarte is a newer version than smeg and can be found here in the forums. I recommend it.

---

### Post by mycelo on 2006-08-01
Wow, thanks, now I have some menu entries that never showed up!

mycelo

---

### Post by brucehohl on 2006-09-23
Thank you for posting this. I had the same problem and this change corrected the problem.

---

### Post by myfmelo on 2006-10-10
> **magnusbb said:**
> Hello everyone,

I had some serious issues with the Ubuntu menu editor in GNOME recently (Smeg / Alacarte). It didn't open, and when running it in terminal I got a ton of errors, ending with:

```
File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 290, in compile
    exec("""
  File "<string>", line 6
    elif :
         ^
SyntaxError: invalid syntax
```

But, I found a fix during some heavy googling.

Do a:
```
sudo gedit /usr/lib/python2.4/site-packages/xdg/Menu.py
```

and jump to somewhere around line 290 (probably 296). Replace the text:
```
elif %s:
```

with

```
elif (%s):
```

And save the file.

Try running smeg or alacarte again, and see what happens. It works here!

Alacarte is a newer version than smeg and can be found here in the forums. I recommend it.


Hello magnusbb,

I'm facing a similar problem that started after I added a new item for NetBeans on the menu. Since then the following error appears:

Any ideas? Thanks in advance. :)

Traceback (most recent call last):
File "/usr/bin/alacarte", line 26, in ?
main()
File "/usr/bin/alacarte", line 23, in main
GnomeFront()
File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 72, in __init__
self.loadMenus()
File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 201, in loadMenus
self.app_handler = MenuHandler('applications.menu', self.options)
File "/usr/lib/python2.4/site-packages/Alacarte/PyXDGMenuHandler.py", line 27, in __init__
xdg.MenuEditor.MenuEditor.__init__(
File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init__
self.parse(menu, filename, root)
File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 40, in parse
self.menu = parse(menu)
File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 516, in parse
__parse(doc, filename, tmp["Root"])
File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
__parseMenu(child, filename, parent)
File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
__parse(child, filename, m)
File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
__parseMenu(child, filename, parent)
File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
__parse(child, filename, m)
File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 571, in __parse
parent.Rules.append(Rule(child.tagName, child))
File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 284, in __init__
self.compile()
File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 290, in compile
exec("""
File "<string>", line 6
elif (menuentry.DesktopFileID == 'file:---home-user-Desktop-netbeans5.5rc1.desktop
^
SyntaxError: EOL while scanning single-quoted string

---

### Post by warmink on 2006-11-12
He magnusbb, magnificent. Great fix for my major problem. The add/remove tool did not work in my case, but this fix works perfectly.

You made me :-D

---

### Post by dpm on 2006-11-12
> **magnusbb said:**
> 
I found a fix during some heavy googling.


Have you reported this as a bug? Otherwise this will not be fixed until the developers get to know about it.

In Edgy, /usr/share/python-support/python-xdg/xdg/Menu.py has still got the line (296):

```
 elif %s:
```without the parentheses, although I must say I personally haven't experienced any problem with Alacarte apart from the fact that it is painfully slow.

Cheers.

---

