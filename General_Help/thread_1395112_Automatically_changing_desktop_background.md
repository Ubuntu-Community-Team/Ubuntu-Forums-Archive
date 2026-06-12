---
title: "Automatically changing desktop background"
date: 2010-01-31
forum: General Help
---

### Post by chrismiceli on 2010-01-31
In Karmic I noticed on the desktop background dialog menu there is a desktop background that has a play button beneath it.  If you choose it, your background will change automatically to the ones in the list.  There is a screenshot of it highlighted.  I can't find a mention of this anywhere and I can't create find a way to create my own.  Also, I don't know how to add photos to the list or remove them.  Can someone point to where some of this information is. Thanks

---

### Post by gabreal2k on 2010-01-31
Hi, welcome to the forums. The picture you supplied shows the cosmos folder, located at /usr/share/backgrounds/

To create your own custom playing setup you could: 

1) Replace the existing images with your own as long as they are named EXACTLY the same as the originals and placed in the same folder. 

2) The other way to do this is to open /usr/share/backgrounds/background-1.xml in the terminal as root and edit the filenames/filepaths.

I'm not sure if redirecting the xml file to a different folder would work or not but it probably will.

Just in case you don't know; to copy some pictures to /usr/share/backgrounds/ do this in a terminal:
$ sudo -i 
enter your user password (you will now be in terminal as root)

$ cp /path/to/my/pictures/*.whatever (jpg,png,tga etc)HIT SPACEBAR TWICE/usr/share/backgrounds/ENTER

or to replace the standard images altogether...

$ rm /usr/share/backgrounds/cosmos/*.jpgENTER, THEN

$cp /path/to/my/pictures/*.whateverHIT SPACEBAR TWICE/usr/share/backgrounds/cosmos/ENTER

Hope this helps. Let us know if you run into problems.

---

### Post by Thepookster on 2010-01-31
I had this same question. 

I thought of just making your own folder within the same directory but it wont allow the creation of folders. I really dont feel like trying to edit the exiting cosmos theme.

This is such a simple feature that I'm surprised it has not been implemented.

Anyone else know of a way to create custom alternating backgrounds?  There has to be a simple way to do this.

---

### Post by gabreal2k on 2010-01-31
to create a folder in /usr/share/backgrounds/
1 open terminal and type sudo -i

2 enter your user password then ENTER

3 mkdir /usr/share/backgrounds/MY NEW FOLDERS NAME then ENTER

4 cp /path/to/my/folder/with/custom/pics/*.whatever (jpg,png, etc)HIT SPACEBAR TWICE /usr/share/backgrounds/MY NEW FOLDERS NAME/ then ENTER
******************************************
YOU MIGHT HAVE TO SPELL OUT THE PICS NAME LONGHAND. ex:
cp /home/user/Pictures/summer vacation/me and suzy.jpg  /usr/share/backgrounds/MY NEW FOLDERS NAME/
*******************************************
5 gedit /usr/share/backgrounds/cosmos/backgrounds-1.xml

6 change the path FROM /usr/share/backgrounds/cosmos/ to /usr/share/backgrounds/YOUR NEW FOLDERS NAME/

7 change the names of the pictures to the names of your pictures in YOUR NEW FOLDER hit SAVE then close terminal. Then change your background to the cosmos one and it should "play" your pictures.

---

### Post by Thepookster on 2010-01-31
that's way to much hacking for my taste for something as simple as auto changing desktop backgrounds, heck even windows does this with little more than a few clicks.  besides, I like the cosmos theme too, I dont want to get rid of that.

Of all the fancy intuitive features we have with Gnome/Ubuntu you would think this was a given.

oh well, ill just have to stick to changing them manually for now, thanks anyway guys.

---

### Post by chrismiceli on 2010-01-31
Hey thanks for the information.  I found an xml for cosmos but it isn't too obvious.  I thought it'd just have all the pictures to rotate through, but it has these timing values associated with it.  I wonder why it is coded like such.  Changing the filenames does put it in the loop.  I tried creating my own folder and own xml file, but the background browser doesn't see it.  I am wondering who started this and if they are planning on adding a gui interface to create these.
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
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/cloud.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/cloud.jpg</from>
    <to>/usr/share/backgrounds/cosmos/comet.jpg</to>
  </transition>
...

```

---

### Post by gabreal2k on 2010-01-31
I ***THINK*** the 1795.0 is seconds, basically every 30minutes it will change. You could try changing that to 3.0 and see if it works. I'm pretty much a newb but I have some Linux experience. If your willing to wait im gonna try it myself in then next half hour or so.

---

### Post by gabreal2k on 2010-01-31
Ok, here is what I found out. The built in wallpaper switcher in karmic is DESIGNED to basically run whatever wallpapers you want, by editing the background-1.xml file. 

The built in wallpaper switcher in karmic has a bug that won't allow it to actually switch anything....but there is a workaround....but I couldnt get it to work/figure out how to do it. The link for the documentation workaround is:

 [https://bugzilla.gnome.org/show_bug.cgi?id=601753](https://bugzilla.gnome.org/show_bug.cgi?id=601753)

As with most things in Ubuntu you CAN go to your SYSTEM>SYNAPTIC PACKAGE MANAGER and type in drapes....Drapes is a free wallpaper switcher that offers a degree of customizability. 

My apologies for my earlier posts, although they are technically correct they have been made MOOT by virtue of the fact that this "built in functionality" is apperntly  BROKEN OUT OF THE BOX. 

In the mean time if anybody figures out how to FIX the built in switcher, please post the necessary steps, so that more of us can enjoy this capability.

---

### Post by gerymate on 2010-08-18
Probably there is a GUI tool that creates such XML files for automatic wallpaper switching...

---

### Post by ectospasm on 2010-11-03
As far as I can tell in Maverick, there's still no way to achieve this in the GNOME GUI.  Drapes is broken for me, and hasn't been updated in over two years (see [http://drapes.mindtouchsoftware.com/](http://drapes.mindtouchsoftware.com/)), but YMMV.

What I had to do is this:

[LIST=1]
[*]Create a directory in /usr/share/backgrounds to hold background-1.xml:
```
sudo mkdir /usr/share/backgrounds/<directory>
```
[*]Copy background-1.xml to new directory:
```
sudo cp /usr/share/backgrounds/cosmos/background-1.xml /usr/share/backgrounds/<directory>/
```
[*]Edit /usr/share/backgrounds/<directory>/background-1.xml, replacing each path to the cosmos files to your own images.  Add or remove tags in the XML as necessary.
NOTE:  the images listed in this file do not need to be stored in /usr/share/backgrounds/<directory>, just be sure to include full paths in background-1.xml.
[/LIST]

---

### Post by williamts99 on 2010-11-27
Try Cortina, [https://launchpad.net/cortina](https://launchpad.net/cortina)

---

### Post by m.alaa8 on 2011-06-22
that is what you need
[gnome-wallpaper-slideshow]("http://www.brighthub.com/link/link.aspx?u=http%3a%2f%2fcode.google.com%2fp%2fgnome-wallpaper-slideshow%2f&p=85656&isHubfolio=1")

---

### Post by e79 on 2011-06-22
And also '**DesktopNova**' downloadable from the Software Center, works like a charm for me [https://launchpad.net/ubuntu/+source/desktopnova](https://launchpad.net/ubuntu/+source/desktopnova).

Simply open the '**Ubuntu Software Center**' and research for '**DesktopNova**', very simple to install and configure.

Hope this helps

---

