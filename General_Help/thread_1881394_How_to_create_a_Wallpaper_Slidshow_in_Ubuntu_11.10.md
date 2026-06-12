---
title: "How to create a Wallpaper Slidshow in Ubuntu 11.10"
date: 2011-11-15
forum: General Help
---

### Post by anur.bhargav on 2011-11-15
I like to have my wallpapers changing constantly.. I used "Crebs" in "Ubuntu 11.04" which generated an XML and I used to add them to the 'Change Desktop Background' Window and select them, and I was done. Just like the default wallpaper slideshow I just had to select it.

I know that we have Wallch. But that has to be kept running in the background and that is something I'd like to avoid.

There must be a way to include custom XML's. Please tell me how ?:)

---

### Post by em3raldxiii on 2011-12-29
I have been trying to use the directions on this page:

[http://askubuntu.com/questions/71008/how-do-i-customize-desktop-wallpaper-slideshow](http://askubuntu.com/questions/71008/how-do-i-customize-desktop-wallpaper-slideshow)

This has allowed me to add a slideshow (XML) that used to work in Gnome (Ubuntu 10.04) to my "Change Desktop Background" configurator in Unity (Ubuntu 11.10), but so far, the thumbnail remains black AND when I click on it, it breaks the window manager.  It sorta looks like Metacity crashes or something - all my window borders vanish and I can't close any apps.  If I happen to have a terminal open, I can do [COLOR="Red"]metacity --replace[/COLOR] long enough to change my wallpaper back.  It ultimately leaves me having to log out or reboot though.  I will keep you posted if I come up with any solutions.  Let me know if you come up with something :D

EDIT:  I have tentatively solved my problem.  It seems that the root of the issue was that I had changed my username on my new install, thus breaking the absolute path to the images (since they were in my Home directory).  Second (and not sure if this is a requirement since I did this plus the absolute path repair at the same time) is that I put the XML file into the [COLOR="Red"]/usr/share/gnome-background-properties/ folder[/COLOR].  This apparently is automatically added to the thumbnail list of backgrounds in the background configurator.  My next post will be a complete tutorial from start to finish.

---

### Post by em3raldxiii on 2011-12-29
**[COLOR="Blue"]_How to make a Wallpaper Slideshow Without Additional Software_[/COLOR]**

**_Explanation_**:
Many of us have created wallpaper slideshows in the past by creating a simple XML file and then pointing the default wallpaper configuration utility (right-click > change background) to this new file.  It seems that in Ubuntu 11.10 (and perhaps others) this is no longer enabled.  Basically, in Unity, the wallpaper configuration utility does not allow you to choose XML files.  I suspect this will be addressed in the near future because it's not that the wallpaper system *can't*, it's simply because the file browser in this system ignores anything except image files, so you just can't click on the XML file you created.

**_STEPS_**

1. Put all of your images into a directory.
2. Generate an XML file with absolute paths to the images.
3. Tell the wallpaper system where to find the new XML Slideshow.
4. Open the wallpaper configuration utility and choose the new Slideshow.

**_DETAILED INSTRUCTIONS_**

_Step 1:  Putting all of your images into a directory_

A. I recommend using all of one image of type.  So far, I have only tested this using .jpg files, and I carefully resized them to all be 100% identical in resolution.  I used TheGimp image editor for this, but there are other tools.  This is not mission critical, but will give you nice results.

B. Use a reliable directory for your images because any changes to this folder's location will ultimately break your slideshow (and possibly crash Unity) due to absolute file paths.  I have a directory (which is actually on a different partition) that is located at root level.  It is my understanding that this will work for a directory located anywhere on your system, but it's good to standardize.  Keep this in mind, particularly if you use symlinks for your directory locations.

C. For my example, I am going to use [COLOR="DarkRed"]/multimedia/Pictures/Backgrounds/My_Folder[/COLOR] and I am going to use 3 images named [COLOR="darkred"]image01.jpg, image02.jpg, and image03.jpg, and my resulting XML file will be my_slideshow.xml[/COLOR].

_Step 2:  Generating your XML file._

A. A quick solution is to copy [COLOR="darkred"]/usr/share/backgrounds/contest/background-1.xml[/COLOR] to a new file (you might want to put it in your home directory until it's ready for use) and then change the absolute paths inside this file to point to your images.  Again, make darned sure you get the pathways absolutely correct.

B. You can manually create one like this:
```
<background>
  <starttime>
    <year>2009</year>
    <month>08</month>
    <day>04</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
  <!-- This animation will start at midnight. -->
  <static>
    <duration>30</duration>
    <file>/multimedia/Pictures/Backgrounds/My_Folder/image01.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/multimedia/Pictures/Backgrounds/My_Folder/image01.jpg</from>
    <to>/multimedia/Pictures/Backgrounds/My_Folder/image02.jpg</to>
  </transition>
  <static>
    <duration>30</duration>
    <file>/multimedia/Pictures/Backgrounds/My_Folder/image02.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/multimedia/Pictures/Backgrounds/My_Folder/image02.jpg</from>
    <to>/multimedia/Pictures/Backgrounds/My_Folder/image03.jpg</to>
  </transition>
  <static>
    <duration>30</duration>
    <file>/multimedia/Pictures/Backgrounds/My_Folder/image03.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>-</from>
    <to>/multimedia/Pictures/Backgrounds/My_Folder/image01.jpg</to>
  </transition>
</background>
```

Save this as [COLOR="darkred"]my_slideshow.xml[/COLOR] in the directory that contains your images.

C. You can use a script to automagically create your XML file instead.  I have attached a script (I no longer have the information as to where I got this script, but kudos to the author).  Put this script into the directory with your images, and run it from the command prompt.  It will give you the correct syntax.  Again, I have to reiterate, you must use precisely the correct path.

_Step 3:  Pointing the wallpaper system to look for the XML file._

A. There should be a file named [COLOR="darkred"]ubuntu-wallpapers.xml[/COLOR] located inside [COLOR="darkred"]/usr/share/gnome-background-properties[/COLOR]. You should back this file up (if it exists) before proceeding.  In a terminal, type this:
```
sudo cp /usr/share/gnome-background-properties/ubuntu-wallpapers.xml /usr/share/gnome-background-properties/ubuntu-wallpapers.xml.backup

B. Now we need to edit that file so that it knows where to find your new XML file:
[CODE]gksu gedit /usr/share/gnome-background-properties/ubuntu-wallpapers.xml
```
Just before [COLOR="darkred"]</wallpapers>[/COLOR] at the bottom, add your XML information like this:
```

  <wallpaper deleted="false">
    <name>Sexy</name>
    <filename>/multimedia/Pictures/Backgrounds/My_Folder/my_slideshow.xml</filename>
    <options>zoom</options>
  </wallpaper>

```

_Step 4:  Enable your new slideshow._

A. Right-click on your desktop and choose *Change Desktop Background*.  In the left hand pane of thumbnails, you should now see a thumbnail with a little clock icon on it in the corner indicating the new slideshow.  CAUTION!  If this thumbnail is black DO NOT CLICK!  If it's black, it means you have made an error somewhere in the steps.  The first thing to do is manually check the XML file and determine that it points to PRECISELY the correct location (including capital letters).  If the thumbnail appears to be one of the images from your directory, then you should be safe to click on it.

ENJOY!

Please leave feedback and I will modify my tutorial as needed.  One of these days I will get around to modifying the script to automagically doing everything for you, but until then this tutorial should get'er done.

---

### Post by em3raldxiii on 2011-12-30
Okay, so I ended up staying up a little too late and working on my script.  I basically just modified (extensively!) the one I uploaded earlier.  Here is the script itself for those who would like a closer look:

```

#!/bin/bash

if [ $# -lt 2 ]
then
    echo
    echo
    echo "You are missing some parameters."
    echo
    echo "example: $0 *.jpg"
    echo
    exit 1
fi

echo -n "Give a name to your new wallpaper slideshow: "; read showname
echo -n "How many seconds do you want each image to display before switching? "; read hold
echo -n "How many seconds would you like the transition to take? "; read fade

#params
outfile=backgrounds.xml
parent=WallpaperSlideshows
wallpaper_config_file="/usr/share/gnome-background-properties/ubuntu-wallpapers.xml"

#DEBUG
echo
echo "Executing ..."
echo "Output to $outfile"

#remove hold parameter
#shift
#remove fade parameter
#shift

( #all of the contents in parentheses will be output to the outfile.
echo "<background>"
echo "  <starttime>"
echo "    <year>2011</year>"
echo "    <month>01</month>"
echo "    <day>01</day>"
echo "    <hour>00</hour>"
echo "    <minute>00</minute>"
echo "    <second>00</second>"
echo "  </starttime>"

while [ $# -gt 0 ]
do
    echo "  <static>"
    echo "    <duration>$hold</duration>"
    echo "    <file>$HOME/$parent/$showname/$1</file>"
    echo "  </static>"
    echo "  <transition>"
    echo "    <duration>$fade</duration>"
    echo "    <from>$HOME/$parent/$showname/$1</from>"
    if [ $# -gt 1 ]
    then
        echo "    <to>$HOME/$parent/$showname/$2</to>"
    else
        echo "    <to>$HOME/$parent/$showname/$first</to>"
    fi
    echo "  </transition>"
    shift
done
echo "</background>"
#Closing parenthesis marks the end of material to be output to the outfile.
)>$outfile

echo "Please Note:  This script should handle files with the .jpg or .png extension"
echo "Copying images to ~/"$parent"/"$showname
mkdir -p ~/$parent/$showname
cp *.jpg ~/$parent/$showname
cp *.png ~/$parent/$showname
cp $outfile ~/$parent/$showname
echo "Backing up wallpaper configuration file ..."
cp $wallpaper_config_file $HOME/WallpaperSlideshows/ubuntu-wallpapers.xml.backup
echo "Adding new slideshow to wallpaper configuration file ..."
sed "
/<\/wallpapers>/ i\
\  <wallpaper deleted=\"false\">\n\
\    <name>$showname<\/name>\n\
\    <filename>$HOME\/$parent\/$showname\/backgrounds.xml<\/filename>\n\
\  <\/wallpaper>" $wallpaper_config_file>$HOME/$parent/$showname/temp_config_file.xml
sudo cp $HOME/$parent/$showname/temp_config_file.xml $wallpaper_config_file
echo "Done."

```

And I have also included the file as an attachment.  To use this file, you have to enable execution.  You can do this by chmod +x MakeSlideShow.sh or by right-clicking>Properties>Permissions and checking the box Execute.

HOW TO USE:

Move the file to the directory that contains the images you would like to use for a slideshow.  Make sure you pick good pictures (so far only .jpg or .png work, and not both simultaneously yet).  Make sure it's executable as I said.  Open a terminal, navigate to the folder that contains the script file and the images, and type this at the prompt:

./MakeSlideShow.sh *.jpg

Of course, change the .jpg to .png if that is what you have.

WHAT IT DOES:

It prompts you to name the slideshow and it uses that name as part of the path, in addition to the name in the wallpaper configuration screen.  Next, it asks how long each picture should be up on the screen in seconds.  Finally it asks for how long the transition should take from one picture to the next, in seconds.  It will ask you for your SUDO password in order to make the changes to the ubuntu-backgrounds.xml file.  It then copies all the pictures & the new XML file to a standardized directory, backs up the ubuntu-wallpapers.xml file into that folder, and then modifies the ubuntu-wallpapers.xml file to include your new slideshow.

Now you can right-click on your desktop and choose the new slideshow from the backgrounds thumbnails.  CAUTION:  If the thumbnail is black, the script may have made an error.  If this happens, copy your backed up ubuntu-wallpapers.xml file back to /usr/share/gnome-background-properties/ folder.

Finally, if this somehow screws up everything, you can do this:

sudo aptitude reinstall ubuntu-wallpapers

Have fun!

---

### Post by em3raldxiii on 2011-12-30
Upon further reflection, it looks like the gnome-desktop-backgrounds directory can contain more than one .xml file pointing to stuff.  I wonder if instead of modifying the existing ubuntu-wallpapers.xml file, we should instead be generating a separate .xml file for each slideshow.  It seems a little redundant to have an xml file pointing to an xml file pointing to the images.  I am not sure which solution seems more elegant.  I will pursue this matter another day.  For now, I have to hit the sack; I have a real-life job that requires a bit of alertness.

---

### Post by subhojit on 2012-02-11
> **em3raldxiii said:**
> **[COLOR="Blue"]_How to make a Wallpaper Slideshow Without Additional Software_[/COLOR]**

**_Explanation_**:
Many of us have created wallpaper slideshows in the past by creating a simple XML file and then pointing the default wallpaper configuration utility (right-click > change background) to this new file.  It seems that in Ubuntu 11.10 (and perhaps others) this is no longer enabled.  Basically, in Unity, the wallpaper configuration utility does not allow you to choose XML files.  I suspect this will be addressed in the near future because it's not that the wallpaper system *can't*, it's simply because the file browser in this system ignores anything except image files, so you just can't click on the XML file you created.

**_STEPS_**

1. Put all of your images into a directory.
2. Generate an XML file with absolute paths to the images.
3. Tell the wallpaper system where to find the new XML Slideshow.
4. Open the wallpaper configuration utility and choose the new Slideshow.

**_DETAILED INSTRUCTIONS_**

_Step 1:  Putting all of your images into a directory_

A. I recommend using all of one image of type.  So far, I have only tested this using .jpg files, and I carefully resized them to all be 100% identical in resolution.  I used TheGimp image editor for this, but there are other tools.  This is not mission critical, but will give you nice results.

B. Use a reliable directory for your images because any changes to this folder's location will ultimately break your slideshow (and possibly crash Unity) due to absolute file paths.  I have a directory (which is actually on a different partition) that is located at root level.  It is my understanding that this will work for a directory located anywhere on your system, but it's good to standardize.  Keep this in mind, particularly if you use symlinks for your directory locations.

C. For my example, I am going to use [COLOR="DarkRed"]/multimedia/Pictures/Backgrounds/My_Folder[/COLOR] and I am going to use 3 images named [COLOR="darkred"]image01.jpg, image02.jpg, and image03.jpg, and my resulting XML file will be my_slideshow.xml[/COLOR].

_Step 2:  Generating your XML file._

A. A quick solution is to copy [COLOR="darkred"]/usr/share/backgrounds/contest/background-1.xml[/COLOR] to a new file (you might want to put it in your home directory until it's ready for use) and then change the absolute paths inside this file to point to your images.  Again, make darned sure you get the pathways absolutely correct.

B. You can manually create one like this:
```
<background>
  <starttime>
    <year>2009</year>
    <month>08</month>
    <day>04</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
  <!-- This animation will start at midnight. -->
  <static>
    <duration>30</duration>
    <file>/multimedia/Pictures/Backgrounds/My_Folder/image01.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/multimedia/Pictures/Backgrounds/My_Folder/image01.jpg</from>
    <to>/multimedia/Pictures/Backgrounds/My_Folder/image02.jpg</to>
  </transition>
  <static>
    <duration>30</duration>
    <file>/multimedia/Pictures/Backgrounds/My_Folder/image02.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/multimedia/Pictures/Backgrounds/My_Folder/image02.jpg</from>
    <to>/multimedia/Pictures/Backgrounds/My_Folder/image03.jpg</to>
  </transition>
  <static>
    <duration>30</duration>
    <file>/multimedia/Pictures/Backgrounds/My_Folder/image03.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>-</from>
    <to>/multimedia/Pictures/Backgrounds/My_Folder/image01.jpg</to>
  </transition>
</background>
```

Save this as [COLOR="darkred"]my_slideshow.xml[/COLOR] in the directory that contains your images.

C. You can use a script to automagically create your XML file instead.  I have attached a script (I no longer have the information as to where I got this script, but kudos to the author).  Put this script into the directory with your images, and run it from the command prompt.  It will give you the correct syntax.  Again, I have to reiterate, you must use precisely the correct path.

_Step 3:  Pointing the wallpaper system to look for the XML file._

A. There should be a file named [COLOR="darkred"]ubuntu-wallpapers.xml[/COLOR] located inside [COLOR="darkred"]/usr/share/gnome-background-properties[/COLOR]. You should back this file up (if it exists) before proceeding.  In a terminal, type this:
```
sudo cp /usr/share/gnome-background-properties/ubuntu-wallpapers.xml /usr/share/gnome-background-properties/ubuntu-wallpapers.xml.backup

B. Now we need to edit that file so that it knows where to find your new XML file:
[CODE]gksu gedit /usr/share/gnome-background-properties/ubuntu-wallpapers.xml
```
Just before [COLOR="darkred"]</wallpapers>[/COLOR] at the bottom, add your XML information like this:
```

  <wallpaper deleted="false">
    <name>Sexy</name>
    <filename>/multimedia/Pictures/Backgrounds/My_Folder/my_slideshow.xml</filename>
    <options>zoom</options>
  </wallpaper>

```

_Step 4:  Enable your new slideshow._

A. Right-click on your desktop and choose *Change Desktop Background*.  In the left hand pane of thumbnails, you should now see a thumbnail with a little clock icon on it in the corner indicating the new slideshow.  CAUTION!  If this thumbnail is black DO NOT CLICK!  If it's black, it means you have made an error somewhere in the steps.  The first thing to do is manually check the XML file and determine that it points to PRECISELY the correct location (including capital letters).  If the thumbnail appears to be one of the images from your directory, then you should be safe to click on it.

ENJOY!

Please leave feedback and I will modify my tutorial as needed.  One of these days I will get around to modifying the script to automagically doing everything for you, but until then this tutorial should get'er done.

thank you very much!

---

### Post by pashilkar on 2012-05-14
Found a small bug in the script. The variable '*first*' is not assigned any value. This makes the slide show stop on the last image instead of looping. To fix the bug, just add the following line before the *while* loop.
```
first=$1
```

---

### Post by twengg on 2012-07-29
Thanks dude for the script. If it does not seem to work, it is a good idea to change all slideshow picture permissions to read only. 
You can do this by entering 'sudo nautilus' in a terminal, go to the 'wallpaperslideshows' folder, select all pictures and set all permissions to read only. 
Thanks once more!!

---

