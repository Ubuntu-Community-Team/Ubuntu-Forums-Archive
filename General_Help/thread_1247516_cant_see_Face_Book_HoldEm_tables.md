---
title: "cant see Face Book HoldEm tables"
date: 2009-08-23
forum: General Help
---

### Post by adirse on 2009-08-23
I use face book on the pc with windows and no problems there.
but at my laptop with my ubuntu I cant see the tables (flash 10)..
both computers are using Mozilla Firefox.
I've installing all the updates and flash 10 included.
what can I do to play with my ubuntu at the Face Book HoldEm poker and see the tables and servers lists?

---

### Post by mbuehl on 2009-08-23
> **adirse said:**
> I use face book on the pc with windows and no problems there.
but at my laptop with my ubuntu I cant see the tables (flash 10)..
both computers are using Mozilla Firefox.
I've installing all the updates and flash 10 included.
what can I do to play with my ubuntu at the Face Book HoldEm poker and see the tables and servers lists?


you'll find your flash issues likely extend beyond just this particular instance.... heh. I can't get mine to work at ALL! and if it does, it's choppy or just broken.

I assume you have ran 

sudo apt-get install flashplugin-nonfree

and that it returns the program being fully updated/configured?


Stupid question probably but did you try rebooting after installing flash?[COLOR=#677788][FONT=Arial][COLOR=#677788][COLOR=#677788][COLOR=#677788][/COLOR][/COLOR][/COLOR][/FONT][/COLOR]

---

### Post by adirse on 2009-08-23
> **mbuehl said:**
> you'll find your flash issues likely extend beyond just this particular instance.... heh. I can't get mine to work at ALL! and if it does, it's choppy or just broken.
 
I assume you have ran 
 
sudo apt-get install flashplugin-nonfree
 
and that it returns the program being fully updated/configured?
 
 
Stupid question probably but did you try rebooting after installing flash?
 
 
**thank you.. but sudo and restart didnt help.**

---

### Post by mbuehl on 2009-08-23
alright.

i fixed mine, maybe this will help you out.

open console, type the following in (type 1 line, push enter, confirm removal/install/whatever, then when it finishes go on to the next line)

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
This removes the other versions of flash from your computer, and freshly installs ver 10 flash.

fixed my issues with flash pretty quick! good luck

---

### Post by adirse on 2009-08-23
> **mbuehl said:**
> alright.
 
i fixed mine, maybe this will help you out.
 
open console, type the following in (type 1 line, push enter, confirm removal/install/whatever, then when it finishes go on to the next line)
 
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
This removes the other versions of flash from your computer, and freshly installs ver 10 flash.
 
fixed my issues with flash pretty quick! good luck
 
 
typed all this. line by line. no good.
still not working..

---

