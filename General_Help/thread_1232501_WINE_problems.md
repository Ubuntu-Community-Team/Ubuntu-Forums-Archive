---
title: "WINE problems?"
date: 2009-08-05
forum: General Help
---

### Post by Cityscape on 2009-08-05
I finally have convinced my parents to switch to Ubuntu. :D 

But they want me setup a few Windows programs for them.
Okay I have WINE installed. I run the exe of the 2 programs and both installed successfully after installing .NET framework and other needed MS components.

But I can't get the program(s) to open.
It put 1*Program*.lnk and 1 *Program*.desktop files on my desktop.
Opening the .desktop brings up a window asking whether or not to open it, i click okay and wait and nothing happens. the .lnk says it's an unknown file type.

The programs show up in the Apps menu under Wine>Programs

How do i run these programs? they are Homeschool Tracker Plus and YNAB Pro.

---

### Post by XCan on 2009-08-05
That sounds like you're placing Windows shortcuts and trying to run them. You probably want to create launchers on the desktops instead. Right click on desktop -> Create Launcher, and type the command you would use to start them through wine, i.e., ```
 wine /path/to/app 
```

---

### Post by CatKiller on 2009-08-05
Not all programs work in Wine. Check the [Applications Database]("http://appdb.winehq.org/") for specifics.

---

### Post by MJClark505 on 2010-10-21
> **Cityscape said:**
> I finally have convinced my parents to switch to Ubuntu. :D 

But they want me setup a few Windows programs for them.
Okay I have WINE installed. I run the exe of the 2 programs and both installed successfully after installing .NET framework and other needed MS components.

But I can't get the program(s) to open.
It put 1*Program*.lnk and 1 *Program*.desktop files on my desktop.
Opening the .desktop brings up a window asking whether or not to open it, i click okay and wait and nothing happens. the .lnk says it's an unknown file type.

The programs show up in the Apps menu under Wine>Programs

How do i run these programs? they are Homeschool Tracker Plus and YNAB Pro.

I know this is a bit late, but I'm sure a few others are trying to get Homeschool Tracker Plus to run under Ubuntu.
[U]
This is my method that worked with **Ubuntu 10.10**[/U]

1. Install Wine via Ubuntu Software Center
2. Install Winetricks
```
sudo apt-get install winetricks
```3. Use Winetricks to install necessary windows packages. It may be better to install them one at a time instead of all at once so that if one installation does have an error, you can easily know and reinstall.
```
sh winetricks dotnet20 dotnet35 msxml6 gdiplus gecko vcrun2005 ie6 vcrun2010 mdac28 jet40 corefonts vb6run
```4. Launch Wine config
     -under Application add the installation file for Homeschool Tracker Plus and set it's Windows version to Vista
5. Right click on the Homeschool Tracker Plus installation file and choose "Open with Wine Windows Program Loader" and install it as you would in Windows

That should be all it takes :). Good luck!

Note: For future versions - HST Plus is built on a Microsoft Access database, so it will generally require the same files needed to install MS Office via Wine. If all else fails, find out what the current method is for installing MS Office and use that method for installing HST Plus.

---

### Post by Mark Phelps on 2010-10-21
Wish you the best of luck ... BOTH of those apps are rated Garbage in the WineHQ app compatibility site, meaning, that neither is likely to work at all.

Looks like you may be able to get HST working if you install enough MS Windows components, but YNAB is unlikely to work.

It always makes me cringe when I read about how another Linux fan has "convinced" folks to leave MS Windows behind ... and then comes running here wanting to know how to install MS Windows apps with Wine.

---

### Post by Cityscape on 2010-10-21
> **Mark Phelps said:**
> Wish you the best of luck ... BOTH of those apps are rated Garbage in the WineHQ app compatibility site, meaning, that neither is likely to work at all.

Looks like you may be able to get HST working if you install enough MS Windows components, but YNAB is unlikely to work.

It always makes me cringe when I read about how another Linux fan has "convinced" folks to leave MS Windows behind ... and then comes running here wanting to know how to install MS Windows apps with Wine.
Actually, I was the one who gave Homeschool Tracker Plus a garbage rating. But if MJClark505's method works (which it should) then I'll do another review.

My parent's no longer need YNAB.

My parents are now both using Ubuntu (my Dad has been for almost a year and used no Windows programs but my Mom only recently switched). They both seem to be happy with it. I use no Windows programs as well. But sometimes someone has only one or two Windows programs they need (like my Mom). That is where Wine is useful.

---

