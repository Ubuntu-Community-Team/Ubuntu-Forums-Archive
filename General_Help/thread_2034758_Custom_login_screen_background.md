---
title: "Custom login screen background?"
date: 2012-07-28
forum: General Help
---

### Post by Stonecold1995 on 2012-07-28
I have my login screen set to display my wallpapers (in random order, changing every 30 minutes just like my wallpaper), but recently when I categorized them and put them in their own folders it won't work.  It used to be that I had my wallpapers like this:

[B]Wallpapers
&#9500;&#9472;&#9472; img1.png
&#9500;&#9472;&#9472; img2.png
&#9492;&#9472;&#9472; img3.png[/B]

But I organized them so they now look like this:

[B]Wallpapers
&#9500;&#9472;&#9472; catagory1
&#9474;[COLOR="White"]---[/COLOR]&#9500;&#9472;&#9472; img1.png
&#9474;[COLOR="White"]---[/COLOR]&#9500;&#9472;&#9472; img2.png
&#9474;[COLOR="White"]---[/COLOR]&#9492;&#9472;&#9472; img3.png
&#9500;&#9472;&#9472; catagory2
&#9474;[COLOR="White"]---[/COLOR]&#9500;&#9472;&#9472; img1.png
&#9474;[COLOR="White"]---[/COLOR]&#9500;&#9472;&#9472; img2.png
&#9474;[COLOR="White"]---[/COLOR]&#9492;&#9472;&#9472; img3.png
&#9492;&#9472;&#9472; catagory3
[COLOR="White"]----[/COLOR]&#9500;&#9472;&#9472; img1.png
[COLOR="White"]----[/COLOR]&#9500;&#9472;&#9472; img2.png
[COLOR="White"]----[/COLOR]&#9492;&#9472;&#9472; img3.png[/B]

Unfortunately, the login screen "manager" is unable to move recursively to find wallpapers like the desktop wallpaper "manager" can.  Because of this, I'm stuck with a blue login screen (which I assume is the default if no images are found).  So my question is, how can I get my desktop background and my login screen background linked so they display the same set of images?  I can't move all my wallpapers into one big folder and point the login screen manger to *it* because I have too many wallpapers (more than a thousand).  Any ideas?

([Here]("http://www.pictureshack.us/images/35977_login_screen.png")'s a screenshot of the problem).

---

### Post by Zorael on 2012-07-29
That looks like [this bug](https://bugs.kde.org/show_bug.cgi?id=235487), yeah.

I'm not sure KDM is really maintained anymore either; effort seems to be aimed at developing [a KDE greeter for **lightdm**](http://agateau.com/2012/04/21/lightdm-kde-0-1-0-released/). And from what I can see it doesn't support rotating wallpapers yet. :/

(lightdm separates behind-the-scenes logic from presentation, which means that we would share code with other DEs instead of having to reimplement the same thing over and over.)

So the only solution/workaround/ugly hack I can think of is to place everything in one directory, yes. But instead of messing up your entire well-categorised Pictures, just create symlinks of all those pictures somewhere else. Then point KDM to that directory.

Like so;
```
$ sudo mkdir -p **/usr/local/share/greeter-wallpapers**  *# or wherever really, as long as the directory is accessible at kdm start*
$ cd **/usr/local/share/greeter-wallpapers**
$ sudo find **/home/alex/Pictures** -type f -iregex '*.*\(jpe?g\|png\|bmp\|gif\|tiff?\)*' -exec printf '.' \; -exec ln -s '{}' . \;
```
Might take a while to finish. You would also have to redo it every now and then when you've added more wallpapers. If you ever delete any of the original pictures, just delete all symlinks before running the command again, so as not to get dead links.

It's not a *good* solution, but it is one that will serve until the kdm bug is fixed (which seems unlikely), and/or the same functionality is implemented in lightdm-kde-greeter after having been [requested as a wishlist feature](https://bugs.kde.org/buglist.cgi?quicksearch=product%3Alightdm).

---

### Post by Stonecold1995 on 2012-07-29
I've found another temporary solution.  I can select all the directories at once ([screenshot]("http://www.pictureshack.us/images/52626_login_screen1.png")).  That way when if I add new wallpapers it'll automatically add them, although if I create a new category I'll have to remember to select all of the directories again.  Do you know where the configuration file for the directories used in the login manager is stored?  If I know that I could create a script that could run at startup and could add all directories under ~/Pictures/Wallpapers to the configuration file and remove any ones that were deleted.

---

### Post by Zorael on 2012-07-30
**/etc/kde4/kdm/backgroundrc**, I believe. Other non-background-related kdm settings are stored in **kdmrc** in the same directory.

---

### Post by Stonecold1995 on 2012-08-08
So I ended up using this script and putting it in "~/.kde/share/shutdown", then pointing the source of wallpapers to "~/.kde/share/wallpapers".  It seems to be working now.  Thanks for all the help!

```
#!/bin/bash

location="/home/alex/Pictures/Wallpapers" # location to (recursively) get wallpapers from

cd /home/alex/.kde/share
rm -f wallpapers-bak
mv -f wallpapers wallpapers-bak
mkdir wallpapers
find $location -type f -iregex '.*\(jpe?g\|png\|bmp\|gif\|tiff?\)' -exec ln -s '{}' wallpapers \;
exit 0
```

EDIT: Didn't work.  For some reason the wallpaper manager won't accept symbolic links.

---

### Post by Stonecold1995 on 2012-08-14
The last solution with the script didn't work.  It turns out the login screen manager can't use symlinks for some reason (which is really weird, IMO).  Anyways, I think found the cause of the problem.  When I save the list of images to use as the login background, it needs to be saved in /etc/kde4/kdm/backgroundrc with the full path, not just the directory name.  This is what the file backgroundrc looks like when it's working:

```
[Desktop0]
BackgroundMode=Flat
BlendBalance=100
BlendMode=NoBlending
ChangeInterval=1
Color1=0,0,200
Color2=192,192,192
CurrentWallpaperName=
LastChange=1344471594
MinOptimizationDepth=1
MultiWallpaperMode=Random
Pattern=fish
Program=
ReverseBlending=false
UseSHM=false
Wallpaper=/home/alex/Pictures/Wallpapers/folder1/image1.jpg
WallpaperList=/home/alex/Pictures/Wallpapers/folder1,/home/alex/Pictures/Wallpaperes/folder2,/home/alex/Pictures/Wallpapers/folder3
WallpaperMode=Scaled

```

And this is what it looks like when it isn't working:
```
[Desktop0]
BackgroundMode=Flat
BlendBalance=100
BlendMode=NoBlending
ChangeInterval=1
Color1=0,0,200
Color2=192,192,192
CurrentWallpaperName=
LastChange=1344471594
MinOptimizationDepth=1
MultiWallpaperMode=Random
Pattern=fish
Program=
ReverseBlending=false
UseSHM=false
Wallpaper=/home/alex/Pictures/Wallpapers/folder1/image1.jpg
WallpaperList=folder1,folder2,folder3
WallpaperMode=Scaled

```

So the problem is that it doesn't save the full path like it should.  When I am about to save the list, it looks like [this]("http://www.pictureshack.us/images/5708_screenshot1.png").  However, when I come back to it later it looks like [this]("http://www.pictureshack.us/images/16043_screenshot2.png"), which makes it look like it didn't save the full path, even though it displayed that.  So if this is the issue, how do i get it to save the full path in backgroundrc without manually changing them all?

---

