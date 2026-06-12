---
title: "installing office 2007 with wine in Ubuntu 9.10"
date: 2010-03-15
forum: General Help
---

### Post by cbecker78 on 2010-03-15
Hi all.  forgive me if this is not the right forum, but I think this is right.

My issue is that after installing wine and office 2007 following [these instructions]("http://helpforlinux.blogspot.com/2008/12/install-microsoft-office-2007-in-ubuntu.html"), whenever I launch any of the office applications, I get the error message "Microsoft office has not been installed for current user. Please run setup to install the application."  Searching I was able to find some similar information on much older versions of wine and office 2003, but nothing that made any sense to me...

Does anyone have any idea how I might resolve this issue, or a link to better "from scratch" instructions that will make it work?  I've seen some stuff talking about wine tricks, and different things, but I just don't know what is right for the current version of ubuntu and wine...

Thanks so much for any help!

(ps, i downloaded wine with following[ this]("http://www.winehq.org/download/deb") link... using the wine from the repository did not allow me to run the setup.exe...)

---

### Post by brian mcgee on 2010-03-15
Just did this yesterday actually.  I renamed ~/.wine to ~/.wine.orig -- then removed the older version of wine (sudo apt-get remove wine). Then I ran the following:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

Then installed the latest wine with:

```
sudo apt-get install wine
```

And reinstalled Office 2007. No problems. HTH

---

### Post by cbecker78 on 2010-03-16
Hi.  Much thanks for the input.  I did as you suggested, but am still not having any luck.  Office will install sucessfully, but on first launch of any office program, I still get the error message "Microsoft Office Word/Excell/etc. has not been installed for the current user.  Please run setup to install the application.")

then the software automatically closes.  On second attempt to open (and subsequent attempts) I get the additional error message first " Word cannot open this document template. (C:\users\cbec\...~$liding Blocks.dotx)

If I try to uninstal office from wine, i get "unable to execute the unistaller C:\program files\common files\microsoft share\office 12\setup controller\setup.exe""/unistall Enterpriser/dll OSETUP.DLL"

Any other ideas on what I might be doing wrong?

---

### Post by cbecker78 on 2010-03-16
Ok, found a link to [this]("http://www.mikesouthby.co.uk/2009/11/ubuntu-9-10-installing-microsoft-office-2007/") page through another post on this forum.  unistalling wine, purging it, and using the version of wine indicated on the linked page (along with following the rest of the instruction on that page), got office 2007 up and running for word, excell, and powerpoint.

Thanks!

---

### Post by qwerty57 on 2010-05-06
I've got a bit of a problem with MSoffice 2007 & Wine.  I installed them both on my desktop and they work perfectly.  I also installed wine version 1.1.38 on my laptop.  Now my laptop is one of those tiny Acer Aspires that doesn't have a DVD player.  So, instead of installing MSoffice from a CD I had to download it from a torrent site.  The download and installation seemed to go OK, but when the window asking for my Registration Key popped up, I couldn't type anything into it!  Also, at least one of the Office functions seems to be less than 100% functional (some ppts will load and others won't).  

Can I just copy my MSoffice CD onto a thumbdrive & install my good version of office from there?  I seem to recall that there is some way to make a thumbdrive read like a CD.

---

### Post by cbecker78 on 2010-05-06
> **qwerty57 said:**
> I've got a bit of a problem with MSoffice 2007 & Wine.  I installed them both on my desktop and they work perfectly.  I also installed wine version 1.1.38 on my laptop.  Now my laptop is one of those tiny Acer Aspires that doesn't have a DVD player.  So, instead of installing MSoffice from a CD I had to download it from a torrent site.  The download and installation seemed to go OK, but when the window asking for my Registration Key popped up, I couldn't type anything into it!  Also, at least one of the Office functions seems to be less than 100% functional (some ppts will load and others won't).  

Can I just copy my MSoffice CD onto a thumbdrive & install my good version of office from there?  I seem to recall that there is some way to make a thumbdrive read like a CD.

Yah, there is a way to set it as a CD, but I don't remember how.  I just always copy the contents of CD onto the flashdrive, the hunt for and run the install/setup executable.  I have only done this for my wife on winXP with her netbook, but should work the same with wine, I would think.\

EDIT:  - I just remembered I had the same issue with not being able to enter anything into the box- It turned out I just had to wait about 5 minutes -so might be wort trying to wait if you haven't already

---

