---
title: "Reinstall ubuntu, with the same configs"
date: 2010-08-21
forum: General Help
---

### Post by behzadsh on 2010-08-21
hi everyone,

because of some partition problem, I have to format my hard disk.

Is there any way to back up all my config files, downloaded softwares and upgrades...
I wish when I reinstalled ubuntu with a simple backup recovery get all my data back, Is it possible? I mean, I don't want to download upgrades i downloaded before and set up some configs that I did before...

thanks,
and apologizing for my bad English :oops:

---

### Post by earthpigg on 2010-08-21
hi,

remastersys.

it will convert your entire install into an .iso that you can either burn onto a dvd or put on a thumb drive using unetbootin or ubuntu's usb startup disk creator (try both, be sure to test).

---

### Post by behzadsh on 2010-08-21
Thanks for your help ;)
--
I will check it and will report

---

### Post by behzadsh on 2010-08-21
Just another question...
what about other program listed in [COLOR=Navy]**[http://en.wikipedia.org/wiki/List_of_remastering_software](http://en.wikipedia.org/wiki/List_of_remastering_software)**[/COLOR]

thanks

---

### Post by deserthowler on 2010-08-21
I had a problem with remastersys.  It might be fixed now.  It wouldn't install.

Open Synaptic and check if the following programs are installed; ubiquity, ubiquity-frontend-debconf, ubiquity-ubuntu-artwork, ubiquity-casper and ubiquity-frontend-gtk..  Install any that are not installed. 

Live CD runs OK but not install without this fix.

Earl

---

### Post by earthpigg on 2010-08-21
sooo install those packages before creating the .iso :D

ubiquity is the installer. if we want our LiveCD to contain an installer, we have to include it on the system we are baing the LiveCD on.

you can uninstall ubiquity after creating the LiveCD if you wish.

---

### Post by behzadsh on 2010-08-22
I had a problem with remastersys.
I've selected **Backup complete System including User Data**, after some calculations it tells me:
> 
The compressed filesystem is larger than the iso9660 specification allows for a single file. You must try to reduce the amount of data you are backing up and try again.


what should I do now?
Is it possible to make several DVD?

---

### Post by earthpigg on 2010-08-22
> **behzadsh said:**
> > The compressed filesystem is larger than the iso9660 specification allows for a single file. You must try to reduce the amount of data you are backing up and try again. 


what should I do now?
Is it possible to make several DVD?

well, some of your user data is certainly not part of the system's configuration right?

back up your entire /home folder separately, then select the option not to back up 'user data'. your home folder = user data, and that doesn't need to be in the .iso.

---

### Post by behzadsh on 2010-08-22
thanks for you helping earthpigg, but I think my system configuration back up is about 10GB :D

I tried once again and that message shown again

---

### Post by earthpigg on 2010-08-22
if it is, that's a rather huge install.

we can find out what's taking up the space: 

system -> accessories -> disk usage analyzer -> scan filesystem

discount /home, because we will be backing that up separately.

---

