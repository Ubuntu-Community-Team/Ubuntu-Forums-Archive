---
title: "Ubuntu 11.10: Nautilus crashes after 5 minutes."
date: 2011-10-14
forum: General Help
---

### Post by gepolv on 2011-10-14
Update:
Soved with the method in the following link:
[https://one.ubuntu.com/help/faq/how-do-i-install-the-gnome-ubuntu-one-client-on-kubuntu/](https://one.ubuntu.com/help/faq/how-do-i-install-the-gnome-ubuntu-one-client-on-kubuntu/)
---------------------------------------
I am running Ubuntu 11.10 and then I found a weird problem:  Nautilus crashes after around 5 minutes, which means after 5 minutes, when I hit "places->home folder" or other folders under "places" menu, it will crash. 

More, after around 5 minutes, all my icons on desktop are gone. But I can still see them through terminal.

Any suggestions?

-------------------------------------
I am using Gnome Classic
-------------------------------------

Thanks
Deryk.

---

### Post by gepolv on 2011-10-15
Nobody?

I am using Gnome Classic  desktop.

---

### Post by elnetotaca on 2011-10-15
open the terminal and type;
sudo apt-get --purge remove nautilus-open-terminal

and go for "y"

cheers.

---

### Post by cicoandcico on 2011-10-15
seems to be fixed:

[https://bugs.launchpad.net/ubuntu/+source/nautilus-open-terminal/+bug/865115](https://bugs.launchpad.net/ubuntu/+source/nautilus-open-terminal/+bug/865115)

just enable "proposed" updates and try it, or wait a few days.

---

### Post by gepolv on 2011-10-15
> **elnetotaca said:**
> open the terminal and type;
sudo apt-get --purge remove nautilus-open-terminal

and go for "y"

cheers.


Awesome! Works!

---

### Post by gepolv on 2011-10-15
New problem, after uninstalling Nautilus terminal, my "open terminal here" is gone.

Any way to fix it?


-------------------------------------
I am using Gnome Classic
-------------------------------------

Thanks.

---

### Post by athena3rm on 2011-10-16
I have the same problem, but when I try to purge and remove nautilus from the terminal the process gets interruptded... what can I do?:(

---

### Post by gepolv on 2011-10-16
> **athena3rm said:**
> I have the same problem, but when I try to purge and remove nautilus from the terminal the process gets interruptded... what can I do?:(

I have no problem to remove nautilus. If you cannot remove it, you can choose to remove ubuntuone-client-gnome. 

This phenomenon only happens in Gnome Classic.

The weird thing is nautilus and ubuntuone can co-exist in Unity. 

Any other thoughts?

Thanks
Deryk

---

### Post by zidangus on 2011-11-11
> **gepolv said:**
> New problem, after uninstalling Nautilus terminal, my "open terminal here" is gone.

Any way to fix it?


-------------------------------------
I am using Gnome Classic
-------------------------------------

Thanks.


This is a work around I found to allow you to still use the open terminal here, 

[http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/](http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/)

it works fine for me in ubuntu 11.10

---

