---
title: "Nautilus wipe and shred"
date: 2010-09-18
forum: General Help
---

### Post by Nuxala on 2010-09-18
I finally found a distro that suits my demands after trying different ones. I only have one problem now and that's nautilus.  I installed nautilus and nautilus-actions so that I could add things like shred and wipe. But the wipe and shred options aren't there. They only appear when I open terminal with. 

name-laptop:~$ nautilus 
Initializing nautilus-gdu extension 

it opens the directory menu and that's when I see the options wipe and shred.  How can I make the actions work without using terminal? Or maybe there's another way for lubuntu to use wipe and shred?

---

### Post by ankspo71 on 2010-09-18
Hi, 
Do you have wipe installed? 

Here is nautilus actions instructions for wipe that might help.
[http://www.mopedia.co.uk/2007/12/wipe-filesfolders-using-nautilus.html](http://www.mopedia.co.uk/2007/12/wipe-filesfolders-using-nautilus.html)

Here is another nautilus actions instructions for shred:
[http://notebook.andrewabogado.com/6-useful-nautilus-file-manager-extensions](http://notebook.andrewabogado.com/6-useful-nautilus-file-manager-extensions)

One more on wipe:
[http://derglotzer.blogspot.com/2010/09/computer-wipe-shred-files-in-nautilus.html](http://derglotzer.blogspot.com/2010/09/computer-wipe-shred-files-in-nautilus.html)

Hope this helps.

This topic makes me want to give Gnome another try. ;)

---

### Post by Nuxala on 2010-09-18
Yes I have them installed and they do work, but they only appear in the  right-click menu when I I open terminal with. 

name-laptop:~$ **nautilus **
Initializing nautilus-gdu extension

---

### Post by ankspo71 on 2010-09-18
Hi,
Ahh, you need a way to start nautius without typing "nautilus". Some LXDE experts might need to step in and help with this, because I have barely used LXDE. I'll try to help though.

There is a shortcut creater for LXDE called "lxshortcut", but I just tried it in gnome and kde but it didn't work for me. Maybe it will work for you since you use Lubuntu. I had to install it because it isn't included in Gnome or KDE

If that utility works, great, but if not, keep reading...

---

On my system there is a nautilus.desktop file located in /usr/share/applications/ . If you have one too, make sure there is a line inside it that says: 
```
OnlyShowIn=GNOME;[COLOR="Blue"]**LXDE;**[/COLOR]
```
The "LXDE;" part I had to add myself because on my desktop it was only created to appear in Gnome. You will need to open your text editor as root to modify the file.

when done editing you might need to run this command to make the shortcut appear in your menu

```
update-menus
```

---

You can also copy that file to your desktop folder too if you like having a desktop shortcut. You can use this command into the terminal to do that.
```
cp /usr/share/applications/nautilus.desktop ~/Desktop/
```
Then you need to right click on that file you just created, go to the permissions settings, and change it to an executable file. I'm not very familiar with LXDE but the shortcut should work. 

---

If you don't have a nautilus.desktop file in your /usr/share/applications/ folder, you can create one yourself.
1 Create a plain file on your desktop.
2 Paste this into it:

```
[Desktop Entry]
Name=File Manager
Exec=nautilus
Icon=system-file-manager
Terminal=false
Type=Application
StartupNotify=true
NoDisplay=true
OnlyShowIn=GNOME;[COLOR="Blue"]**LXDE;**[/COLOR]

```

3. Make sure the shortcut will work in your LXDE desktop as shown in blue above as I mentioned earlier. You can also change the shortcut's name and icon if you want.

4. save the file as nautilus.desktop

5. right click on the file and make it executable.
That should do it.

References:
[http://stray-notes.blogspot.com/2010/08/lxde-main-menu-edit.html](http://stray-notes.blogspot.com/2010/08/lxde-main-menu-edit.html) 
[http://www.pclinuxos.com/forum/index.php?topic=71445.0](http://www.pclinuxos.com/forum/index.php?topic=71445.0)

---

### Post by Nuxala on 2010-09-18
Thanks for you help ankspo71, but nothing worked or I did something wrong.


> There is a shortcut creater for LXDE called "lxshortcut", but I just  tried it in gnome and kde but it didn't work for me. Maybe it will work  for you since you use Lubuntu. I had to install it because it isn't  included in Gnome or KDE

I have it installed too but it didn't work.


> On my system there is a nautilus.desktop file located in /usr/share/applications/ . If you have one too, make sure there is a line inside it that says: 

I have one too I just can't see it. When I made one it said do you want to replace it and I said yes.
(I used gksudo nautilus command and show hidden file to paste the new file)

---

### Post by searchfgold6789 on 2010-09-18
Try making a shortcut on your desktop that runs nautilus in the terminal. If that works, you might try finding a way to make all the nautilus launchers run in the terminal.

---

### Post by Nuxala on 2010-09-18
> Try making a shortcut on your desktop that runs nautilus in the  terminal. If that works, you might try finding a way to make all the  nautilus launchers run in the terminal. 	

I find this link and it worked, thanks for the tip.

[B][Create a Desktop shortcut in Lubuntu for Nautilus]("http://nancyfusco.com/wp/index.php/2010/08/create-a-desktop-shortcut-in-lubuntu-for-nautilus/")

[/B]I still don't understand why typing lxshortcut won't open it but 
**lxshortcut -o ~/Desktop/nautilus.desktop** did.

---

