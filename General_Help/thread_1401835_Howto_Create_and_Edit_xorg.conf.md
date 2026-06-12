---
title: "Howto Create and Edit xorg.conf"
date: 2010-02-08
forum: General Help
---

### Post by pi/roman on 2010-02-08
This is a basic guide to create an xorg.conf file and edit it to fix display problems. In order to get the most out of your display adapter you should follow a guide for your particular model which may be found here:
[[COLOR=Blue]BinaryDriverHowto[/COLOR]]("https://help.ubuntu.com/community/BinaryDriverHowto")
or search for it on the forums.

Here is a command to type in a terminal which will create xorg.conf.new in your /home/username/ folder:
```
sudo X :2 -configure
```Open this file up in your favorite editor, for example press Alt/F2 and run:
```
gksudo gedit xorg.conf.new
```Now open up your current xorg.conf, for example Alt/F2:
```
gksudo gedit /etc/X11/xorg.conf
```If xorg.conf is empty, then you can copy everything from xorg.conf.new into it.

If it is not empty, then you will need to study it and decide what to include in it.  It is very important to recognize the "Identifier" in each section because that same identifier will be referenced in other sections and they must match up.  It is also important to recognize which Driver is being used in the "Device" section because different drivers will obviously produce different results.
So before you do go about making major changes to an already existing xorg.conf I would recommend researching the documentation on the subject.
Here are some manuals you can find through a terminal window that may be of use:
```
man xorg.conf
``` -covers mostly everything
```
man gtf
``` -gtf creates modelines to insert into xorg.conf
```
man cvt
``` -cvt also creates modelines
Use the following to find manuals on specific drivers by typing man followed by 1 of these:
> ati  chips cirrus cyrix fbdev i128 i740 intel mga neomagic nv openchrome  r128  rendition  s3virge  siliconmotion  sis tdfx tga trident tseng v4l vesaI also recommend researching the options in your "Device" section, which are different for each graphics adapter, by searching for them online.  They are commented out with "#" by default.  If you find an option that looks like it will fix a problem then uncomment it and supply a value to it.

Optional quick fix when you are getting the wrong resolution:
Look in your "Screen" section and go to Subsection "Display" and place within this subsection the following line, substituting xres yres for your desired resolution:
virtual xres yres
For example using the virtual option, your "display subsection may look something like this:
> SubSection "Display"
    virtual 1280 768
Viewport   0 0
    Depth     24
EndSubSectionOptional - Make modelines to place inside your "Monitor" section by using one of the following commands substituting xres yres for your desired resolution and rate for your desired refresh rate:
gtf xres yres rate
cvt xres yres
Then copy the 2nd line of output to the last number, and paste it into your "Monitor" section so the result would look something like this:
> Modeline "1280x768"  80.14  1280 1344 1480 1680  768 769 772 795Now copy the identifier from the modeline which in this example is "1280x768" and go to your "Screen" section and in your "Display" subsection add it to your list of modes.  If you don't have a list of modes in your Display subsection then you can create one like this for example:
> SubSection "Display"
    Modes "1280x768"
    Viewport   0 0
    Depth     24
EndSubSectionand you should add the same Modes to each "Display" subsection.

---

### Post by ottosykora on 2010-12-31
is there a way to find out the current settings to the lines concerning monitor? In the xorg.conf, there seems to be all set somehow to default or auto at the moment.

---

### Post by pi/roman on 2011-01-02
Modeline data can usually be found in Xorg.0.log. Your computer may sometimes display important information here that it just wasn't able to figure out how to use properly itself.

```
cat /var/log/Xorg.0.log | grep -i modeline
```should show the current modeline in use and may display other relevant video data or look in the output of that for something else to grep for like part of the name of your driver or adapter and use the "-i" so it is not case sensitive. If you find a modeline for the proper resolution in your log then it may be better than a modeline you can create otherwise.

---

