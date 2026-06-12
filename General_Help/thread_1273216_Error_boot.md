---
title: "Error boot"
date: 2009-09-23
forum: General Help
---

### Post by GahocIT on 2009-09-23
When I was power on computers and load boot it error
I don't want load [SIZE="4"]Starting up.....[/SIZE]
[CENTER][IMG]http://i81.servimg.com/u/f81/11/91/56/19/p1000610.jpg[/IMG][/CENTER]

I want boot to flat after power on computers 
[CENTER][IMG]http://www.pureelite.co.uk/wp-content/uploads/2009/04/bootscreen.jpg[/IMG][/CENTER]

Sorry, my English very bad

---

### Post by oldfred on 2009-09-23
You can download startup manager from Synaptic and you the checkbox on the first screen to control if text is shown.

or you can edit /boot/grub/menu.lst lines like this: 

kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f9b2a783-78ba-4437-9bc5-9d8cfa86ff0c ro splash quiet 

The splash and quiet control what is shown.

---

