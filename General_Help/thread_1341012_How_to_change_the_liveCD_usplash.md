---
title: "How to change the liveCD usplash"
date: 2009-11-29
forum: General Help
---

### Post by shababhsiddique on 2009-11-29
I have been trying for months but could not change the usplash of my installation. I downloaded
'debian.so' and used startupmanager to set it to usplash, but what it did was replace my default usplash loading screen with text based boot. I have no idea how to make those .so files for this purpose. I even tried 
[http://lunatic.no/usplash/](http://lunatic.no/usplash/)
to make one. It did produced a usplash.so but had the same result.

Many of the users suggested splashy- it worked at least , but the screen showed off occasionaly (less than 30% of the times i boot!!!). THe rest of the times I had to be satisfied with the text based boot.

Can anyone tell me whats wrong ??

---

### Post by shababhsiddique on 2010-03-06
> **shababhsiddique said:**
> I have been trying for months but could not change the usplash of my installation. I downloaded
'debian.so' and used startupmanager to set it to usplash, but what it did was replace my default usplash loading screen with text based boot. I have no idea how to make those .so files for this purpose. I even tried 
[http://lunatic.no/usplash/](http://lunatic.no/usplash/)
to make one. It did produced a usplash.so but had the same result.

Many of the users suggested splashy- it worked at least , but the screen showed off occasionaly (less than 30% of the times i boot!!!). THe rest of the times I had to be satisfied with the text based boot.

Can anyone tell me whats wrong ??

i think this will help out some out there..


This how-to is going to walk you through building your own custom usplash theme.  It does not use startup manager or any kind of 3rd party usplash manager crap.  I am going to assume you know what your doing at command line a little bit.
 [INDENT]$user = your login username
[/INDENT] First you need to make sure you get a few applications, libraries and a source.  Make sure you have GIMP.  It comes installed with Ubuntu Jaunty desktop edition so you should already have it. However if you dont:
 [INDENT]sudo apt-get install gimp
[/INDENT] Now lets apt to get some more tools we will be using:
 [INDENT]sudo apt-get install cdbs debhelper dpkg-dev fakeroot autotools-dev libusplash-dev
[/INDENT] Create a work directory:
 [INDENT]mkdir /home/$user/work
[/INDENT] change directories:
 [INDENT]cd /home/$user/work
[/INDENT] Download an example source.  We will be using the current incarnation of Ubuntu Jaunty’s usplash theme, just to work from at the moment.
 [INDENT]sudo apt-get source usplash-theme-ubuntu
[/INDENT] This will download the source of the newest ubuntu usplash theme and save it in your work directory as .tar.gz to decompress simply:
 [INDENT]tar xvzf usplash-theme-ubuntu_X.X.tar.gz
[/INDENT] Where X and X is the current version of the theme, I am using 0.23 during this writting.  This will create the folder usplash-theme-ubuntu-X.X.  Lets make sure we have editing priviledges so we can work with the files in this directory:
 [INDENT]sudo chmod -R 777 /home/$user/work/usplash-theme-ubuntu-X.X
[/INDENT] Open up GIMP and there should be 3 .png images located there (backgrounds), and some images labeled throbber (these are for your progress bar).  Open up the background .png images, located there, into GIMP.  Also open up the file usplash-theme-ubuntu.c into your favorite text editor.
 To work with the background images, goto Image->Mode-> and choose RGB, take note that the image mode is at default indexed, this is important for building your usplash theme.
 You should be able to work with the file now.  To make things simple I used simple colors, in a graphic made in photoshop.  I took the background images and wiped them to all black, getting rid of the ubuntu and dropping in my own graphic, roughly around the same area of the Ubuntu logo.
 When your finished editing the image flatten it by going to ->Image-Flatten Image, then change the mode back to indexed by going to ->Images->Indexed.  This is going to throw up a pop-up.  All I did was choose the generate optimum pallet with 256 colors, click Convert.
 Do this for each of the 3 background images found within the theme folder.
 Now open up throbber_front.png and throbber_back.png into GIMP.  These files are indexed as well, but don’t go changing anything just yet.  Goto ->Colors->Map->Rearrange Colormap and take a look at this.  You will see a bunch of colored sqaures.  This is the visual color index for the .png.  If you look at the usplash-theme-ubuntu.c file in your text editor scroll down until you see the first set of variables titled “Pallet Indexes” it should be commented out.  Each of these variables tells Usplash what colors to use for the progressbar, text and background.  Compare these values with those found in the numbered colored boxes in GIMP.  Do you see the connection?
 So what we have to do, is if we want to edit the progress bar, we need to come up with throbber images with a pallet of 256, to follow with the usplash-theme-ubuntu.c script.
 For this, I recolored my throbber images, back_throbber.png to a solid green, and fore_throbber to a gradient with greens.  I then chose a 256 colormap by going to ->Colors->Map->Set Colormap.  I chose the green.  Then went back to the  theme C script and changed the Palette values to those most representing of my progressbar and theme.  You MUST do this to each representation of the themes Palette indexes in the C file, there will be a few of them, for different resolutions throughout the file.  Save the images, indexed.
 Now its time for the fun part, we need to compile this theme into a .so file compatible for Usplash to work with. Open up terminal if its not open and issue the following commands:
 [INDENT]cd /home/$user/work/usplash-theme-ubuntu-X.X/ && dpkg-buildpackage -rfakeroot
 “wait for it to work…if successful it will create usplash-theme-ubuntu.so
 sudo cp /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-theme-ubuntu.so.old
 “backup old usplash theme”
 sudo cp usplash-theme-ubuntu.so /usr/lib/usplash/usplash-theme-ubuntu.so
 sudo update-initramfs -u
[/INDENT] If everything worked out correctly when you restart, you should see your new usplash boot screen.
 Now if your looking to get a bit more indepth into the customizations, the ubuntu source is a pretty good starting point, edit the make files and usplash-theme-ubuntu.c files accordingly, along with making sure your using the correct colors with your indexed .png files.






i put it on the live CD using reconstructor....

---

