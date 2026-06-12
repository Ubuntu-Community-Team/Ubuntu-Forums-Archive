---
title: "root password"
date: 2009-10-20
forum: General Help
---

### Post by blur xc on 2009-10-20
I know, I know, there are tons of threads on why you shouldn't create a root password, or enable the root user account, etc., and I believe it.  But- I ran into a case where my only solutions was to create a root password.

tubo print- whenever I needed to change something in regards to our canon printer, turbo print would aks for my root password.  My login password woudln't work, so I followed the ubuntu kung fu instructions on how to enable the root account, and give it a password, that I was able to get past those stupid root password prompts.  Is there another way?  Once you enable the root account, how can you disable it?

thanks,
BM

---

### Post by Bachstelze on 2009-10-20
> **blur xc said:**
> Is there another way?

Probably. Is the program asking for your root password a GUI or CLI one?

> **blur xc said:**
> Once you enable the root account, how can you disable it?

```
sudo passwd -l root
```

---

### Post by blur xc on 2009-10-20
> **Bachstelze said:**
> Probably. Is the program asking for your root password a GUI or CLI one?



```
sudo passwd -l root
```

It's a gui program.  Really frustrating.  I tried and tried to not give root a password, but I finally did, and it worked fine.  Now I can disable it, and just re-enable it when I need to.  Better yet- I'll get an HP pritner w/ Linux drivers, and @!#!$ can turbo print along w/ that canon printer.  Thorn in my side...


thanks much!
BM

---

### Post by mikewhatever on 2009-10-20
You can easily get root prompt in Terminal with sudo -i, or by booting into recovery mode, rather then enable root login just to deal with a printer.

---

### Post by Bachstelze on 2009-10-20
> **blur xc said:**
> It's a gui program.  Really frustrating.  I tried and tried to not give root a password, but I finally did, and it worked fine.  Now I can disable it, and just re-enable it when I need to.  Better yet- I'll get an HP pritner w/ Linux drivers, and @!#!$ can turbo print along w/ that canon printer.  Thorn in my side...


thanks much!
BM

What happens if you run the program with gksudo? Does it still ask for the root password?

---

### Post by blur xc on 2009-10-20
I never tried that- I actually don't even know how to run the program except from the gui.  After going to system-> administration-> printers, select the printer, and try to change any properties about it, the dialog asking for the root password would pop up.  I can't try to recreate the problem right now.  It's a network printer on our home wifi, and we recently changed our router.  To get it back on the network, I have to plug it into a windows computer w/ the usb cable, uninstall all the canon software and drivers, and reinstall it all, according to Canon tech support.  It took over an hour last time.  It's ridiculous that I can't select a network to connect to, and enter the new pass-phrase on the printer or load settings from a usb stick.

Thanks,
BM

---

