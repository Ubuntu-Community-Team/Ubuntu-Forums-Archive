---
title: "why wont nouveau work with my nvidia card?"
date: 2010-04-23
forum: General Help
---

### Post by wagonfactor on 2010-04-23
this is inreference to 10.04. i have an nvidia 8700m gt in my laptop. ANY distro ive ever tried that uses nouveau doesnt seem to work. when i boot the live cd only the background and mouse load. you cant right click or do anything. and it stays like that. 8.04 was the first ubuntu i used and theyve all worked fine untill 10.04. fedora does the same thing (background and mouse only) and it also defaults nouveau.

i just downloaded the latest rc for ubuntu 10.04, bout to burn it, cross my fingers and give it a try. but im pretty sure i will encounter the same problem. 

has anyone run into this and possibly found a way around it? ive been googling for months and cant seem to find an answer.

oh, and yes, i can install 9.10, get it up to date and get the drivers, then upgrade to 10.04. but it takes soooo long and i have a bad habit of distro hopping :P (it literally takes about an hour and a half to install/update 9.10, then upgrade to 10.04 on my comp)

---

### Post by wojox on 2010-04-24
Why don't you just download the nvidia driver?

---

### Post by 3rdalbum on 2010-04-24
I don't know why Nouveau won't work with your graphics card - I hadn't heard of an 8700M, maybe it's quite obscure? In any case I'm sure the Nouveau folks would LOVE to hear from you. That is, assuming that the problem goes away when you use a different driver.

---

### Post by wagonfactor on 2010-04-24
i dont download the nvidia drivers because the OS is unusable. i literally cant do anything. i get a mouse cursor and a wallpaper, nothing else. cant right click, use keyboard shortcuts or anything.

and i guess ill make a post over at nouveau. i thought for sure another ubuntu user would have encountered this with 10.04.

ty for the replies :)

---

### Post by lidex on 2010-04-24
> **wagonfactor said:**
> i dont download the nvidia drivers because the OS is unusable. i literally cant do anything. i get a mouse cursor and a wallpaper, nothing else. cant right click, use keyboard shortcuts or anything.

and i guess ill make a post over at nouveau. i thought for sure another ubuntu user would have encountered this with 10.04.


Maybe you should look over at the lucid forum:
[http://ubuntuforums.org/forumdisplay.php?f=377]("http://ubuntuforums.org/forumdisplay.php?f=377")

---

### Post by 3rdalbum on 2010-04-24
Ubuntu 10.04 still has the old 'nv' driver, you can drop to the terminal and edit xorg.conf to enable it.

---

