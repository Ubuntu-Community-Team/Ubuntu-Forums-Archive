---
title: "Slow Ubuntu"
date: 2006-01-27
forum: General Help
---

### Post by zainka on 2006-01-27
[-o< Should have posted thisone in the beginner forum... SORRY

I am new to Linux and decided after peeping around a bit to let Ubuntu distro have the honor to introduse me into the world of Linux, and I do not think I am going to regret this decission when I am setteled. By reading this forum I see that most users are happy with Ubuntu which tells me that Ubuntu is a good choice. However, as always when evolving into a higher computer platform level (i.e. from the lowgrade w2k plattform) there is new contry to discover and both laughter and tears yet to experience.

My trouble is that when running Ubuntu everything is wery slow speed. I.e. Ubuntu respond very slowly to my actions like when opening programs, looking into prefferences etc. Firefox for example spends almost 30 to 45 seconds to start up, and even more trying to open a simple page which loads very fast when running  firefox on [SIZE="2"][SIZE="1"]w2k[/SIZE][/SIZE] on the same computer, and running several programs (say 3) and when switching between them, it goes ages (from 30secs to 1.5 miutes) from the time when I want to change focus (i.e. clicking on a unfocused window) until focus switches, meanwhile my computer hangs or respond and acts even slower. [SIZE="1"]I do not have such problems when running w2k partition.[/SIZE]

I guess these things has someting to do with my configuration setup and possible my machinewarez. I am still running on an P2 processor 533MHz with 256kB RAM. Ubuntu is starting up with the default kernel options as beeing selected by installation cd. Ubuntu partition is app. 14GB using ext3. [SIZE="1"]w2k[/SIZE] is installed on its own partition with NTSF. Any help or pointers to other treads / tutorials would help. 

Second. By default the GRUB bootloader was installed making me able to select OS at power-up. Is there someway that I can tell GRUB to always start [SIZE="1"]w2k[/SIZE] after say 30 secs by default if no other choices are done or do I need a another bootloader. Whataboute the one implemented in [SIZE="1"]w2k[/SIZE]. How do I eventually get rid of GRUB?

Thanks in advance
Vidar (Z)

---

### Post by StefanoCole on 2006-01-27
About Grub read the following wiki: [https://wiki.ubuntu.com/GrubHowto]("https://wiki.ubuntu.com/GrubHowto")

Stefano

---

### Post by Perfect Storm on 2006-01-27
Firefox on ubuntu is slow, you might try to install firefox 1.5 which you can find in the HOwto forum or try another browser as epiphany.
Also you might get kernel i686 for your pentium machine and setup your graphic card to speed up te performance.

> P2 processor 533MHz with 256kB RAM

I would recommend that you use a lightweight desktop. You can try with xubuntu which have XFCE as DE. Other choice which I recommend is Openbox.

---

### Post by Lord Illidan on 2006-01-27
I assume you mean MB of RAM... 256 kb... you wouldn't have gone past the installation!!

About the GUI.. GNOME's metacity is extremely slow.. you might want to try Xubuntu.

Or else, even consider another distro like puppy linux.

And I don't think you can remove Grub.. The Windows bootloader doesn't recognise your Linux partition AFAIK...

---

### Post by simon_is_learning on 2006-01-27
[QUOTE=Artificial Intelligence]
Also you might get kernel i686 for your pentium machine and setup your graphic card to speed up te performance.
.[/QUOTE]

How much speed can you gain on that?
I've got an PIII 667MHZ
dumb question maybe, but how do i know if it's an i686?

---

