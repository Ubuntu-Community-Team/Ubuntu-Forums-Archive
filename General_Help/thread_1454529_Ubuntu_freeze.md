---
title: "Ubuntu freeze"
date: 2010-04-14
forum: General Help
---

### Post by Dr-a on 2010-04-14
after the installation of compize  I did a lot of settings to make some effects , when I did that my laptop froze ! :confused: 
I took the battery out :) and when I restarted ... it only shows ubuntu logo then it freeze during boot up ...

how can I fix this ? please help

---

### Post by Dr-a on 2010-04-14
please help :(

---

### Post by Dr-a on 2010-04-14
I need help please

---

### Post by Benchamoneh on 2010-04-14
Does pressing CTRL + ALT + F1 bring up a terminal window that you can log in with? Does your HDD activity light stay on? You could try disabling the Ubuntu splash screen and seeing where abouts your computer is freezing.

---

### Post by oleink on 2010-04-14
Did you change any access rights for any reason??

---

### Post by Rasa1111 on 2010-04-14
compiz completely screwed me up to man.
a few little pretty effects, that are also rather useless,  aren't worth it imho. 

 I understand it has something to do with my graphics card (has to)
because everything else in my machine should allow it to work. 

I decided id just do w/out "special effects". lol  :)

---

### Post by oleink on 2010-04-14
My graphics card is integrated garbage and my compiz works..

---

### Post by Rasa1111 on 2010-04-14
> **oleink said:**
> My graphics card is integrated garbage and my compiz works..

 :lol:  terrific.
 im ok w/out "a pulse" or "wobbly window" on my screen though.

---

### Post by oleink on 2010-04-14
I'm ok as long as its still ubuntu haha.  But i like compiz

---

### Post by Rasa1111 on 2010-04-14
haha, true that! :)

---

### Post by Dr-a on 2010-04-15
> **Benchamoneh said:**
> Does pressing CTRL + ALT + F1 bring up a terminal window that you can log in with? Does your HDD activity light stay on? You could try disabling the Ubuntu splash screen and seeing where abouts your computer is freezing.

what is splash screen and how can I disable it ?
Im a new ubuntu user

---

### Post by RobinJ1995 on 2010-04-15
I think trying to disable the usplash screen wouldn't solve anything.
I have the same problem when I apply some of the more "heavy" effects, then the GDM (or X I don't know) just freezes and doesn't start anymore.

Possible solution:
Choose the recovery option from your GRUB bootloader and go in a recovery shell.

First try this:
cd to your home directory and run
```
rm .compiz
cd config
rm compiz
```
Now your compiz configuration files should be reset.
Reboot and see if the problem's solved.

If the above didn't work you can try this:
Go to the recovery shell again and run
```
sudo aptitude purge compiz compiz-core compiz-gnome libdecoration0 compiz-wrapper compiz-plugins compiz-settings-manager compiz-fusion-plugins-main compiz-fusion-plugins-extra
```
Maybe just 'remove' in stead of purge could already be enough.
Then restart and maybe the problem is solved now.
If it isn't, you could reinstall the packages anyway.
If it's solved and you want your visual effects back, try reinstalling the packages 'cause their configuration files should be removed, so it should be safe for you to reinstall them :)

Good luck!

---

### Post by Dr-a on 2010-04-15
> **ErJeeB said:**
> I think trying to disable the usplash screen wouldn't solve anything.
I have the same problem when I apply some of the more "heavy" effects, then the GDM (or X I don't know) just freezes and doesn't start anymore.

Possible solution:
Choose the recovery option from your GRUB bootloader and go in a recovery shell.

First try this:
cd to your home directory and run
```
rm .compiz
cd config
rm compiz
```
Now your compiz configuration files should be reset.
Reboot and see if the problem's solved.

If the above didn't work you can try this:
Go to the recovery shell again and run
```
sudo aptitude purge compiz compiz-core compiz-gnome libdecoration0 compiz-wrapper compiz-plugins compiz-settings-manager compiz-fusion-plugins-main compiz-fusion-plugins-extra
```
Maybe just 'remove' in stead of purge could already be enough.
Then restart and maybe the problem is solved now.
If it isn't, you could reinstall the packages anyway.
If it's solved and you want your visual effects back, try reinstalling the packages 'cause their configuration files should be removed, so it should be safe for you to reinstall them :)

Good luck!


Thank you Ill try this 
but how can I enter to the Recovery shell 
and how can I write these orders ( I cant go to the terminal)
Im a new in ubuntu :confused:

---

### Post by Dr-a on 2010-04-15
^^^^
Please help

---

### Post by Rasa1111 on 2010-04-16
bump~ to help Dr-a.

---

### Post by Dr-a on 2010-04-16
^^
lol
still no help :confused:?

---

### Post by maddg3241 on 2010-04-16
can you get past the boot screen i think that i understand that you r stuck there right

---

