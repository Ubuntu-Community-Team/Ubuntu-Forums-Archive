---
title: "Windows to Linux"
date: 2009-08-03
forum: General Help
---

### Post by gavinjb on 2009-08-03
Hi,

I am trying to make a complete move to Linux from Windows Vista and have been doing an audit of the software that I use under Windows and where I know the alternative what it is, not sure if anyone can help with identifying alternatives for the items I have been unable to find alternatives for (preferably Gnome)

Apps I have found Linux versions of
```

7Zip &#8594; 7 Zip
VLC &#8594; VLC
TrueCrypt &#8594; TrueCrypt
GoogleEarth &#8594; GoogleEarth
Picasa &#8594; Picasa
Bibble &#8594; Bibble
MoneyDance &#8594; MoneyDance
Alistair (Topfield File Transfer) &#8594; Puppy/Guppy
MyDropbox &#8594; Linux client of MyDropBox
OpenOffice &#8594; OpenOffice / Gnome Office
KeePass &#8594; KeePassX

```

Apps I have questions about or have found no alternatives
```

**UAE** &#8594; I know there is an UAE for Linux, not sure how good it is?
**Speculator** (Spectrum Emulator) &#8594; Any suggestions
**Lightscribe** &#8594; Haven't found anything for this yet
**Fastcheck** (or multi folder IMAP checker)
**Topfield to MP4 Converter** &#8594; at a push I could run VideoReDo with Wine
Video Editor &#8594; Looking for reconmendations for Good Linux Video Editors
**SlickRun** &#8594; Windows Freeware tool to speedup launching of apps (e.g. press Special + Q type Firefox and press enter to run Firefox)
**CintraNotes** &#8594; Similar to Basket Notepads but would ideally like a Gnome app (Tomboy doesn't give me the functionality)
**Video Editing** &#8594; Looking for a good Photo Editing software, needs to be able to edit MPG files
**Photoshop CS3** &#8594; Have tried Gimp/CinePaint but can't get on with them as I much prefer the MDI interface design of Deluxe Paint clones, so currently looking at using VirtualBox to run CS3 unless anyone else has any suggestions
**Samsung S5230 (Tocco Lite) Sync** &#8594; Use Mobile Master on Windows but need to have a way to Sync Thunderbird Contacts & Calendar and Transfer files easily between PC and device in Linux 

```

I know I have loads of questions here but any help would be appreciated.

Thanks,



Gavin,

---

### Post by TeoBigusGeekus on 2009-08-03
Perhaps some of your windows apps might be able to run in Ubuntu with wine.
Check out this page
[http://appdb.winehq.org/index.php]("http://appdb.winehq.org/index.php")

---

### Post by asmoore82 on 2009-08-03
FYI, from the 7-zip manual:
> DO NOT USE the 7-zip format for backup purpose on Linux/Unix because - 7-zip does not store the owner/group of the file.
On Linux/Unix, in order to backup directories you must use tar

The built-in archive manager in GNOME is dandy.

---

### Post by ppirilla on 2009-08-03
While image and video editing software exists for Linux, nearly anyone who does serious work with this type of software has trouble migrating over.

Wine might work for some of it, but I wouldn't count on that.

I really hate to say it, but if moving from Photoshop to TheGIMP is not acceptable, then Linux probably isn't for you right now.

---

### Post by chriswyatt on 2009-08-03
For ZX Spectrum emulation try FUSE.

There are DEBs here:

[http://people.igalia.com/berto/](http://people.igalia.com/berto/)

---

### Post by bruce2000 on 2009-08-03
Apps I have questions about or have found no alternatives
```

**UAE** &#8594; I know there is an UAE for Linux, not sure how good it is?
**Speculator** (Spectrum Emulator) &#8594; Any suggestions

```

There are linux versions of uae and a spectrum emulator called xspect in the ubuntu repositories. I've not tried uae but the speccy emulator is pretty good once you've learned its commands.

To install open a terminal and type:

```

sudo apt-get install spectemu-x11
sudo apt-get install uae

```

If youre interested there are more emulators for linux on this page:

[http://www.worldofspectrum.org/emulators.html#unix]("http://www.worldofspectrum.org/emulators.html#unix")

---

### Post by gavinjb on 2009-08-04
Hi,

Thanks for the input.

I have been looking at GimpShop which from the screenshots seems to have all the application windows in a MDI like window, does anyone use this and how well is it maintained?

For my SlickRun replacement I found info on an app called GnomeDo, does anyone use this as it sounds like it might possibly do what I want?

Also anyone with any ideas on Syncing my Samsung Phone.


Thanks,


Gavin,

---

### Post by gradinaruvasile on 2009-08-04
Lightscribe -

[http://ubuntuforums.org/showthread.php?t=106197&page=18]("http://ubuntuforums.org/showthread.php?t=106197&page=18")

---

### Post by credobyte on 2009-08-04
> **Video Editing &#8594;** Looking for a good Photo Editing software, needs to be able to edit MPG files[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/) ( available from repos )

> **Photoshop CS3 &#8594;** Have tried Gimp/CinePaint but can't get on with them as I much prefer the MDI interface design of Deluxe Paint clones, so currently looking at using VirtualBox to run CS3 unless anyone else has any suggestions[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

---

### Post by MaxIBoy on 2009-08-04
For your "slickrun," an alternative is built-in. In GNOME (Ubuntu's default desktop environment) hit alt-F2 and type the name of the program. I'm pretty sure this works in KDE and XFCE (as in Kubuntu and Xubuntu) as well, but it's been a while since I experimented with either of those, my memory might not be so good.


As far as I know, GIMPshop only works with Gimp 2.2, whereas the most recent version is 2.6. 

For image editing, I agree that the UI of the GIMP takes getting used to. It's fairly easy to customize though. On my laptop I like to put all the controls in one window and tile it side-by-side with the image. On my desktop, I have two monitors, and I can add a lot of extra controls and put them all on the second monitor. Anyway, it takes a few days, at most a week, to get comfortable with the GIMP, and after that it will come almost as naturally as breathing.

This will be a recurring theme for you. It's a new OS, largely new software, and much of what you know about the "old way" will simply be wrong. You might as well resign yourself to that. View it as a fun challenge to explore the new system. Don't try to bludgeon it into similarity with the old one, because it's not really possible. 


These pages will probably help you find what you need:
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linuxlinks.com/article/20070701111340544/Equivalents.html](http://www.linuxlinks.com/article/20070701111340544/Equivalents.html)
[http://www.linuxscrew.com/2007/11/22/windows-software-linux-software/](http://www.linuxscrew.com/2007/11/22/windows-software-linux-software/)
[http://www.google.com](http://www.google.com)

---

### Post by ad_267 on 2009-08-04
> This will be a recurring theme for you. It's a new OS, largely new software, and much of what you know about the "old way" will simply be wrong. You might as well resign yourself to that. View it as a fun challenge to explore the new system. Don't try to bludgeon it into similarity with the old one, because it's not really possible.

+1 to that, Linux is quite a different beast to Windows. It isn't too hard to get used to though if you can accept that things are going to be different.

Video editor: Kdenlive is pretty good although still has some stability problems.

For Photoshop, another alternative is Krita. For vector image editing, use Inkscape. There's also Paint-Mono, a port of Paint.Net to Mono, although I haven't tried it myself and I'm not sure how far along the project is.

SlickRun looks very similar to Gnome-Do. Also check out the Docky interface for it if you like OS X's dock.

---

### Post by gavinjb on 2009-08-04
Hi,

I have just found a couple of interesting looking Linux Photo Editors, what I am looking at doing now is running CS3 in VirtualBox for when the Linux tools can't do what I need but the rest of the time I will use the Linux Tools (I need a Windows Session anyway to be able to connect to work as the software they use only supports Windows!)

The Photo Editors are:

1. Fotoxx - [http://kornelix.squarespace.com/fotoxx/](http://kornelix.squarespace.com/fotoxx/) (includes some nice features including HDR and Panoramic merges)

2. Photo-Mono - [http://code.google.com/p/paint-mono/](http://code.google.com/p/paint-mono/) (clone of Photo.net using Mono)

Gavin,

---

### Post by koushik.ms on 2010-06-17
One thing which slickrun does very well that I haven't been able to figure out how to do in gnome-do is expanding URLs with arbitrary text replacement. 

For example, I can view popular bookmarks tagged with tag in delicious with a slickrun command like "deltag tag" mapped to "http://delicious.com/popular/$W$" and slickrun will replace $W$ with tag. I can do the same thing for viewing a bug in launchpad or search a query in google by replacing special token like $W$ with user input.

I know there are separate gnome-do plugins for launchpad and google search, but what I want is a generic url expansion with parameters that user can supply at the time of invoking that shortcut. If I have that capability I can drive my browser directly into the depths of any REST-ful webapp - even e.g., a properietary company intranet.

---

### Post by ad_267 on 2010-06-18
You can ask a question or file a feature request at [https://bugs.launchpad.net/do](https://bugs.launchpad.net/do)

---

