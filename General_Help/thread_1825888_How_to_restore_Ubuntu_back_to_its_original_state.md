---
title: "How to restore Ubuntu back to its original state?"
date: 2011-08-15
forum: General Help
---

### Post by Comkore on 2011-08-15
Hello everyone,

I recently had a problem in Ubuntu 11.04. I had just installed GNOME 3, however, I didn't really like it as much so I decided to go back using GNOME 2,but then a whole bunch of things happened. I tried re-installing GNOME 2,but then I lost the Ubuntu enviorment and stuck only with GNOME and now I'm only left with a terminal whenever I log in.

Does anyone know how to restore Ubuntu 11.04 back to its original state, like as if it had a fresh installation? 

I don't want to backup and restore, just a complete restoration.

The help would be appreciated ^^

Thanks

---

### Post by angry_johnnie on 2011-08-16
unfortunately, there's nothing that resembles windows' system restore.

if you're booting into a terminal, you could try re-installing ubuntu desktop.

you could try

```
sudo apt-get install ubuntu-desktop
```

or

```
sudo apt-get install --reinstall ubuntu-desktop
```

if it's still installed, but borked.

or

```
sudo dpkg-reconfigure ubuntu-desktop
```

that should fix it, too, although i'm not entirely sure :p


on the other hand, are you sure it's the desktop that's messed up, and not your display driver?

have you tried running

```
startx
```

when you get to the terminal?


whether it works or not, it may give you a hint about what's really wrong with it.

---

### Post by Comkore on 2011-08-16
I did try "sudo apt-get install ubuntu-desktop" in terminal but it didn't worked ,which got me very confused. I will try the others though, thanks.

---

### Post by pqwoerituytrueiwoq on 2011-08-16
since you have to use a ppa to get gnome 3 you can use the ppa-purge package to remove it
i know it is available in the ubuntu-x-swats ppa
assuming you do not have this package available for install
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get install ppa-purge
```
i dont konw how to use it as i have not needed to but based on the description it should be very useful

---

### Post by Comkore on 2011-08-16
Well I tried everything so far and nothing worked, I think I must have accidentally uninstalled ubuntu-desktop.However I can use your codes angry_johnnie,but I need a internet connection going,but I'm not really sure how to do that in terminal can you show me?

I am very sorry if I'm wasting your time. I'm sort of a newbie to Linux.

---

### Post by Comkore on 2011-08-16
Thanks for the help though pqwoerituytrueiwoq, but if I can only get an internet connection going then I'll be able to fix ubuntu

---

### Post by angry_johnnie on 2011-08-16
you wouldn't need a connection to run dpkg-reconfigure.

by the way, you could also try

```
sudo dpkg-reconfigure -a
```

that would reconfigure everything you have.


other than that, i think you could connect by running something like this

```
ifconfig
```

that would show you your available interfaces.  say, for example, you have eth0 available as your ethernet interface.  you would then run

```
sudo ifconfig eth0 up
```

you'd just need to replace eth0 with whichever interface you happen to have.

you could also use your installation cd as an offline repository.

you would need to run

```
sudo nano /etc/apt/sources.list
```

at the very beginning of the file, you should have a line that reads "# deb cdrom:[Ubuntu... and so on..."

all you would need to do is uncomment that line (remove the #).  you may also need to comment out (add #'s at the beginning) all the other lines, but i'm not sure about that. :p

in order to save a file in nano, you must press ctrl + O (notice that's Oh, not zero).
to exit out of nano, you must press ctrl + X

then you'd run

```
sudo apt-get update
```

and then

```
sudo apt-get install --reinstall ubuntu-desktop
```

this way, instead of downloading it from the internet, it would re install it from your original ubuntu installation cd.

---

### Post by Comkore on 2011-08-17
Nice, thanks ^^

---

