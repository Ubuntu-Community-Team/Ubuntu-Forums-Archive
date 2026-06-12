---
title: "How to get crebs working in 11.10?"
date: 2011-10-14
forum: General Help
---

### Post by kc1di on 2011-10-14
I've done a new install of 11.10 and like it very much so far.
one thing I have not been able to do is install crebs wallpaper slide show.  Get a 404 not found from their ppa.  Anyone got this working yet?

Thanks,
Dave

---

### Post by skag on 2011-10-15
I have the same problem too... I also cant install it with the source(tar). It says its installed in the /usr/local folder (actually it is in the /usr/local/share/applications folder) but when i run it nothing happens....

---

### Post by Pete Pupalaikis on 2011-10-15
I also recently updated to 11.10 and like most things better and am having the same problem.  I was not able to connect to a crebs repository for oneiric.  I did visit the crebs homepage at:  [http://www.obfuscatepenguin.net/crebs/](http://www.obfuscatepenguin.net/crebs/).

Here I downloaded the crebs source, extracted and ran the install.  It is installed and I'm able to create .xml files of my crebs slideshows.

The problem appears to be with the setting of the background wallpaper from within oneiric.  In natty, I would see my crebs .xml files along with other pictures and wallpapers shown as a stack of pictures, instead of a single picture.  I've tried navigating to my ~/.crebs folder where the slideshows are located, but I am not allowed to select these files as a background like before.

I hope this gets resolved because I really loved this program and feature.

---

### Post by nasrat on 2011-10-15
I create my own xml files, and as stated I can't get it working either. Manually setting the background xml using gconf2 doesn't work!

Anyone know if there is a bug report out there about this?

EDIT: I found this [http://askubuntu.com/questions/67218/how-do-i-create-a-desktop-wallpaper-slideshow-in-oneiric](http://askubuntu.com/questions/67218/how-do-i-create-a-desktop-wallpaper-slideshow-in-oneiric)

EDIT 2: there is a bug [https://bugs.launchpad.net/gnome-control-center/+bug/868850](https://bugs.launchpad.net/gnome-control-center/+bug/868850) and the developer marked it as invalid stating they are not going to let users use this feature, please subscribe and be loud about this

---

### Post by kc1di on 2011-10-17
after installing crebs manually and trying to run it in a terminal get the following error messages. anyone have any idea what might be missing?

(crebs:13989): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(crebs:13989): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(crebs:13989): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(crebs:13989): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/local/bin/crebs", line 38, in <module>
    from crebs.main import main
  File "/usr/local/bin/../share/crebs/lib/crebs/__init__.py", line 6, in <module>
    from gtk                import glade
ImportError: cannot import name glade


thanks,
Dave

---

### Post by Pete Pupalaikis on 2011-10-17
I was very disappointed to find out that crebs does not work when upgrading to oneiric.

I'm disappointed that they marked the bug as invalid, since it is really a simple problem - just allow users to select .xml files as wallpaper in the Change Desktop Background menu.  If you look at the selections provided, you find one wallpaper with a clock on it which is in fact exactly a file like crebs would produce!  Only you can't select one that's not already in the list only one that is provided.

A workaround I've figured out, with help from Pyklar (see [https://bugs.launchpad.net/gnome-control-center/+bug/868850](https://bugs.launchpad.net/gnome-control-center/+bug/868850)) on another forum is as follows:

1) As of today, the crebs repository is not found for oneiric.  install crebs manually by downloading from [http://www.obfuscatepenguin.net/crebs/](http://www.obfuscatepenguin.net/crebs/).

2) use crebs to produce your .xml wallpaper shows.  They are stored by crebs in ~/.crebs which is a hidden directory.

after all, crebs just creates the .xml files - it also sets the current wallpaper when done.  it is the setting of the wallpaper file that is really broken.

if you already have some .xml wallpaper files, you can skip to this step.

3) look in the directory /usr/share/gnome-background-properties.  You will see a few .xml files which contain the selections allowed when you try to set the background wallpaper from the Change Desktop Background menu.

Create an .xml file which references your .xml wallpapers.  You can name it custom-wallpapers.xml.  Mine looks like this:

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
  <wallpaper deleted="false">
    <name>Airshow Pax</name>
    <filename>/home/peterp/.crebs/Airshow_-_Pax.xml</filename>
    <options>zoom</options>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Airshow Dover</name>
    <filename>/home/peterp/.crebs/Airshow_Dover.xml</filename>
    <options>zoom</options>
  </wallpaper>
  <wallpaper deleted="false">
    <name>England London</name>
    <filename>/home/peterp/.crebs/England_-_London.xml</filename>
    <options>zoom</options>
  </wallpaper>
 </wallpapers>

Basically, you need to set the name to what you want displayed and set the filename to access your crebs created .xml files in your crebs directory.

One thing to remember, when you edit your custom wallpaper file, make sure any backups are deleted - ubuntu will concatenate the contents of any file found in this directory so not deleting the backup will create multiple selections of the same thing.  It took me awhile to figure out what was going on.

Anyway, after doing this, you will find that your .xml file background slideshows are immediately accessible when you try to change the background.

It's really a shame that this doesn't work easier, but for me, I just spent a little time making all of my screenshows, manually editing the file, and I'm back in business.  Not too painful because I don't often create these, but I have a wide variety to choose from as the mood fits.

The developers really ought to fix this.

Pete

---

### Post by kc1di on 2011-10-18
> **Pete Pupalaikis said:**
> I was very disappointed to find out that crebs does not work when upgrading to oneiric.

Pete
Thank you Pete for this info it helps.
my problem is I can't get crebs to even run on new install. Reference the error code I posted earlier
may be will re submit a new bug report see if it gets handled differently.

Dave

---

### Post by kc1di on 2011-10-18
Reported to lauchpad bug #

Bug #877401

hope it helps

---

### Post by kc1di on 2011-10-24
Received the  following temporary fix from luachpad bug reporting
Haven't had a opportunity to try it yet though. 
Will when things slow down a bit here. 

> RepoOne quick fix is: sudo apt-get install gtk2-engines-pixbufrt from lauchpad bug report say to install 

the bug link on lauchpad can be found here.

[https://bugs.launchpad.net/bugs/877401]("https://bugs.launchpad.net/bugs/877401")

---

### Post by kc1di on 2011-10-24
> **kc1di said:**
> Received the  following temporary fix from luachpad bug reporting
Haven't had a opportunity to try it yet though. 
Will when things slow down a bit here. 



the bug link on lauchpad can be found here.

[https://bugs.launchpad.net/bugs/877401]("https://bugs.launchpad.net/bugs/877401")

This work around did not work.  :(

---

### Post by BillyBoa on 2011-11-07
Another work around is to run this app:
[http://gnome-look.org/content/show.php/Wallpaper+Slideshow?content=125178](http://gnome-look.org/content/show.php/Wallpaper+Slideshow?content=125178)

---

### Post by RafiB on 2011-11-12
Yep, got it. *rubs eyes*
You've got to download the source from the Internet and install. And then. It's ugly, but basically, you don't have the right dependencies installed for pygtk, which is what crebs uses.
Fix that with

```
$ sudo apt-get install python-glade2 python-gtk2 python-gtk2-dbg python-gtk2-dev python-gtk2-doc
```

And if that doesn't work, do this as well:

```
$ sudo apt-get install debhelper python-support gnome-pkg-tools cdbs autotools-dev quilt xvfb xauth xfonts-base python-all-dev python-all-dbg libgtk2.0-dev libglib2.0-dev libpango1.0-dev libatk1.0-dev libglade2-dev python-numpy-dbg python-cairo-dev python-cairo-dbg python-gobject-dev python-gobject-dbg xsltproc docbook-xsl gnome-icon-theme
```

Should work fine now - at least, it worked for me.

---

### Post by em3raldxiii on 2011-12-30
Just an addendum to this thread is a related thread:
 
[http://ubuntuforums.org/showthread.php?t=1881394](http://ubuntuforums.org/showthread.php?t=1881394)
 
The only differences are: 1. Using alternative methods (rather than CReBS) to generate the slideshow XML file, and 2. I've been working on a script to automatically add the XML pointer info to the gnome-background-properties directory. As of the writing of this post, it simply adds the information using SED to the existing ubuntu-wallpapers.xml file, but after reading this thread I think I am going to have it generate (or append to) a custom-wallpapers.xml file.  The script is attached to the above linked thread.

---

### Post by kc1di on 2012-01-22
Downloaded and installed Wallch and it's working fine.
:)

---

### Post by Razer1103 on 2012-10-24
[SIZE="4"]**Here's the solution I've found...**[/SIZE]

I've tried Wallch. It's nice, but quickly get's annoying due to the fact there is no way to make it start on boot, and from what I've found, it must either stay open on the launcher or on the menu bar. (The icon on the menu bar looks horrible.)

It took me a while, but I finally figured out the only way to activate CreBS is to browse to an image file, (in Nautilus,) right-click, and choose Open With... -> Create Background Slideshow. CreBS opens, and from there you can add more images. Alternatively, (what I did,) you can select multiple images at a time and choose Open With... -> Create Background Slideshow.

Once you tinker with CreBS getting the timing setting how you like it, click the Tick to save the XML file. At that point, nothing else seems to happen. It says in the corner that the wallpaper is changed, but it's not. From there, what you have to do is open up a terminal and type, ```
gsettings set org.gnome.desktop.background picture-uri file:///home/<username>/.crebs/<slideshowname>.xml
``` That will change the background to the slideshow you just created, and you should be good to go. The "file:///" is necessary. Make sure you replace <username> with your username and <slideshowname> with the name you gave to your slideshow.

---

