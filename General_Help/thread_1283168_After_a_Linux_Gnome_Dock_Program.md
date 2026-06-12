---
title: "After a Linux Gnome Dock Program"
date: 2009-10-05
forum: General Help
---

### Post by Rick Abraham on 2009-10-05
Hi guys Im wanting a dock program but one that doesnt use Compiz, I have Compiz on my machine but when I activate it, it slows my application launch times considerbly.
I have found a number of dock programs that dont need Compiz but they are only for 32bit versions of Ubuntu and Im using 64bit.

I forced the installation of the 32 bit .deb package anyway but it didnt work.
So Im wanting to know if anyone knows of a good dock program that works with 64bit Ubuntu and doesnt need Compiz ???????????

---

### Post by the_hardy_kid on 2009-10-05
Try AWN.
Stands for Avant Window Navigator. Lotsa fun :)

---

### Post by Rick Abraham on 2009-10-05
I tried AWN but that requires Compiz, I have no idea why my machine slows down when Compiz is activated.
I have 8GB DDR2 RAM, Intel T8300 2.4GHz Duo CPU but only a 256mb ATI 3650 Graphics Card.
That might be causing the bottle neck with Compiz working.

---

### Post by the_hardy_kid on 2009-10-05
It "requires" compiz?
It ran fine on my machine. It has 256MB of ram and cannot run compiz...?

---

### Post by Rick Abraham on 2009-10-05
I just installed Avant again and when I try and run it, I get this error.

Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

When I activate Compiz it works fine but slows application launch times down.

---

### Post by fabounet on 2009-10-05
Cairo-Dock doesn't require composite.

---

### Post by ankspo71 on 2009-10-05
Hi,
You have the option to use gnome compositing too. 

open the terminal and type
```
gconf-editor
```

When it opens, navigate to Apps > Metacity > General
then check the box next to "compositing_manager"

You should see shadows added to your desktop, and will allow for transparency in the dock. Warning ahead of time... many people will say the gnome compositing is glitchy. I don't know if everybody has that trouble though. It flickers for me sometimes.

If you cant find a dock that doesn't need compositing to look good, or don't like all compositing at all because it slows down your system, you can always create a fake dock using an empty gnome panel at the bottom of the screen. Then make it transparent in the panel preferences, or add a custom background, then simply drag your favorite icons to it. The biggest disadvantage to this is the icons won't center themselves with a full panel. I used to do this on my other computer that had really low resources.
James.

---

### Post by ankspo71 on 2009-10-05
> **Rick Abraham said:**
> 
When I activate Compiz it works fine but slows application launch times down.

Oh, I think I know what you mean now. It takes a bit of time for applications to fade in and out of the screen, as part of the special effects. You can adjust this, or completely disable certain special effects, using Compiz Congfiguration Settings Manager. 

to install it open a terminal and type
sudo apt-get install compizconfig-settings-manager

Unless you really do mean compiz (in general) really does slow down your computer. PS. Sorry, I'm not aware of any docks created specifically for 64bit systems... I'm a 32bit user.
James

---

