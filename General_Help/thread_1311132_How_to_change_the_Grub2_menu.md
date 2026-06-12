---
title: "How to change the Grub2 menu?"
date: 2009-11-02
forum: General Help
---

### Post by selachiix on 2009-11-02
Hi everybody,

Today I installed Ubuntu 9.10. (Also first time I'm using "Linux" :) )
I want my Windows 7 partition to be the default OS to boot.
I've been searching on google on how to change the menu but everything I find is about /boot/grub/menu.lst. The problem is that I didn't find that file. Then I found out that menu.lst doesn't exist anymore, cause it's now Grub2.
Some people say that you need to edit grub.conf but I have no idea at all what I need to change.

What should I do to have Windows 7 as the default OS in Grub2?
(Please keep in mind I'm a newbie :p )

Thanks in advance!!!

Simon

---

### Post by ranch hand on 2009-11-02
Read the link in my sig.

The links in it are to more info.

You need to change the default number in /etc/default/grub.

---

### Post by selachiix on 2009-11-02
Thanks! I'll check it out ;)

---

### Post by Uncle Spellbinder on 2009-11-02
In Synaptic, search *startupmanager*, install it.............

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/StartUpManager.jpg[/IMG]

---

### Post by selachiix on 2009-11-02
Thanks Uncle Spellbinder for your reply! I'll try it out.

@ranch hand: It was easier than I thought!

I edited the /etc/default/grub and set the default value to 4 and did a sudo update-grub and that's that :D

Thanks guy's for your help! ;)

---

### Post by ranch hand on 2009-11-02
I would be real careful about using SUM at this point.  It is being rewritten, right now, so that it will be compatable with grub2.  It really is not yet fully functional in the grub2 environment.  Should be soon.

---

### Post by Glugglug on 2009-11-02
In the previous  startup manager  you had the option to add a bit of colour to Grub   but  there isn't that option anymore . 


You could choose  a background  colour  and a text colour.

---

### Post by ranch hand on 2009-11-02
Read the link in my sig.

You can change the background to any image you want and the font to something that will show up on that image.  I use my wallpaper from menu to xsplash to GDM and back to xslpash and then wallpaper at fully booted.

FUN

---

