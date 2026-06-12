---
title: "Lightscribe Software for Linux..."
date: 2010-01-22
forum: General Help
---

### Post by casparov on 2010-01-22
Hi Everyone... 

I am running Karmic and my Lightscribe DVD works beautifully w/ the very basic Linux application release for Lightscribe burners.  

Can anyone suggest a competent burning program which will, at least, allow me to drag and drop an image into the mix?  

Thanks so much,

C.

---

### Post by timgood on 2010-01-22
This page has details of Lacie's 4L which will do what you want:

[http://www.linux.com/archive/feed/118705](http://www.linux.com/archive/feed/118705)

Hope this helps.

---

### Post by Uncle Spellbinder on 2010-01-22
The official LightScribe System Software and LightScribe Simple Labeler are available for Linux in rpm and deb files at the LightScribe site.

LightScribe System Software: [http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372](http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372)

Or LightScribe Simple Labeler here: [http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1374](http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1374)

---

### Post by jollins69 on 2010-02-19
i too am looking for a lightscribe burning program. 
The simple one isnt good enough as it only allows text and the other you mentioned gives a link to removed files! shame as it seems the only place to get it :(

---

### Post by texla on 2010-08-03
You can download it elsewhere:

From the help forum: [https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

Download the [LaCie 4L Labeler utility "deb package"]("http://uploads.mitechie.com/lightscribe/4l_1.0-r6_i386.deb") software.

This is how I set up the whole lightscribe program (I have an hp drive already installed)

Downloaded lightscribe software deb for linux here:
[http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814)

clicked on deb to install

then downloaded the 4L labeler from the link above

clicked on deb to install

then from this how to in the forums I did these steps  to make a shortcut for 4L: 
[http://ubuntuforums.org/showthread.php?t=809112](http://ubuntuforums.org/showthread.php?t=809112)[FONT=monospace]
[/FONT]
(none of the other steps seem to apply for lucid...?):

checked to see if the labeler worked by typing this in terminal: [FONT=monospace]
gksudo 4L-gui

then I added the shortcut like this:
[/FONT]6. Create a shortcut to launch the 4L Disk Labeler as root
a. Right Click on the Ubuntu Menu Bar and choose Edit Menus.
b. In the left pane labeled menus choose either "Sound & Video" or "System Tools".
c. Then, click new item.
Enter this information into the window:
     Code:
     Type: Application Name: Lightscribe Command: gksudo 4L-gui Comment: Label a disc with Lightscribe [SIZE=3]

[/SIZE]Results:  works great - faint graphics can be reburnt to make them darker - it automatically centers the disk for this so you can put it back in for a second burn. Biggest issues are - the Lacie 4L program takes images only so you need a gimp template to work with and save it as a jpeg - and it takes a long time!  especially for two burns (25 minutes per burn!)

cool Gimp template here:[SIZE=3]
[/SIZE][URL="http://www.vitalbodies.net/site/tech-web/tech/111-open-source-cddvd-cover-for-open-source-projects.html"]http://www.vitalbodies.net/site/tech-web/tech/111-open-source-cddvd-cover-for-open-source-projects.html
[/URL][SIZE=3]


[/SIZE]

---

### Post by jollins69 on 2010-12-11
Thank you. this was very useful

---

### Post by texla on 2011-01-15
[SIZE=2]And for Lightscribe on 64bit Maverick:
download to home folder:
1: [LIGHTSCRIBE SYSTEM SOFTWARE]("http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814")
2: [LIGHTSCRIBE SIMPLE LABELER]("http://www.lightscribe.com/downloadSection/linux/index.aspx?id=815")
from: [http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

[/SIZE] [SIZE=2]Then, in terminal install the 32-bit compatibility package: [/SIZE]
[FONT=Arial][SIZE=2]sudo apt-get install ia32-libs   (mine was already installed and up to date)[/SIZE][/FONT]

[FONT=Arial][SIZE=2]next, in terminal force the 32 bit programs to install:[/SIZE][/FONT][FONT=Arial][SIZE=2]
(changing the files to the name of current downloaded version if needed)

sudo dpkg -i --force-architecture lightscribe-1.18.28.1-linux-2.6-intel.deb
[/SIZE][/FONT][FONT=Arial][SIZE=2]sudo dpkg -i --force-architecture lightscribeApplications-1.18.15.1-linux-2.6-intel.deb

(note: version numbers may change - ex: [/SIZE][/FONT][FONT=Arial][SIZE=2]1.18.28.1 could become a newer version like 1.19.0 so [/SIZE][/FONT][FONT=Arial][SIZE=2]just change them if you get an error message)

next:
sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/
sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/
sudo ldconfig

[SIZE=2]then download Lacie program here so you can add your own images:
[/SIZE][/SIZE][/FONT][FONT=Arial][SIZE=2][http://principialabs.com/files/4l_1.0-r6_i386.deb](http://principialabs.com/files/4l_1.0-r6_i386.deb)

install:
sudo dpkg --install --force-architecture 4l_1.0-r6_i386.deb[/SIZE][/FONT][FONT=Arial][SIZE=2]

The following instruction will provide a two-item menu that includes an option to print darker labels:

sudo /usr/lib/lightscribe/elcu.sh[/SIZE][/FONT]

[FONT=Arial][SIZE=2]then to run Lacie labeler as root:

sudo 4L-gui
  
you can also run the Simple Labeler installed by Lightscribe but it is  very BORING - however it is a fast way to go because of the circular printing - you get to it in /OPT or add this shortcut to a launcher:

/opt/lightscribeApplications/SimpleLabeler/SimpleLabeler

Some ideas for getting started with the Lacie can be found by using this Gimp template here:
[http://www.vitalbodies.net/site/tech-web/tech/111-open-source-cddvd-cover-for-open-source-projects.html](http://www.vitalbodies.net/site/tech-web/tech/111-open-source-cddvd-cover-for-open-source-projects.html)
[/SIZE][/FONT] 

:popcorn:

---

### Post by jollins69 on 2011-01-15
Thank you for sharing :)

---

