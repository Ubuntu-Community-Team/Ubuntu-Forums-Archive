---
title: "Unable to open executables with WINE Program Loader since upgrade"
date: 2011-05-11
forum: General Help
---

### Post by Dáire Fagan on 2011-05-11
Since ugprading today to a fresh install of Xubuntu 11.04 I am unable to open .exe's through Thunar my file manager with 'WINE Program Loader'

Wine 1.2.2.

When I try to i receive the error: 

> The file '/media/DUMP/Downloads/anything.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit.When I check the permissions tab of properties there is no option to make it executable as per screenshot.

Also using chmod +x doesn't change anything but I am able to open .exe using WINE in the terminal but I would rather I did not have to do this every time I use WINE.

Is there something I can do?

P.S. I have no intention of using mIRC, it was just a small windows installer I downloaded for testing.

EDIT: when I chmod +x on the file on my home partition I can open it, but when I try the same on my media partition it does not help at all. 

Can I make it so it will work on any partition, and can I make it so I do not need to manually chmod +x every time?

---

### Post by mc4man on 2011-05-11
r click on any .exe > **properties** > open with > other application > use a custom command
For the command simply use 
wine
Then use that in the future off of right click or should have been set as the new default double l. left click from above

Or (though a wine update can overwrite

```
gksudo gedit /usr/share/applications/wine.desktop
``` and make the Exec= line as such
```
Exec=wine start /unix %f
```

---

### Post by Dáire Fagan on 2011-05-11
[IMG]http://oi56.tinypic.com/2ni5t9f.jpg[/IMG]

---

### Post by mc4man on 2011-05-11
Sorry - missed the xubuntu, don't know here how xubuntu sets file associations
If you edit the wine.desktop should be no issue with the cautious-launcher when using Wine  Windows Program Loader

---

### Post by 3rdalbum on 2011-05-11
You can't chmod on a non Linux filesystem, because they don't support the execute permission. Only Linux and Unix filesystem.

---

### Post by Dáire Fagan on 2011-05-18
> **mc4man said:**
> r click on any .exe > **properties** > open with > other application > use a custom command
 For the command simply use 
 wine
 
 That worked great, thanks! :)
 
 That said, if possible just so everything's working as it should I would rather be able to use the WINE Program Loader...
 
 > **mc4man said:**
> 
 Or (though a wine update can overwrite
 
 ```
gksudo gedit /usr/share/applications/wine.desktop
``` and make the Exec= line as such
 ```
Exec=wine start /unix %f
```

> **mc4man said:**
> 
 If you edit the wine.desktop should be no issue with the cautious-launcher when using Wine  Windows Program Loader
 
 I used: 
 
 ```
gksudo mousepad /use/share/applications/wine.desktop
```
 
 and I added the line:
 
 ```
Exec=wine start /unix %f
```
 
 and then saved the file.
 
This works great, thanks! :)

Is there anyway to get around wine.desktop being overwritten every WINE update, and if this is the problem does this mean the Exec line is different on Ubuntu than it is on Xubuntu, and if so why? 

> **3rdalbum said:**
> You can't chmod on a non Linux filesystem, because they don't support the execute permission. Only Linux and Unix filesystem.

Thanks good to know, but it seems it's not necessary for me to chmod +x in the first place as editing wine.desktop negates that.

---

### Post by mc4man on 2011-05-18
> Is there anyway to get around wine.desktop being overwritten every WINE update, and if this is the problem does this mean the Exec line is different on Ubuntu than it is on Xubuntu, and if so why? 
Sure - just copy to your home directory's applications folder, it takes precedence over the one in /usr and can't be overwritten - a log out/in to set after the cp
This goes for most uses of any .desktop you may modify and want to protect - 
( modifying .desktops can serve one well  in unity

for wine
```
cp /usr/share/applications/wine.desktop ~/.local/share/applications/

```

Just make sure the applications folder exists, on a fresh install it doesn't, though usually created by any number of common actions, - r.click - open with, ect.
To ck. and create if not there
mkdir ~/.local/share/applications

(if providing for other users then cp .desktops as root to /usr/local/share/applications instead, more likely it doesn't exist - this will ck. and create if not there
sudo mkdir /usr/local/share/applications

---

### Post by mafredd03 on 2011-11-20
[QUOTE=dusf;10830706]That worked great, thanks! :)
 
 That said, if possible just so everything's working as it should I would rather be able to use the WINE Program Loader...
 
 


 
 I used: 
 
Code:
gksudo gedit /usr/share/applications/wine.desktop
and make the Exec= line as such
Code:
Exec=wine start /unix %f

It worked great :KS thanks !!!!!

---

