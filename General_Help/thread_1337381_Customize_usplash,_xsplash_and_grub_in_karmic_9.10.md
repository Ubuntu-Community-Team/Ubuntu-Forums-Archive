---
title: "Customize usplash, xsplash and grub in karmic 9.10"
date: 2009-11-25
forum: General Help
---

### Post by bargie on 2009-11-25
Okay, my first post so I thought I'd make it worthwhile. Incase you're wondering how to customize the grub boot menu, the usplash boot screen and then the xsplash GDM login screen in karmic koala (9.10), this should help you out considerably. 

[B]1- Change the GDM theme and background (xsplash)
[/B]
Okay..here goes.
> 
# gksudo gdm -u dbus-launch gnome-appearance-properties
This pops up the GNOME Appearance settings window, just install your theme by clicking on "Install" Under the "Themes" tab, similarly click on "Background" and then on "Add" and select whatever background you would like when the login input screen comes up.

(Note: If for some reason your theme still doesn't show up under the Theme tab, select a theme and click on "Customize", then select your theme under the "Controls" tab and similarly under the "Windows borders" tab.)

To get rid of the irritating dark brown background with the white ubuntu logo and progress bar, do this:

Move the background image file or whatever image file you would like to /usr/share/images/xsplash/ and rename it as bg_screenresolution.jpg, so mine is bg_2560x1600.jpg

If you open up the /usr/share/images/xsplash/ folder you'll also see some files starting with logo_, you can let them remain as is they are if you like to see the ubuntu logo, i changed mine to look like a mac logo. Incase you want to change them just replace them with  your own logos and size the dimensions to match, so logo_large.png is 302 x 110, just make sure your image file has the same dimensions. (Backup the existing logo_ files too btw)

Now moving onto the the usplash screen with the black background and white ubuntu logo on it, this comes up after the grub boot selection menu.
[B]
2- Change the usplash boot screen:
[/B]
First off you need to download a few things to get started.

> 
james@james-desktop:~$ sudo apt-get install cdbs debhelper dpkg-dev fakeroot autotools-dev libusplash-dev
Now you need to download the source of usplash-theme-ubuntu package.
You'll need to goto [https://launchpad.net/ubuntu/+source/usplash-theme-ubuntu/0.27 ]("https://launchpad.net/ubuntu/+source/usplash-theme-ubuntu/0.27")and download the usplash-theme-ubuntu_releaseNumber.tar.gz  (I downloaded 0.27). apt-get did not seem to work for some reason. Anyway, untar the package by:

> 
james@james-desktop:~$ tar xvzf usplash-theme-ubuntu_releaseNumber.tar.gz
If you look in the usplash-theme-ubuntu folder, you'll see there are 4 files starting with the logo_ prefix and .png extension, you need to either edit these files or make your own image files making sure that the color mode is Indexed and not RGB or Grayscale or anything else (see how in the paragraph below, i use gimp btw), they also need to be one layered and the same resolution as the logo_ image files. You can completely discard the throbber_ files because they have been dropped in 9.10 (karmic).

What I did was to take an image I already had (1208 x 1024) and resize it down to 139 x 139 and 222 x 222 and so on until i had 4 files. If you want to edit the file already provided, open up gimp or your favourite image editor and click on image > mode > RGB and then you can edit the files, once you're done, click on image > Flatten image and then image > mode > Indexed, and select the normal optimum palette with 256 colors. Save the file and you're done.

Heres a small trick incase you're using an image that doesn't have a black background and you don't want to go through the hassle of making 4 versions of the same file in different sizes.

Just breeze through the usplash-ubuntu-theme.c file and see what file (i.e. logo_large.png or logo_small.png and so on) is selected for your screen resolution and then resize that file to the same resolution (so, in my case screen resolution is 1280 x 1024 and the logo_med.png file is used , therefore, i used an image with dimensions of 1280 x 1024, naming it to logo_med.png). This is what it looks like:

> 
struct usplash_theme usplash_theme_1280_1024 = {
    .version = THEME_VERSION,
    .next = &usplash_theme_1440_900,
        .ratio = USPLASH_4_3,

    /* Background and font */
    .pixmap = &pixmap_logo_med,

        /* position of pixmap */
        .pixmap_x = 664,
        .pixmap_y = 350,
Just change the .pixmap_x = 664, to .pixmap_x = 0,  same for .pixmap_y and bingo, you should have your own image after the grub boot screen.

Once, youre done fiddling around with the images, open up a terminal, cd into the usplash-theme-ubuntu directory and type these commands out:

> 
james@james-desktop:~/usplash-theme-ubuntu$ dpkg-buildpackage -rfakeroot -us -uc
Once it finishes, backup your existing usplash .so file by typing:

> 
james@james-desktop:~/usplash-theme-ubuntu$ sudo cp /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-theme-ubuntu.so.old
and then copy the new .so file that you've just created by typing:

> 
james@james-desktop:~/usplash-theme-ubuntu$ sudo cp usplash-theme-ubuntu.so /usr/lib/usplash/
then do:

> 
james@james-desktop:~/usplash-theme-ubuntu$ sudo update-initramfs -u
and you're done.

Note: To check up on your new usplash screen just type "sudo usplash -c" and it'll come up, you can come back to gnome by pressing Alt + F7

**3- Changing the grub boot screen.**

Back up your /boot/grub/menu.lst file first, by:

> 
james@james-desktop:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
then open up the menu.lst file in /boot/grub/ (Press Alt + F2 and enter gksudo gedit /grub/boot/menu.lst)
scroll down till you see:

> 
#A splash image for the menu
splashimage=/boot/grub/splashimages/FileName.xpm.gz
Download or copy a image of your liking in the /boot/grub/splashimages/ as root and just substitute the FileName.xpm.gz for your image file name, make sure its extension is .gz and its .xpm file type, e.g.

> 
#A splash image for the menu
splashimage=/boot/grub/splashimages/Mac4Lin_GRUB1_v1.0.xpm.gz
save the file and close gedit.
Open up a terminal and do:

> 
james@james-desktop:~$ sudo update-grub
and you're done. Everything customized to your needs and liking. :D

---

### Post by tomski on 2009-12-07
this is incorrect:

# gksudo gdm -u dbus-launch gnome-appearance-properties 

it should be:

# gksudo -u gdm dbus-launch gnome-appearance-properties 

-u = run as user
user = gdm not dbus-launch

other than that this is a great post thanks a bunch :)

shame ubuntu dev's decided on this but hey karmic has had a lot done to it which in my opinion should not have been done

---

### Post by ult_avatar on 2009-12-17
... there is no menu.lst in 9.10. Karmic uses grub2 and therefore you will only find a grub.cfg!

---

### Post by wojox on 2009-12-17
Splash image for grub2: [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by sitonap on 2010-02-09
Bargie,

Many thanks for the usplash customization guide, it was really simple and the only one that actually worked.

---

### Post by Nunu on 2010-02-09
Thanks for a awesome tut... I am going to try this when I get home.

---

### Post by towheedm on 2010-04-28
Really want to customize Grub, USplash, Xsplash and GDM?  Check out the link a the beginning of this thread.
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

