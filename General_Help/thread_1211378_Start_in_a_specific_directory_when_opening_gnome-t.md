---
title: "Start in a specific directory when opening gnome-terminal"
date: 2009-07-12
forum: General Help
---

### Post by gasto on 2009-07-12
Hi folks,

I always start the gnome-terminal, by(alt+f2 and inputting gnome-terminal for the name of the app).

So it always opens at directory: ~   which is home\UserName

I guess,

but I want it to start on say:

home/UserName/Documents/AnotherDir

I read that I had to modify /etc/.bashprofile

But I couldn't see where $HOME was so I couldn't change it. Also I don't know if with sudo gedit /etc/.bashprofile I will be able to edit it (the last time I tried to create a .bashrc file, gedit did not allow me to edit it because of lack of permission).

---

### Post by Finalfantasykid on 2009-07-12
```
gnome-terminal --working-directory=/directory 
```

Just make that the new command for the launcher or whatever and it will open in that directory.  I think you can also change the default directory if you play with the terminal profile preferences.

---

### Post by nice_like_rice on 2009-07-12
Just go into a console, log in as your usual user, and type

```

HOME=/home/user/somedirectory/

```

hmph user above is right - it seems that changing it my way isn't permanent.

david

---

### Post by philinux on 2009-07-12
> **gasto said:**
> Hi folks,

I always start the gnome-terminal, by(alt+f2 and inputting gnome-terminal for the name of the app).

So it always opens at directory: ~   which is home\UserName

I guess,

but I want it to start on say:

home/UserName/Documents/AnotherDir

I read that I had to modify /etc/.bashprofile

But I couldn't see where $HOME was so I couldn't change it. Also I don't know if with sudo gedit /etc/.bashprofile I will be able to edit it (the last time I tried to create a .bashrc file, gedit did not allow me to edit it because of lack of permission).

I run it by assigning one of the windows keys as a shortcut. Or from the menu "add to panel". Using the latter you could modify the command as given above.

---

### Post by philinux on 2009-07-12
Even easier

```
gedit ~/.bashrc
```

add a line like this at the end, pick your own directory.

cd Desktop

or

cd /home/UserName/Documents/AnotherDir


Save file.

---

### Post by gasto on 2009-07-13
Hi, thanks for the info.

---

### Post by CatKiller on 2009-07-14
A couple of things in addition to the above posts.

There is a nautilus script in the repository that will let you open a Terminal with the current directory set to whatever the location is where you right-click and select it. So if you're browsing round your files and you realise you want to open a terminal at that location it's simple to do so. The above posts answer the question that you asked, but you might not have been aware of this option.

Also, don't use sudo for gedit (or any graphical application). Use gksudo instead.

---

