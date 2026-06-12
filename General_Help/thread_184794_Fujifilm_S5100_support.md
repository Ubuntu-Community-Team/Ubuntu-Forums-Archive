---
title: "Fujifilm S5100 support?"
date: 2006-05-30
forum: General Help
---

### Post by Joseph Elliott on 2006-05-30
i cant seem to get my computer to recognise my digi cam, can anyone help me this is my first time using a linux system

---

### Post by mkoyle on 2006-06-24
[QUOTE=Joseph Elliott]i cant seem to get my computer to recognise my digi cam, can anyone help me this is my first time using a linux system[/QUOTE]

[SIZE="4"]The problem[/SIZE]

If you are using Ubuntu, you can get the pictures and edit them in Ubuntu.  It is a little more difficult than on windows with the Fuji program (or better, S7Raw: [http://www.geocities.co.jp/SiliconValley-PaloAlto/9919/s7raw.html](http://www.geocities.co.jp/SiliconValley-PaloAlto/9919/s7raw.html) ), but it can be done.

Right now, when I plug in my S5100 (and presumably most of the Fuji cameras will be the same), I get a message about importing pictures: "A photo card has been detected ... Ignore or Import Photos."  Currently, the Import Photos option does not work in default Ubuntu because the gthumb program (which handles a lot of cameras) does not know what to do with Fuji's proprietary format.

We have two options if we want to use Ubuntu: use JPG in the camera (not great but okay) or import every picture manually (which is what you have to do in Windows if you want to make sure every one is of good quality).

If you want to get the files on your hard drive using that "Import Photos" button, I can show you how.  But first, let me show you that you can get the photos manually.

[SIZE="4"]Where the files are:[/SIZE]

If everything is working properly (USB drivers and Ubuntu's default actions) you will have an icon on the desktop for 'usbdisk' or something like that which will be the filesystem of your camera.  If you open that (and have a s5100) there is a directory DCIM and in that directory is 100_FUJI and there are your pictures.  The .RAF files are the proprietary ones (the pictures you get when you go into the camera's menu and turn on CCD-RAW before taking your pictures).

[SIZE="4"]Getting pictures into GIMP photo editor[/SIZE]

To edit those pictures in GIMP, you will need the GIMP UFRAW plugin (gimp-ufraw).  The easiest way to get this is to open a terminal (it is called Terminal in the menu under Applications) and you will get a command prompt (mine says "matthew@ruth:~$").  Type 

sudo apt-get install gimp-ufraw

and you are done with that.  That gets software off the internet, so you need to be connected when you do that.  Now, when you are looking at a .RAF file or a .JPG file if you right click and click "open with other application" you can pick GIMP and it will open UFRAW.  You will want to move the controls around until it looks okay (you can find UFRAW tutorials if you need to) and then click OK.  Now you have the file in GIMP and you can edit and save as about any file type you might need to (most commonly .JPG for low-quality and .TIF / .GIF for high quality).

If anyone needs help after stumbling across this, they can email me... I think you can get my email if you register.  Later I will post the file I create that copies my files from the camera onto the computer automatically.  I did it once before but ... silly me ... I did something with that system and started over without saving my script.

--Matthew

---

### Post by mkoyle on 2007-02-03
Here is the bash script I use to copy photos from my FujiFilm S5100 to the directory I want them in on my computer.  I then use s7raw.exe inside wine to batch-convert all of my pictures.  The script should actually work for about any camera.  To use this script, you would 

1. open a terminal (in Edgy that is Applications --> Accessories --> Terminal) and then run

sudo gedit /usr/bin/camera-script

2. then paste the file information below into the new file, save, and exit from gedit.

3. Now change the permissions of the new script so it can be executed:

sudo chmod 755 /usr/bin/camera-script

4. Finally, change Ubuntu's default setting for when a camera is detected by going to System --> Preferences --> Removable Devices, selecting Cameras, and puting the following in the 'Command' line:

gnome-terminal -x /usr/bin/camera-script %h

> #!/bin/sh
# Script for importing photos from a digital camera to /shared/Pictures
# I set this script to run when the system detects a usb camera and it
# imports my photos.  To do this, I go to System-->Preferences-->Removable Devices
# select Cameras, and put 
# gnome-terminal -x /usr/bin/camera-script %h
# in the Command box after checking the "Import digital photographs when connected" box.

## The following are descriptions of variables; 
## changing them will modify the output of the script.

# Set the directory where pictures will be saved; 
# include the entire directory name from the root filesystem 
# (make it the directory name that will allow the 'cd' command
# to go there no matter what your starting directory is.
pictures="/shared/Pictures"
echo $pictures

# Note: The end output directory will be today's date in the YYYY_mmdd format.
subdir=$(date '+%Y_%m%d')
echo $subdir

MOUNT_POINT=$(hal-get-property --udi "$1" --key volume.mount_point)
if test -z "$MOUNT_POINT"; then
  cd "$pictures"
  mkdir -v "$subdir"
  cd "$subdir"
  cp -v "${MOUNT_POINT}"/* .

else
  ROOT=${MOUNT_POINT}
  dcim=$(ls "${ROOT}" | grep -i dcim)
  if [ $? -eq 0 ]; then
    ROOT="${ROOT}/$dcim"
    # if there is only one dir in the dcim directory, enter it
    if test $(/bin/ls -1 "${ROOT}" | wc -l)  -eq 1; then
      ROOT="${ROOT}/$(ls -1 "${ROOT}" | head -n 1)"
    fi
  fi
  cd $pictures
  mkdir -v $subdir
  cd $subdir
  cp -v "${ROOT}"/* .
fi

---

### Post by mkoyle on 2007-07-07
I recently stumbled across another useful package:

 apt-get install gnome-raw-thumbnailer

Makes filesystem windows display thumbnails of Fuji (and other) raw files (.RAF).

--Matthew

---

### Post by timcredible on 2007-07-25
i ran into this problem with a s5200 and s6000fd.  i found that there's a bug submitted for it, and there was a solution involving adding the vendor id and model id from lsusb into the file that the photo program uses.  sorry i don't have more info, but if you do a search in google you should find that bug report along with how to get your camera to be accessible with gphoto and digikam.

---

### Post by mkoyle on 2008-05-20
Sorry to keep posting new information here, but if someone is looking about S5100 (or other Fuji camera Ubuntu info) it's useful if it is all together.  

To make s7raw automatically open Fuji .raf files in Ubuntu, one option is to create a script to make wine use s7raw to open it.

If you haven't already, install wine:

```
sudo aptitude install wine
```

Run winecfg to create a wine directory for your user:

```
winecfg
```

Download s7raw [http://www.geocities.co.jp/SiliconValley-PaloAlto/9919/s7raw.html#Download](http://www.geocities.co.jp/SiliconValley-PaloAlto/9919/s7raw.html#Download) create a s7raw directory in your Program Files directory (should be ~/.wine/drive_c/Program Files) and unpack s7raw there.

Now, run the following command to create a new script file:

```
gedit ~/.wine/drive_c/Program\ Files/s7raw/wine_s7raw
```

Paste the following into the new file:

```
#!/bin/sh

QUICKPARLOCATION="c:\\Program Files\\s7raw\\s7raw.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0

```

Exit and make the new file executable:

```
chmod 755 ~/.wine/drive_c/Program\ Files/s7raw/wine_s7raw
```

Now open a directory with .raf files in it, right click on one, and (in Hardy) go to 'Open with' --> 'open with other application'

Click the arrow by 'Use a custom command' and in the box that appears, paste the following, but replace 'YOUR_USERNAME' with your username that you use to log in.

```
/home/YOUR_USERNAME/.wine/drive_c/Program\ Files/s7raw/wine_s7raw
```

Now when you double click on those files, they should open right up.

---

