---
title: "best way to remove chromium browser"
date: 2010-07-26
forum: General Help
---

### Post by MMALLOW on 2010-07-26
what the best way to remove 

chromum browser and his elements or all backedge

---

### Post by linux18 on 2010-07-26
```
 sudo aptitude purge chromium*
```

---

### Post by dv3500ea on 2010-07-26
Go to System -> Administration -> Synaptic Package Manager.
Type chromium into the search box.
Select the chromium package and mark it for complete removal.
Click on the green tick to apply.

---

### Post by clhsharky on 2010-07-26
With your package manager.
Info please(distribution & Release).

Sharky

---

### Post by MMALLOW on 2010-07-26
THANKS I MADE THIS FROM TERMINAL BUT  I GO TO APPLECATION - INTERNET

I FOUND CHROMUM BROOWSER

THAT MEANING I NOT DELETED

ALSO THIS DETALS FROM TERMINAL


-------------------------------
mallow@mallow-laptop:~$  sudo aptitude purge chromium*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "chromium*"
Couldn't find any package whose name or description matched "chromium*"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
--------------------------------------------------------

WHAT I WILL DO NOW

---

### Post by VH-BIL on 2010-07-26
Chrome or Chromium?

---

### Post by Goolie on 2010-07-26
```
sudo apt-get remove chromium
```

try this?

---

### Post by MMALLOW on 2010-07-26
THIS CODE WILL REMOVE CHROMIUM BROWSER WITH HIS ELEMENTS OR ALL BACK EDGE 


Code: 

 	sudo apt-get remove chromium

---

### Post by MMALLOW on 2010-07-26
I TRYED THIS CODE mallow@mallow-laptop:~$ sudo apt-get remove chromium

AND THIS RESULT
-------------------------


mallow@mallow-laptop:~$ sudo apt-get remove chromium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package chromium is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mallow@mallow-laptop:~$ 

----------------------------------------------

ALSO I GO TO APPLECATION -- INTERNET 

STILL THER PROGRAM THERE

WHAT I WILL DO

---

### Post by VH-BIL on 2010-07-26
You can delete the directory "~/.config/chromium" as well if you like.

---

### Post by MMALLOW on 2010-07-26
Where can i find this place

---

### Post by MMALLOW on 2010-07-26
Thanks 
 i removed by synaptic

---

### Post by Goolie on 2010-07-26
```
rm -r /.config/chromium
```

---

### Post by dv3500ea on 2010-07-26
> **MMALLOW said:**
> Where can i find this place

Places -> Home
Press ctrl-h
double click the .config folder.
delete the chromium folder.

---

### Post by VH-BIL on 2010-07-26
> **Goolie said:**
> ```
rm -r /.config/chromium
```

Wouldn't it be:
```
rm -r ~/.config/chromium
```

---

### Post by lovinglinux on 2010-07-26
For the record, it is **chromium-browser** folks. The package **chromium** is a game, that's why the OP kept receiving messages that it wasn't installed.

---

### Post by VH-BIL on 2010-07-27
> **lovinglinux said:**
> For the record, it is **chromium-browser** folks. The package **chromium** is a game, that's why the OP kept receiving messages that it wasn't installed.

I have accidentally installed that game many times and wondered where is my browser lol.

---

### Post by lovinglinux on 2010-07-27
> **VH-BIL said:**
> I have accidentally installed that game many times and wondered where is my browser lol.

:lol:

I have accidentally installed it a couple of times too.

---

### Post by cespinal on 2010-07-27
rm -rf ~ /.config/chromium/default

this one was the command I executed. It deleted my whole home folder...

---

### Post by VH-BIL on 2010-07-27
> **cespinal said:**
> rm -rf ~ /.config/chromium/default

this one was the command I executed. It deleted my whole home folder...

That is because you have a space between the ~ and /. The remove command thinks you are giving it 2 locations to delete, your home directory being ~ and /.config/chromium/default which would not exist at that location. The ~ symbol is just a quick way of typing the path to your home folder.

---

### Post by wojox on 2010-07-27
Did you install this through a ppa?

---

### Post by chrisharrington on 2010-07-27
EDIT:
-------------------
Er, lovinglinux already said it....next time I'll read the whole thread ;)

> **lovinglinux said:**
> For the record, it is **chromium-browser** folks. The package **chromium** is a game, that's why the OP kept receiving messages that it wasn't installed.

-------------------

Actually, package chromium is a transitional dummy package for a game. The package 'chromium' is NOT the chromium browser. The chromium browser package is 'chromium-browser'.

[INDENT]package chromium
transitional dummy package to pull in chromium-bsu[/INDENT]

[INDENT]package chromium-browser
Chromium is an open-source browser project that aims to build a safer, faster,
and more stable way for all Internet users to experience the web.
So it is better to be specific and ... [/INDENT]

So you want to type this in terminal:

```
sudo apt-get purge chromium-browser
```

and then remove any left over config folders in your $HOME directory if necessary.

If you installed the Chrome browser, not the chromium browser, then it is again a *different* package


[INDENT]package google-chrome-beta
Google Chrome is a browser that combines a minimal design with sophisticated technology to make the web faster, safer, and easier.[/INDENT]

So you would type 

```
sudo apt-get purge google-chrome-beta
```

---

### Post by jtarin on 2010-07-28
> **MMALLOW said:**
> 

ALSO I GO TO APPLECATION -- INTERNET 

STILL THER PROGRAM THERE

WHAT I WILL DOYou will right-click on the panel icon for the start menu and choose "Edit Menus".Then from the menu editor you will choose the "Application" column then the sub-title "Internet and after that selection you should see your menu item in the "Items" column in the right-hand window. High-light your desired item then click delete.

---

### Post by jtarin on 2010-07-28
> **alibiter said:**
> [www.ben10tengames.com](www.ben10tengames.com) how can i increase hit of this game site.By removing it from the forum.:p

---

