---
title: "how to share and view network servers"
date: 2010-05-12
forum: General Help
---

### Post by rmcellig on 2010-05-12
When I was using Ubuntu, I would go to Places-Network to view the other computers on my network. Now that I am using Xubuntu, I can't for the life of me figure out how to do this as well as how to share files and folders in Xubuntu.

Is it possible and is there a GUI solution?

---

### Post by ubunterooster on 2010-05-12
In my xfce I use nautilus :|

---

### Post by rmcellig on 2010-05-12
How exactly can I use Nautilus in xubuntu? I am pretty new to Linux.

Is there a way to use file sharing and access network servers using the xubuntu file manager?

If I use Nautilus in Xubuntu, will that utilize more resources? I have an older computer from around 2003 and find xubuntu works great on it.

---

### Post by ubunterooster on 2010-05-12
I start it by either making a short cut or by pressing alt+f2 then typing in "nautilus"

Using Thunar to do file sharing; don't know about that but you could use just the regular samba gui

Nautilus does take up some more resources but it is not that significant

---

### Post by rmcellig on 2010-05-13
I was able to invoke Nautilus with alt-F2 but how can I make an alias of it?

Thanks so much for your help!!

I am in the middle of installing Samba to see if I can get file sharing to work.

---

### Post by ubunterooster on 2010-05-13
"add to panel" a "custom launcher". In the box where it wants a command type "nautilus"

---

### Post by rmcellig on 2010-05-13
That was easy!! Thanks again!! Is there a way to make the Nautilus browser my default broser while I am in Xubuntu?

---

### Post by ubunterooster on 2010-05-13
I'm _still_ trying to figure that out, personally ;)

---

### Post by rmcellig on 2010-05-13
Thanks again for all of your help!! I want to add Samba to my launcher. What command can I use to launch it and how do I know what command to use when I add something to my launcher?

---

### Post by ubunterooster on 2010-05-13
gksu system-config-samba


I'm not sure how you figure them out, honestly; I just know them :/

---

### Post by rmcellig on 2010-05-13
Thanks!

---

### Post by ubunterooster on 2010-05-13
Not a problem. :D

---

### Post by RyanRahl on 2010-05-26
You don't need Nautilus for network browsing in Xubuntu. You can use Thunar (the one it comes with) by using gigolo.

go to the terminal and type

user@localhost:/# sudo apt-get install gigolo

Xubuntu uses Thunar because it is more lightweight than Nautilus. Using Nautilus defeats the propose of Xubuntu.

---

### Post by ubunterooster on 2010-05-26
"gigolo"?
Okay, thanks.

---

