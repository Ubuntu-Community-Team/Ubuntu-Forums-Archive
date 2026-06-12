---
title: "menu bare top reset"
date: 2009-11-01
forum: General Help
---

### Post by Thomaslje on 2009-11-01
hi I removed one of the icons in the menu bare at the top is there a way to set it to defult/reset it I removed the icon right next to the time the icon that had shut down ad reboot and so on

and it's 9.10

---

### Post by PorkyPie on 2009-11-01
Which icon was it? You can put it back by right-clicking the panel and clicking "Add to Panel". Then, select the icon you removed.

---

### Post by Thomaslje on 2009-11-01
ok I just want to reset the menu bar because it's totally meshed up

---

### Post by PorkyPie on 2009-11-01
Ok... now i know what you are trying to do. Firs of all, run this command in a terminal:

```
sudo nautilus ~/.gconf/apps
```Delete the folder "panel". Now, re-login and everything should be back to normal.

You might have to do the command in a shell before logging in.

By the way, this is a re-write of the tutorial here: [http://www.celsius1414.com/2006/08/31/how-to-reset-gnome-panel-to-default-in-ubuntugnome2](http://www.celsius1414.com/2006/08/31/how-to-reset-gnome-panel-to-default-in-ubuntugnome2)

...as it contained a possibly malicious code, [http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

---

### Post by Thomaslje on 2009-11-01
when I run the sudo nautilus ~/.gconf/apps command it says [sudo] password for thomas: what to do

---

### Post by Thomaslje on 2009-11-01
when I run the sudo nautilus ~/.gconf/apps now it says coulden find "/home/thomas/.gconf/apps".
check the spelling 


thomas@thomas-laptop:~$ sudo nautilus ~/.gconf/apps
[sudo] password for thomas: 

(nautilus:3488): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
thomas@thomas-laptop:~$ sudo nautilus ~/.gconf/apps


(nautilus:3493): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
thomas@thomas-laptop:~$ 
thomas@thomas-laptop:~$ sudo nautilus ~/.gconf/apps

(nautilus:3499): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed


so what to do 

and how to do the shell before logging in. in completely new to linux

sry for be a noob

---

### Post by Thomaslje on 2009-11-01
and if you dount know im running the notebook remix edition if that makes a different

---

### Post by PorkyPie on 2009-11-01
> **Thomaslje said:**
> when I run the sudo nautilus ~/.gconf/apps now it says coulden find "/home/thomas/.gconf/apps".
check the spelling 


thomas@thomas-laptop:~$ sudo nautilus ~/.gconf/apps
[sudo] password for thomas: 

(nautilus:3488): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
thomas@thomas-laptop:~$ sudo nautilus ~/.gconf/apps


(nautilus:3493): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
thomas@thomas-laptop:~$ 
thomas@thomas-laptop:~$ sudo nautilus ~/.gconf/apps

(nautilus:3499): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed


so what to do 

and how to do the shell before logging in. in completely new to linux

sry for be a noob

Don't worry about the shell for now. Try this in the terminal:

```
sudo nautilus /home/thomas
```

Now, type in your password when it asks:

```
[sudo] password for thomas: 
```

You won't see the password on screen. When you've entered it, click Enter on your keyboard. The file manager, "nautilus" should open in a new window. In view, at the top of the file manager, make sure that "Show hidden Files and Folders" (or something like that) is ticked. Now, try to find the folder ".gconf" and go into "apps". Try to delete the folder now.

Restart your computer, and everything should be back to normal. Hope this helps!

---

### Post by PorkyPie on 2009-11-01
> **Thomaslje said:**
> and if you dount know im running the notebook remix edition if that makes a different

Hmm.. that might make a bit of a difference. I'm not sure about it in the Netbook Remix, I'll see if I can find a way.

---

### Post by Thomaslje on 2009-11-01
> **PorkyPie said:**
> Hmm.. that might make a bit of a difference. I'm not sure about it in the Netbook Remix, I'll see if I can find a way.



thx that hope you will get this working for me

---

