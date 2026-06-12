---
title: "Graphics driver SiS on notebook asus"
date: 2009-12-22
forum: General Help
---

### Post by uomomedio on 2009-12-22
[SIZE=3]Hello everybody. I've bought the notebook ASUS K50C and I installed ubuntu well except the graphics driver of the Graphic support SIS M672 . I'm trying in every way to find these drivers cause my resolution now is just 800x600.. i should have a resolution of 1366x768!
is there a way to find these drivers?? I'm really sorry for my bad english! and thank you for your help anyway!:)[/SIZE]

---

### Post by 3rdalbum on 2009-12-22
The SiS driver is built in. You may be able to add the desired resolution to /etc/X11/xorg.conf.

Or, if you can, take the notebook back and replace it with one that has ATI, Nvidia or Intel graphics. SiS is bad on Linux. (it's not even very good on Windows)

---

### Post by uomomedio on 2009-12-23
i tried to go on etc/X11/xorg.conf but i coudnt! it say  Command not found ! i can't change the notebook :(! that's terrible!

---

### Post by 57kev on 2009-12-23
Big thread on SiS graphics here:

[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)

Hope this helps.

---

### Post by audiomick on 2009-12-23
Hallo.
xorg.conf is not necessarily there on 9.10.
If you know what to put in it and create one, it will be used.

---

### Post by uomomedio on 2009-12-23
how I can create one?! i'm a newbie in ubuntu and all this morning i tried to find some good settings for xorg.conf..:( ! is there a simpler way to reach the resolution?!

---

### Post by 3rdalbum on 2009-12-23
> **uomomedio said:**
> how I can create one?! i'm a newbie in ubuntu and all this morning i tried to find some good settings for xorg.conf..:( ! is there a simpler way to reach the resolution?!

If you were using Nvidia or ATI graphics, then yes - the resolutions would be in System > Preferences > Display. With SiS, unfortunately the drivers are quite old-fashioned and you need to edit Xorg.conf.

If you type "/etc/X11/xorg.conf" into the terminal, you're telling the system that you want to run the file. Obviously that's not what you want to do, you want to open it and edit it. Install the "nautilus-gksu" package, log out and back in, and then locate the /etc/X11/xorg.conf file in your file browser and right-click it, and choose "Open as Administrator".

If you don't have an xorg.conf, you need to generate one. Unfortunately this involves briefly turning off your GUI. Log out. When you get to the login screen, press Control-Alt-F2.

Type:

```
sudo killall gdm
sudo Xorg -configure
```

This turns off X temporarily and runs the "configure" command. This puts a new xorg.conf into /root (or possibly into your home directory - I'm not quite sure).

You can move it to the desired location:

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

or, if in your home directory:

```
cp xorg.conf.new /etc/X11/xorg.conf
```

When done, you can restart the display server:

```
sudo gdm
```

---

### Post by uomomedio on 2009-12-23
i couldn't create  the file xorg.conf.. i installed the package Nautilus  but i wasn't able to put a new xorg.conf in my home directory.. it answer me something about an error in the cp using. And when i try to run "configure" it answer me
> marco@marco-laptop:~$ sudo Xorg -configure
[sudo] password for marco: 

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org]("http://wiki.x.org/")
 for help. 

 ddxSigGiveUp: Closing log




and i would like to show you The file Xorg.conf opened with nano 2.0.9

> Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "glx"
        Load  "dri2"
        Load  "dbe"
        Load  "dri"
        Load  "record"
        Load  "extmod"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
      ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "Rotate"                    # <str>
        #Option     "fbdev"                     # <str>
        #Option     "debug"                     # [<bool>]
        Identifier  "Card0"
        Driver      "fbdev"
        VendorName  "Silicon Integrated Systems [SiS]"
        BoardName   "771/671 PCIE VGA Display Adapter"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
               Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


I still say sorry about my unexperience and thank you !

---

### Post by aminmatrix on 2009-12-23
HERE THE SOLUTION
[http://nacho.larrateguy.com.ar/wp-content/uploads/2009/07/xorg-driver-sisimedia_0.9-1_i386.deb](http://nacho.larrateguy.com.ar/wp-content/uploads/2009/07/xorg-driver-sisimedia_0.9-1_i386.deb)

---

### Post by uomomedio on 2009-12-23
I tried to install the package you suggest me but it didn't work! after i istalled it and restarted the colours were like crazy and i couldn't see everything!!! i'm losing the hope to use ubuntu on my notebook!!:(
is it possible to set the xorg.conf file?! i tried to paste in some settings taken from other posts in the forum..but i'm not able to set the file well for my notebook!

---

### Post by Paper Tiger on 2010-03-13
I'm trying to follow these instructions but after I log out and press CTRL-ALT F2 and get a shell the commmand

sudo killall gdm

returns- gdm:no processes found

So, how can I shut down X or whatever is handling the windowing session in Karmic so that I can run Xorg -configure?

As you've probably guessed I'm trying to install SiS m671 drivers for an FS Esprimo 5535 laptop.  I had no trouble with my Tosh, but sadly that died and I got this FS piece of junk as a replacement. :(

---

### Post by elliotn on 2010-03-13
> **uomomedio said:**
> [SIZE=3]Hello everybody. I've bought the notebook ASUS K50C and I installed ubuntu well except the graphics driver of the Graphic support SIS M672 . I'm trying in every way to find these drivers cause my resolution now is just 800x600.. i should have a resolution of 1366x768!
is there a way to find these drivers?? I'm really sorry for my bad english! and thank you for your help anyway!:)[/SIZE]

SiS sux I had to buy a new gfx to get the effects

---

### Post by Paper Tiger on 2010-03-13
I've kept looking and still no joy:

sudo /etc/init.d/gdm stop just tells me not to invoke scripts through init.d and that I should use the service(8) utility.  However

[sudo] service gdm stop just tells me "stop: unknown instance"

sudo init 1 apparently should leave me at run level 1 single user and text input.  except it doesn't.

laptop is still stuck in an unusable 800x600 resolution :(

---

### Post by Paper Tiger on 2010-03-13
**Success!**

First of all I used this to make sure my driver was up to date

```

sudo apt-get install xorg-driver-sis671

```

Then pressed  Ctrl+Alt+F1, and entered my login before issuing the following commands:

```

sudo service gdm stop

sudo Xorg -configure

sudo cp /home/<username>/xorg.conf.new /etc/X11/xorg.conf

sudo nano /etc/X11/xorg.conf

```

Then I added in the following subsection in the "Screen" section

```

Section "Screen"
    SubSection "Display"
        Depth    24
        Modes    "1280x800"   "1280x768"    "1024x768"    "800x600"    "640x480"
    EndSubSection
    # Leave other settings intact
EndSection

```

then finally restart gdm with

```

sudo service gdm start

```

And Bingo - my laptop is now running in 1280x800

No idea why the service stop wouldn't work before but it did this time.
I hope this is of help to some people

---

### Post by buckyaustin on 2010-03-23
Hi this is the solution I stumbled upon when I had the same problem. Its from  [http://ubuntuforums.org/showthread.php?p=9014997#post9014997](http://ubuntuforums.org/showthread.php?p=9014997#post9014997).

In this thread there is a xorg.conf file which I just copied and pasted as I had tried in the past to rewrite the xorg.conf file which failed. This also switches you from SIS drivers to VESA drivers. Don't be naive the SIS drivers won't work. And as from my experience of using Ubuntu with SIS which is since Ubuntu hardy they do not work nor will ever work, use the more stable Vesa drivers.



Here Is The Solution:
Applications: top left corner 
Accessories
Terminal

Copy Code: sudo gedit /etc/X11/xorg.conf
type your password.

Then copy this into your xorg.conf
Section "Device"
        Identifier      "Configured Device"
        Driver  "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31-61  
        VertRefresh 50-75
        Modeline "1024x768" 25.20 640 688 784 800 350 410 412 449
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Device"
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

---

### Post by azedddine on 2010-03-23
> **buckyaustin said:**
> Hi this is the solution I stumbled upon when I had the same problem. Its from  [http://ubuntuforums.org/showthread.php?p=9014997#post9014997](http://ubuntuforums.org/showthread.php?p=9014997#post9014997).

In this thread there is a xorg.conf file which I just copied and pasted as I had tried in the past to rewrite the xorg.conf file which failed. This also switches you from SIS drivers to VESA drivers. Don't be naive the SIS drivers won't work. And as from my experience of using Ubuntu with SIS which is since Ubuntu hardy they do not work nor will ever work, use the more stable Vesa drivers.



Here Is The Solution:
Applications: top left corner 
Accessories
Terminal

Copy Code: sudo gedit /etc/X11/xorg.conf
type your password.

Then copy this into your xorg.conf
Section "Device"
        Identifier      "Configured Device"
        Driver  "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31-61  
        VertRefresh 50-75
        Modeline "1024x768" 25.20 640 688 784 800 350 410 412 449
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Device"
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection


hello, is this a solution for the sis 672 graphic? i mean, can i get the 3D effect?

---

### Post by 3rdalbum on 2010-03-23
> **Paper Tiger said:**
> **Success!**...

And Bingo - my laptop is now running in 1280x800

No idea why the service stop wouldn't work before but it did this time.
I hope this is of help to some people

Hmm, that's what I was trying to advise you to do... but looking back at what I'd written earlier, I realise I was giving some obsolete commands that don't work in 9.10.

---

### Post by purct on 2010-03-30
I had problems with configuring sis671 driver with my laptop ASUS X5DC.   I had to modify the src code to get it working.   check out my blog to get the binaries if you want to try the driver I modified.

[http://tpurch-blog.blogspot.com](http://tpurch-blog.blogspot.com)

---

### Post by jb_barroso on 2010-03-30
SiS M671/M672 driver for xorg xserver 7.5 on Debian / Sidux (Working on Ubuntu 10.04):

[http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/](http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/)

---

### Post by mhgsys on 2010-05-11
[http://go2.wordpress.com/?id=725X1342&site=ubuntuway.wordpress.com&url=http%3A%2F%2Fnacho.larrateguy.com.ar%2Fwp-content%2Fuploads%2F2009%2F07%2Fxorg-driver-sisimedia_0.9-1_i386.deb](http://go2.wordpress.com/?id=725X1342&site=ubuntuway.wordpress.com&url=http%3A%2F%2Fnacho.larrateguy.com.ar%2Fwp-content%2Fuploads%2F2009%2F07%2Fxorg-driver-sisimedia_0.9-1_i386.deb)
will work for most people on ubuntu   9.10
simply install the deb package and reboot.(for asus ask purct)

[http://ubuntuforums.org/showthread.php?t=958967&page=45](http://ubuntuforums.org/showthread.php?t=958967&page=45)
#post 445
Will work for most people on 10.04 (for asus follow next link)

[http://ubuntuforums.org/showthread.php?t=958967&page=44](http://ubuntuforums.org/showthread.php?t=958967&page=44)
#438 will work for most people on 10,04 using asus K50C/X5DC

Also; Last two links direct to the most active sis 771/671 thread since 2008 and contains lot's of contributing users.

Edit: No 3d... no compiz.. 2d drivers only.

---

### Post by Rackless on 2011-02-09
Driver SiS Mirage 3 M671 for Ubuntu 10.10

For you who get down because you can’t run 3D effect with compiz because of this SiS driver, well lucky for you. They already release the driver. for SiS Mirage 3 M671. This is how to install it.
First download the driver here. Extract the file and copy file “sisimedia_drv.so” to “/usr/lib/xorg/modules/drivers/”. Then also copy file “xorg.conf” to “/etc/X11/”.

Reboot the computer and see what happen :D

---

### Post by kommissario on 2011-03-06
> **Rackless said:**
> Driver SiS Mirage 3 M671 for Ubuntu 10.10

For you who get down because you can’t run 3D effect with compiz because of this SiS driver, well lucky for you. They already release the driver. for SiS Mirage 3 M671. This is how to install it.
First download the driver here. Extract the file and copy file “sisimedia_drv.so” to “/usr/lib/xorg/modules/drivers/”. Then also copy file “xorg.conf” to “/etc/X11/”.

Reboot the computer and see what happen :D

I do not see any driver to download ... Is there any solution for Compiz with Asus K50C?

---

### Post by danelwillis on 2012-10-14
SIS graphics do not really work on Linux. I have struggled in the past with them. But there is a way around it, though you will not be able to use graphics accelerated scripts etc. Change to ur desired resolution, hope all works out for you.

this is the solution I stumbled upon when I had the same problem. Its from  [http://ubuntuforums.org/showthread.p...97#post9014997]("http://ubuntuforums.org/showthread.php?p=9014997#post9014997").

In this thread there is a xorg.conf file which I just copied and pasted  as I had tried in the past to rewrite the xorg.conf file which failed.  This also switches you from SIS drivers to VESA drivers. Don't be naive  the SIS drivers won't work. And as from my experience of using Ubuntu  with SIS which is since Ubuntu hardy they do not work nor will ever  work, use the more stable Vesa drivers.



Here Is The Solution:
Applications: top left corner 
Accessories
Terminal

Copy Code: sudo gedit /etc/X11/xorg.conf
type your password.

Then copy this into your xorg.conf
Section "Device"
        Identifier      "Configured Device"
        Driver  "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31-61  
        VertRefresh 50-75
        Modeline "1024x768" 25.20 640 688 784 800 350 410 412 449
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Device"
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

---

### Post by wildmanne39 on 2012-10-14
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

