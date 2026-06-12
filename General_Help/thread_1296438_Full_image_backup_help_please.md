---
title: "Full image backup help please"
date: 2009-10-20
forum: General Help
---

### Post by garnold on 2009-10-20
I wanted to play around with Wine and try to install some Windows apps. Before I did this I was hoping to make a full backup of the system so I could restore it. I used Windows HomeServer for this in the Windows world. Can I get some help on how to make a full image backup of my Ubuntu install to either an external HD or network location? Thanks

---

### Post by Mark Phelps on 2009-10-20
There are several apps available for doing this, but the more sophisticated ones take a lot of setup and configuring to work right.

A simple partition backup/restore app is P.I.N.G (Partimage Is Not Ghost) -- a frontend to the Partimage program that provides text-based menu screens in which you select the partitions to be backed up, a place to store them, and a name for identifying them.

The product download is an ISO which, when burned to a CD, can be booted and performs both the backup and restore from that CD; thus, it can even work when your OS is completely hosed.

For more information, go to windowsdream.com and read the PING information.  The product is free, of course.

---

### Post by mocoloco on 2009-10-20
Since Wine is installed and run entirely by one user you don't need to back up your whole system, just that users home folder.  Even easier do what I do, create a new user just for your wine stuff and at any point you can just remove that user and it's home folder and all is gone.

---

### Post by garnold on 2009-10-20
> **mocoloco said:**
> Since Wine is installed and run entirely by one user you don't need to back up your whole system, just that users home folder.  Even easier do what I do, create a new user just for your wine stuff and at any point you can just remove that user and it's home folder and all is gone.

Woo you mean all the Wine install stuff in just placed in the single users home directory and not splattered all over the OS?

This is a really cool idea! I'm going to download PING for my full backup just in case I mess other stuff up too :)

What I did in the mean time was since I already use VirtualBox I grabbed a Ubuntu image from them and will test on that.

Thank you both for you excellent ideas!

---

### Post by kaibob on 2009-10-20
You may want to have a look at the following current thread, which deals with imaging a hard drive. 

[http://ubuntuforums.org/showthread.php?t=1287019](http://ubuntuforums.org/showthread.php?t=1287019)

I recently began using Clonezilla and like it a lot.

---

### Post by mocoloco on 2009-10-21
Yeah, just a bit more handy info:
When you first run wine's configuration or any wine app it creates the default .wine folder. (Any folder that starts with a dot is a hidden folder in Linux.)  Poking around in there you'll see the fake drive c, along with the files that serve as the fake registry.
Other than that folder wine puts stuff in a couple of other places to add your windows apps in to the menu.  Unfortunately currently these don't get removed when you uninstall through wine.  This will clear those out
```
 rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm 
```

So removing those and removing the .wine folder would clear everything wine's put in.

---

