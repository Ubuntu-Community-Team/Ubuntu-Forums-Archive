---
title: "Apps for printing photos"
date: 2012-09-02
forum: General Help
---

### Post by notoriousdbp on 2012-09-02
Hi everyone,
I used to use Picasa for printing out photos to put in our albums but alas Picasa for Linux is nor more.  I've looked into Shotwell and the best it can do is print one photo per page when I usually print 4 on a sheet of A4.  I've also tried F-Spot but it crashes every time I go to print preview or print.

So basically I'm asking what apps do people use to print their photos out, how easy are they to use and how good are the results?

---

### Post by Frogs Hair on 2012-09-02
Gimp from the software center would be one solution. You can place a number of photos on a background by using open as layers and move them where you want and add text. Coloring the background and changing size is no problem either.

---

### Post by timcredible on 2012-09-02
i print a lot of photos, i use snapfish, mpix, costco, and winkflash, depending on what kind of print and timeframe i need photos.  ink is too expensive to print much at home.  plus there's so many cool items that they offer.  i use digikam for editing.  if i need photos instantly, i put edited photo on sd card and plug that card into my hp printer and let the printer print on borderless photo paper, that works much better and cheaper than trying to print photo quality prints on 8x11 paper and cutting, which i've never had much luck with on linux or windows.  a printer like that only runs about $80 and can't tell it from storemade print

---

### Post by jmate24 on 2012-09-03
gnome photo printer is also good.

best of luck...

jmate24

---

### Post by SeijiSensei on 2012-09-03
[Gwenview]("http://gwenview.sourceforge.net/") with the "[kipi-plugins]("http://packages.ubuntu.com/precise/kipi-plugins")" package added makes for an excellent photo printing application.  It can also do simple edits like cropping and resizing without having to resort to a more full-featured editor like GIMP.

It can also "print" to a PDF file if you want to preserve the photos and layout for future copies.

---

### Post by oldfred on 2012-09-03
My wife just uploaded a bunch of photos from Picasa to Snapfish. 

We have the current Windows version of Picasa 3.9 running in .wine without any major issues.

[http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html](http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html)
[http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019](http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019)
[http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html](http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html)
But I never installed Picasa 3.0
[http://ubuntuforums.org/showthread.php?t=1385837](http://ubuntuforums.org/showthread.php?t=1385837)

&#65279;sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine winetricks

Configure Wine to set up directory,  Applications, Wine, Configure

Then download picasa for windows
 ([http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe))
cd && wget [http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe)
Move it into .wine/drive_c/Program Files
wine picasa39-setup.exe

---

### Post by temetvince on 2012-09-03
What? They got rid of picasa? I make the jump to mac for a year and look what happens! :(

Anyway, as oldfred mentioned, you could always run picasa in wine, as it seems to run fairly well.

---

### Post by notoriousdbp on 2012-09-05
Hi, thanks for your help on this one everybody. Gwenview + kipi-plugins seems to do the job just nicely, exactly what I was looking for.  Very much appreciated.

---

