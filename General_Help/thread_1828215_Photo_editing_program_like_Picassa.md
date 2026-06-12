---
title: "Photo editing program like Picassa?"
date: 2011-08-18
forum: General Help
---

### Post by insman1132 on 2011-08-18
This 75 year old works well with Picasa when working on windows XP.  Am looking for something similar that I can use with Utuntu?  I understand the Linux versions of Picasa when south!!  Never could get one downloaded anyway.

Photoshop-like programs are way too complicated for the simple photo editing functions that I want to do.  Can anyone recommend a photo editing program for Ubuntu that is less complicated than the Photoshop types available for Linux?

Thanks, guys.  This grandpa admires your near professionalism with your computers.

---

### Post by flipper T on 2011-08-18
picasa works ok with wine

---

### Post by angry_johnnie on 2011-08-18
there's picasa for linux

[http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30)

---

### Post by angry_johnnie on 2011-08-18
now that i think about it.  F-spot has many of the same features.  it comes, or came, included with ubuntu, depending on which version you're using.

if you happen to have the latest version, i think it comes with something other than f-spot, but it is, or should be, still available from ubuntu repositories.

while f-spot has many of the same features as picasa, it is important to keep it mind it is not picasa.  it looks different, and will probably take some getting used to.  but, then again, doesn't everything?

on the other hand, if you're used to picasa, you might as well use picasa.  it is, after all, available for linux in a nice and comfortable ubuntu package.

---

### Post by oldfred on 2011-08-18
I have the current windows Picassa 3.8 running in .wine without any real issues. Some of these instructions are for earlier versions but I am still installing the same way but downloading the windows 3.8 version.

                       [http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html](http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html)
    [http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019](http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019)
    [LEFT][http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html](http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html)[/LEFT]
    [LEFT]But I never installed Picasa 3.0[/LEFT]
    [LEFT][http://ubuntuforums.org/showthread.php?t=1385837](http://ubuntuforums.org/showthread.php?t=1385837)[/LEFT]
    
    [LEFT]  114  wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/LEFT]
    [LEFT]  115  sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/LEFT]
    [LEFT]  116  sudo chmod 777 winetricks[/LEFT]
    [LEFT]  117  sudo apt-get install cabextract wine wine-gecko[/LEFT]
    [LEFT]  118  winetricks allfonts fontsmooth-rgb gecko allfonts[/LEFT]
    [LEFT]Then download picasa for windows (change to 3.8 version:)
 ([http://dl.google.com/picasa/picasa36-setup.exe]("http://dl.google.com/picasa/picasa35-setup.exe"))
 run it, and the installer should start.[/LEFT]
    [LEFT]rename to picasa and move to wine programs[/LEFT]
        [LEFT]/home/fred/.wine/drive_c/Program Files/Google/Picasa3/runtime defaults.ini remove chg printer2 to printers[/LEFT]
    [LEFT]printerURL=https://client4.google.com/providers/printers.html[/LEFT]
        &#65279;sudo apt-get install wine cabextract
cd /usr/bin
wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 winetricks

---

### Post by flipper T on 2011-08-18
old fred

is there a way to increase the font size in latest picasa ? there used to be a config gui in older versions

also, how do i add gimp to the "open with" options


sorry for highjacking thread :)

---

### Post by oldfred on 2011-08-19
I have never changed fonts in Picasa. I do not see it in options in my version.

When in Nautilus file browser, right click on a file. The use open with, then other applications, and you can check always use this application.

Under open with is command line and I use that to create a gksudo gedit to let me edit as root without having to open a gksudo nautilus or command line when browsing and finally decide I want to edit a root owned file.

---

### Post by flipper T on 2011-08-19
sorry, i wasn't clear :

within picasa (run under wine) if you right click a picture, there is a "open with" option

i would like to add gimp to this. anyone know how ?

---

### Post by kaldor on 2011-08-19
> **insman1132 said:**
> This 75 year old works well with Picasa when working on windows XP.  Am looking for something similar that I can use with Utuntu?  I understand the Linux versions of Picasa when south!!  Never could get one downloaded anyway.

Photoshop-like programs are way too complicated for the simple photo editing functions that I want to do.  Can anyone recommend a photo editing program for Ubuntu that is less complicated than the Photoshop types available for Linux?

Thanks, guys.  This grandpa admires your near professionalism with your computers.


I am quite fond of using Shotwell for all my basic photo-editing needs. You can crop, enhance, and do very minor editing from within that program.

---

### Post by mrag on 2011-08-21
> **flipper T said:**
> sorry, i wasn't clear :

within picasa (run under wine) if you right click a picture, there is a "open with" option

i would like to add gimp to this. anyone know how ?

How would you do that? In fact how do you change the default program? Example, you have a jpg, you double click it, it opens with program X, how do you change that to open with program Y? Or you click on 'Print Screen' and you want Gimp to open instead of Shotwell (or Glenview or...).

I hope this is not too far off the original post. Which I believe was looking to an alternative to Picassa (for editing and not management purposes). Shotwell, Glenview, Shutter seem good. Gimp is probably overkill. Someone needs to get Irfanview working in Ubuntu ;-)

---

### Post by mike555 on 2011-08-21
....... Someone needs to get Irfanview working in Ubuntu ;-)[/QUOTE]

I second that, someone should contact him....... maybe in their forum;
[http://en.irfanview-forum.de/vb/forum.php](http://en.irfanview-forum.de/vb/forum.php)

---

