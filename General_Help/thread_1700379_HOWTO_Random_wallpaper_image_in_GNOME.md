---
title: "HOWTO: Random wallpaper image in GNOME"
date: 2011-03-04
forum: General Help
---

### Post by orodoni_le on 2011-03-04
This tutorial is for a GNOME Desktop. I try to made it general, to work in distros not Debian-based

Several options exist to achieve this objective. By default, GNOME uses an .xml file to create a slide-show. However, if you want to create yours, it takes a long time

This solution is based on the post by [llebegue](http://ubuntuforums.org/showthread.php?t=185154), with modifications to the script for added functionality

Just create an script with a meaningful name (background.sh) and save it in an accessible folder: mine is in $HOME/Pictures.
The script should be as follows
```

#!/bin/bash

#################################################################
# Script to select a random wallpaper in GNOME 2		#
#								#
# Selects images from the previously selected wallpapers,	#
# and from a desired folder. Its path should be configured 	#
# in line 31, along with desired image extension 		#
#								#
# The script also selects the rendering method for the image	#
# This feature uses the command "identify", from ImageMagick	#
# Also, check if your distro is using gconftool or gconftool-2	#
# Change this option in lines 50, 52 and 56			#
#								#
# The Delay between images is set in seconds, in line 62	#
#								#
# Create an entry to this script in your "Startup Applications"	#
# to execute it in every gnome session start. The command would	#
# be:								#
# 	PathToScript/background.sh &				#
# The & would run the script as a background process		#
#################################################################

# Begin of infinite loop [condition always true]
while [ 1 == 1 ] ; do

# Create array with the filenames of the previously selected wallpapers,
# from the information in the file "~/.gnome2/backgrounds.xml"
ALIST=( `grep filename ~/.gnome2/backgrounds.xml | sed 's/<filename>//g' | sed 's/<\/filename>//g'` )

# Add to this array the filenames of images '*.JPG' in "$HOME/DATA/Pictures"
# folder. Additional folders could be added with the same syntax
ALIST=( "${ALIST[@]}" `find $HOME/DATA/Pictures/ -name '*.JPG'` )

# Obtain the number of elements in this array
RANGE=${#ALIST[@]}

# Select randomly one of these elements
let "number = $RANDOM % $RANGE"

# Obtain the width and height of the image
xIMG=`identify -format "%[fx:w]" ${ALIST[$number]}` #Width
yIMG=`identify -format "%[fx:h]" ${ALIST[$number]}` #Height

# Compares the Width and Height, to select the rendering option of the image
# If Width > Height, select "zoom"
# Else, select "scaled"
# Possible values: "none", "wallpaper", "centered", "scaled", "stretched", "zoom", "spanned"
if [ "$xIMG" -gt "$yIMG" ] ; then
  gconftool -t string -s /desktop/gnome/background/picture_options zoom
else
  gconftool -t string -s /desktop/gnome/background/picture_options scaled
fi

# Set the random filename as wallpaper image
gconftool -t string -s /desktop/gnome/background/picture_filename ${ALIST[$number]}

# Pause in the script, in seconds. The time the image will remain as wallpaper
# 60   =  1 minute
# 300  =  5 minutes
# 1800 = 30 minutes
sleep 300

# Continue loop
done

```

Copy the script and paste it in your favorite text editor (i.e. gedit). Edit the lines specified in the header. To make the editing process easier, activate the "Display Line Number" options in Edit -> Preferences -> View Tab

Make the script executable. You can right click on the file and change its permissions, or you can run in the terminal, in the same directory you saved the script, assuming that you save it as "background.sh". If you use a different filename, change the command accordingly
```
chmod u+x background.sh
```

Execute from console:
```
PathToScript/background.sh &
```
The & is important to run it as a background process. You can omit it when you are testing if the script works. For testing purposes, reduce the sleep time to 5 seconds. You should see your wallpaper changing every few seconds. If there is any error message in the Terminal, or the images doesn't switch, then something is wrong with the configuration. Check the lines specified in the Header of the script.

Once that the script is working fine, it is a good idea configure it in your startup applications, so it will run every time you start your gnome session.

Configuration options are specified in the header of the script. You can modify the path to folder(s) to look for files, and the image format: *.JPG, *.jpg, *.png, etc. Pay attention to the capitalization of the path and the file extension

Pay special care to the use of ImageMagick, and gconftool (or gconftool-2). You need to install ImageMagick in order to check the image properties (width and height) from the terminal and the script. To confirm that you have it installed, just type
```
identify -version
```

If it gives you an error, you should install it, and the procedure will depend of your distro. In Debian based, type
```
sudo apt-get install imagemagick
```
If you are using Fedora or Red Hat, type as root
```
yum -install imagemagick
```

For the gconftool, check the filename of your current background. Then type
```
gconftool -g /desktop/gnome/background/picture_filename
```
to get the filename (-g option) according to gconftool. If it's not the same as your current background, or it gives you an error, try with gconftool-2
```
gconftool-2 -g /desktop/gnome/background/picture_filename
```
The output should be the filename of your current background

---

### Post by ean5533 on 2011-03-05
Why not just use a program like [DesktopNova]("https://launchpad.net/desktopnova") or [Drapes]("http://drapes.mindtouchsoftware.com/")?

---

### Post by orodoni_le on 2011-03-05
> **ean5533 said:**
> Why not just use a program like [DesktopNova]("https://launchpad.net/desktopnova") or [Drapes]("http://drapes.mindtouchsoftware.com/")?

I made this in a computer without root access (Fedora), so I couldn't install any additional programs. Plus, it was an exercise for scripting, and I though that a simple task like switching the wallpaper shouldn't require additional software. Thanks for the links.

---

### Post by TheTinyt1 on 2011-03-24
Thanks for the info...
Just what I was looking for..

Bright Blessings
TheTiny1:P

---

### Post by hakermania on 2011-03-24
Hey, wallch has a function for exactly this!
See the links at my signature

---

### Post by Joseph.M on 2011-05-03
I did this and only line  changed line 31, 33, and 62.  It is giving me an error about line 49 what did i do wrong?  I have not done any scripting yet so i don't know what to do to fix it. 

```
#!/bin/bash

#################################################################
# Script to select a random wallpaper in GNOME 2		#
#								#
# Selects images from the previously selected wallpapers,	#
# and from a desired folder. Its path should be configured 	#
# in line 31, along with desired image extension 		#
#								#
# The script also selects the rendering method for the image	#
# This feature uses the command "identify", from ImageMagick	#
# Also, check if your distro is using gconftool or gconftool-2	#
# Change this option in lines 50, 52 and 56			#
#								#
# The Delay between images is set in seconds, in line 62	#
#								#
# Create an entry to this script in your "Startup Applications"	#
# to execute it in every gnome session start. The command would	#
# be:								#
# 	PathToScript/background.sh &				#
# The & would run the script as a background process		#
#################################################################

# Begin of infinite loop [condition always true]
while [ 1 == 1 ] ; do

# Create array with the filenames of the previously selected wallpapers,
# from the information in the file "~/.gnome2/backgrounds.xml"
ALIST=( `grep filename ~/.gnome2/backgrounds.xml | sed 's/<filename>//g' | sed 's/<\/filename>//g'` )

# Add to this array the filenames of images '*.JPG' in "$HOME/Pictures/Wallbase"
# folder. Additional folders could be added with the same syntax
ALIST=( "${ALIST[@]}" `find $HOME/Pictures/Wallbase -name '*.JPG''*.png'` )

# Obtain the number of elements in this array
RANGE=${#ALIST[@]}

# Select randomly one of these elements
let "number = $RANDOM % $RANGE"

# Obtain the width and height of the image
xIMG=`identify -format "%[fx:w]" ${ALIST[$number]}` #Width
yIMG=`identify -format "%[fx:h]" ${ALIST[$number]}` #Height

# Compares the Width and Height, to select the rendering option of the image
# If Width > Height, select "zoom"
# Else, select "scaled"
# Possible values: "none", "wallpaper", "centered", "scaled", "stretched", "zoom", "spanned"
if [ "$xIMG" -gt "$yIMG" ] ; then
  gconftool -t string -s /desktop/gnome/background/picture_options zoom
else
  gconftool -t string -s /desktop/gnome/background/picture_options scaled
fi

# Set the random filename as wallpaper image
gconftool -t string -s /desktop/gnome/background/picture_filename ${ALIST[$number]}

# Pause in the script, in seconds. The time the image will remain as wallpaper
# 60   =  1 minute
# 300  =  5 minutes
# 1800 = 30 minutes
sleep 15

# Continue loop
done
```

---

### Post by ean5533 on 2011-05-03
> **Joseph.M said:**
> I did this and only line  changed line 31, 33, and 62.  It is giving me an error about line 49 what did i do wrong?  I have not done any scripting yet so i don't know what to do to fix it. 

*snip*

The problem is actually with what you changed on line 33. You can't have multiple names just separated by groups of quotes; you need to separate them with the **-o** switch. So on line 33, replace this part:

```
-name '*.JPG''*.png'
```

...with this:

```
-name '*.JPG' -o -name '*.png'
```

I haven't had a chance to actually test that, but it should work.

---

### Post by Joseph.M on 2011-05-03
#-o I should have known that, Thanks a bunch!

---

### Post by orodoni_le on 2011-05-09
Linux it sensitive to the capitalization of the file names.
Thus, if you want, in line 33, you can put
```

-iname '*.JPG' -o -iname '*.png'

```
to ignore the character cases of the file extension. In other words, it will recognize *.JPG, *.jpg, and weird combinations like *.JpG. The same with the PNG files.

---

### Post by maverick280857 on 2011-05-21
Does this work in GNOME 3?

---

### Post by halovivek on 2011-05-21
> **ean5533 said:**
> Why not just use a program like [DesktopNova]("https://launchpad.net/desktopnova") or [Drapes]("http://drapes.mindtouchsoftware.com/")?

i am using DesktopNova and its doing fine.
Thanks for the new one.
I will try this in another system :)

---

### Post by maverick280857 on 2011-05-22
> **halovivek said:**
> i am using DesktopNova and its doing fine.
Thanks for the new one.
I will try this in another system :)

I'm assuming this is still Gnome 2 you're talking about? DesktopNova doesn't work for me on Gnome 3..

---

### Post by linuxinstalledfromhdd on 2011-05-22
I like Gnome Wallpaer slideshow.

wget [http://gnome-look.org/CONTENT/content-files/125178-gnome-wallpaper-slideshow.tar.gz](http://gnome-look.org/CONTENT/content-files/125178-gnome-wallpaper-slideshow.tar.gz)

tar zxvf 125178-gnome-wallpaper-slideshow.tar.gz && ./gnome-wallpaper-slideshow

---

### Post by maverick280857 on 2011-05-22
> **linuxinstalledfromhdd said:**
> I like Gnome Wallpaer slideshow.

wget [http://gnome-look.org/CONTENT/content-files/125178-gnome-wallpaper-slideshow.tar.gz](http://gnome-look.org/CONTENT/content-files/125178-gnome-wallpaper-slideshow.tar.gz)

tar zxvf 125178-gnome-wallpaper-slideshow.tar.gz && ./gnome-wallpaper-slideshow

This does not work on Gnome3 either.

**Has anyone gotten a dynamic wallpaper thing to work in Gnome 3?**

---

### Post by maverick280857 on 2011-05-24
Please see [http://ubuntuforums.org/showthread.php?t=1764695](http://ubuntuforums.org/showthread.php?t=1764695).

---

### Post by linuxinstalledfromhdd on 2011-05-24
Gnome 3 is in development.

---

### Post by maverick280857 on 2011-05-24
> **linuxinstalledfromhdd said:**
> Gnome 3 is in development.

I believe I have found a partial solution to the problem in the form of a Perl script. I have described the link and provided references here:

[http://ubuntuforums.org/showpost.php?p=10858322&postcount=8](http://ubuntuforums.org/showpost.php?p=10858322&postcount=8)

But I am still trying to figure out how to execute this script automatically after logging into gnome3.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Did you make it executable and put it in your PATH?

---

### Post by maverick280857 on 2011-05-24
> **linuxinstalledfromhdd said:**
> Did you make it executable and put it in your PATH?

Yes, but its a Perl script, and it resides in $HOME. What do you mean by making it executable? It's executed using a terminal command 

```
perl shifter & 
```

---

### Post by maverick280857 on 2011-05-24
I also changed the permissions

```
chmod +x shifter
```

and added it to gnome-session-properties, but it apparently does not get executed at all.

---

### Post by maverick280857 on 2011-05-24
Creating a file by the name shifter.desktop under $HOME/.config/autostart/ with the following lines, solved the problem.

```

[Desktop Entry]
Type=Application
Exec=/home/username/shifter &
Hidden=false
X-GNOME-Autostart-enabled=true
Name[en_US]=shifter
Name=shifter
Comment[en_US]=Rotate wallpaper
Comment=Rotate wallpaper

```

---

### Post by 23dornot23d on 2011-05-24
Great sorted ..... like this and so lightweight and fast ..... just got it like a slide show going through all my photos ...... great addition .... ;)

Thanks for posting the code to autostart it too .... what do you name this file ? (shifter)

---

### Post by maverick280857 on 2011-05-24
> **23dornot23d said:**
> Great sorted ..... like this and so lightweight and fast ..... just got it like a slide show going through all my photos ...... great addition .... ;)

Thanks for posting the code to autostart it too .... what do you name this file ?

You're welcome. I just called it 'shifter' but you are free to name it whatever you want of course. If its named 'filename' then you need a 'filename' script in $HOME and correspondingly a filename.desktop file in $HOME/.config/autostart/.

---

### Post by 23dornot23d on 2011-05-24
Ok thanks got it .... its really good ..... do you know how to change the login greeter
background too ?

Some code like this there would be neat - if its fast enough we could animate something ......

---

### Post by maverick280857 on 2011-05-24
> **23dornot23d said:**
> Ok thanks got it .... its really good ..... do you know how to change the login greeter
background too ?

Some code like this there would be neat - if its fast enough we could animate something ......

I was just going to ask *you* that :-P. I was trying this

[https://bbs.archlinux.org/viewtopic.php?pid=930084](https://bbs.archlinux.org/viewtopic.php?pid=930084)

but I am unable to get it to work. If you can, give it a shot and let us know if it works and if so, how you got it to work.

---

### Post by 23dornot23d on 2011-05-24
> **maverick280857 said:**
> I was just going to ask *you* that :-P. I was trying this

[https://bbs.archlinux.org/viewtopic.php?pid=930084](https://bbs.archlinux.org/viewtopic.php?pid=930084)

but I am unable to get it to work. If you can, give it a shot and let us know if it works and if so, how you got it to work.


Ok will have a look now ......  ;) ty
> 
I am logging in through kdm at the moment on this system .... sorry will be tomorrow before I get chance
to try it out ....... but looks simple enough ...... just added dconf from the repository as it was not there.
  was an error out on the first copy command ..... 


---

### Post by maverick280857 on 2011-05-24
> **23dornot23d said:**
> Ok will have a look now ......  ;) ty

The script in post #19 of that link ([https://bbs.archlinux.org/viewtopic.php?pid=930084](https://bbs.archlinux.org/viewtopic.php?pid=930084)) does not work for me.

---

### Post by RedMcGregor on 2011-12-09
Very nice, cheers!

---

