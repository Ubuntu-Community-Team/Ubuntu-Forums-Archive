---
title: "Icons for Shutdown Dialog"
date: 2011-03-28
forum: General Help
---

### Post by jesuisbenjamin on 2011-03-28
Hello there,

I recently installed the latest Faenza icon set. To shut down the computer i use the gnome-session shut-down dialog (which is activated by an applet in Cairo-Dock). The equivalent command line is: [FONT="Courier New"]gnome-session-save --shutdown-dialog[/FONT]

One thing however is that the shut down dialog does not display the icons Faenza supposedly is providing with. The "restart" and "hybernate" icons show alternate icons--[see screenshot]("https://lh4.googleusercontent.com/_7mkhSDYn8TQ/TY7XSKbt2KI/AAAAAAAACPM/fxD_uzoY694/Screenshot.png")--all four icons should be of the silverish/metalic type.

I believe i simply need to create two icons with the proper name as the dialog expects to find them. That's the problem really: **how can i find out the icon names required by the dialog? **

Thanks.
Benjamin

---

### Post by jesuisbenjamin on 2011-04-07
Bump

---

### Post by jesuisbenjamin on 2011-04-22
Just thought i'd bounce this one...

---

### Post by PC_load_letter on 2011-06-28
Same exact problem here. Bump of the month :D

---

### Post by joejoe74236 on 2011-09-03
i'll bump as well. still can't find a thing about this problem anywhere.

---

### Post by whatthefunk on 2011-09-03
Find the icon files.  I use Lubuntu so cant help you find them, but they are probably called something like "gnome-session-hibernate.png" "gnome-session-switch.png" etc.  In a terminal, try using the locate command, something like 
```
locate hibernate
```
Once you find the icon that you want to replace, change its name and create a symoblic link to the new icon.  For example, if I wanted to change the hibernate icon, I would do the following:
Change the original icons name
```
sudo mv gnome-session-hibernate.png gnome-session-hibernate1.png
```
Create a symbolic link to the icon that I want to display
```
ln -s /home/username/.icons/Faenza/apps/scalable/gnome-session-hibernate.svg gnome-session-hibernate.png
```

This is kind of a rough work around, but it should work.  Please keep in mind that I use Lubuntu and my file structure is slightly different than yours so edit the paths in the code above to match those of your system...

EDIT:
While youre digging around in your file system, take note of what your icons are called.  This might simply be a matter of changing the name of the Faenza icon to match the name of the icon that Ubuntu uses.

---

### Post by jesuisbenjamin on 2011-09-04
It's kind of mad cause I was thinking about this earlier today and here you are with your answer :)

Thanks.

---

### Post by whatthefunk on 2011-09-04
> **jesuisbenjamin said:**
> It's kind of mad cause I was thinking about this earlier today and here you are with your answer :)

Thanks.

Did it work?

---

### Post by jesuisbenjamin on 2011-09-04
I didn't try--because I moved on without using the shut-down dialogue. But I am not looking at it and think: isn't the problem than the dialogue points to the wrong icons rather than the icons missing?

For instance the restart icon is not used, and the refresh icon is used instead. Now if I link the refresh icon to restart, it might fix the problem, but it also will be messed up when another dialogue wants to show a refresh icon and will provide the restart instead.

IMO the best solution would be to make a new dialogue for this, which is not a big task really. I'm working on some other project, but I'll see if I recreate this dialogue.

---

