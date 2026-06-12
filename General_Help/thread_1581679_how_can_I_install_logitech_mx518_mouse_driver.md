---
title: "how can I install logitech mx518 mouse driver?"
date: 2010-09-25
forum: General Help
---

### Post by warakawa on 2010-09-25
I need to download the driver so that I can get the buttons to work on the mouse. I couldn't find any driver for ubuntu. What can I do?

---

### Post by lykeion on 2010-09-25
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by warakawa on 2010-09-25
is there a way to configure without going through terminal?

---

### Post by warakawa on 2010-09-26
I found[URL="http://www.linuxforums.org/forum/hardware-peripherals/58668-mouse-logitech-mx.html"] this thread, 
[/URL]
I want to which version of xorg.conf so that I can put in the right code. 

after do I just restart my computer?

thanks. 
[]("http://www.linuxforums.org/forum/hardware-peripherals/58668-mouse-logitech-mx.html")

---

### Post by lykeion on 2010-09-26
I haven't tried this myself but maybe this program is the easiest solution: [http://www.hidpoint.com](http://www.hidpoint.com)

About the link you posted, you should know that from Ubuntu version 9.10 the xorg.conf isn't used anymore by default. 
You could generate a configuration file but that would involve the command-line.

Maybe someone else can explain Xorg, xinput, udev in an easy way to a user not used to using command-line.

---

### Post by warakawa on 2010-09-26
They say that linux has the best support community... after two day of ubuntu, I can't get even get my mouse to work properly, some thing that only took me 5 minutes with Windows. Logitech is one of the most popular brand of mouse there is on the market and I can't find a crap about it on the internet that shows you step by step instruct on how to install it on ubuntu. 

And the support community isn't so helpful either, I just can NOT believe out of all the people on this forum, no one uses mx518 or similar model on 10.04.

---

### Post by P4man on 2010-09-26
Maybe you should ask for a refund?
Seriously you get help in a matter of minutes/hours and it cost you zilch. Its not like you are paying us to use ubuntu, if you dont like it, dont use it.  If you want faster or better support, go here:
[http://shop.canonical.com/product_info.php?products_id=715](http://shop.canonical.com/product_info.php?products_id=715)

FWIW, I can not get half my buttons on my old keyboard and mouse (a logitech wireless set) to work on windows 7 64 bit. It took logitech 5 days to respond and say logitech no longer supports it. 

I get nearly all of them working on ubuntu.

---

### Post by warakawa on 2010-09-26
> **P4man said:**
> Maybe you should ask for a refund?
Seriously you get help in a matter of minutes/hours and it cost you zilch. Its not like you are paying us to use ubuntu, if you dont like it, dont use it.  If you want faster or better support, go here:
[http://shop.canonical.com/product_info.php?products_id=715](http://shop.canonical.com/product_info.php?products_id=715)

FWIW, I can not get half my buttons on my old keyboard and mouse (a logitech wireless set) to work on windows 7 64 bit. It took logitech 5 days to respond and say logitech no longer supports it. 

I get nearly all of them working on ubuntu.

I don't think people use ubuntu because it is free, windows 7 was free, it came with my laptop.

---

### Post by P4man on 2010-09-26
That doesnt make it free, the price is just included (and you could ask a nice refund if you dont use it).

Regardless, lykeion has given you several leads to solve the problem. If you want the problem fixed, then start reading and feel free to ask any questions you have, but just slamming him or the community when you get accurate answers within minutes isnt the way to get help.

---

### Post by dmizer on 2010-09-26
> **warakawa said:**
> They say that linux has the best support community... after two day of ubuntu, I can't get even get my mouse to work properly, some thing that only took me 5 minutes with Windows. Logitech is one of the most popular brand of mouse there is on the market and I can't find a crap about it on the internet that shows you step by step instruct on how to install it on ubuntu. 

And the support community isn't so helpful either, I just can NOT believe out of all the people on this forum, no one uses mx518 or similar model on 10.04.

You asked for and got a complete fix for your problem within an hour of posting. You simply chose to ignore it because it used the terminal.

If you need help with implementing the fix, please ask for it. It doesn't help to complain about a community not helping you when it indeed has. Since a fix has been posted, I am closing this thread to further comment. If you need help implementing the fix, or if the fix does not work, please feel free to open a new thread.

Thank you.

---

