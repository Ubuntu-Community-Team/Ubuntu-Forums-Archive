---
title: "default programs"
date: 2009-08-11
forum: General Help
---

### Post by blur xc on 2009-08-11
Hey- how do you set the default program to open a specific kind of file?


I have two problems-
#1- I installed real player after I installed VLC player, now real player launches when 
I stick in a dvd, but it can't play them.  That's annoying...  I have to close it, right click, open w/ vlc player.

#2- chm files...  I installed Wine after I installed chmsee, so no it launches a buggy wine app to view chm files, same deal- right click- etc.  

Thanks,
BM

---

### Post by wojox on 2009-08-11
When you right click go to properties and Opens with. That should set it.

---

### Post by LowSky on 2009-08-11
In Nautilus, right click on the file and choose Properties from the menu that appears. The Properties dialog opens.
  
Click on the Open With tab. A list of applications appears.

Select the default application you want for the file type. If the application is not on the list, use the Add button to add the application to the list.


[http://lmgtfy.com/?q=set+default+program+ubuntu](http://lmgtfy.com/?q=set+default+program+ubuntu)

---

### Post by Wistful on 2009-08-11
> **blur xc said:**
> 

#2- chm files...  I installed Wine after I installed chmsee, so no it launches a buggy wine app to view chm files, same deal- right click- etc.  


You don't need an emulator to view .chm files in Ubuntu, there are applications created for this purpose.

Like Gnochm for Gnome and KchmViewer for KDE. 

A simple **sudo apt-get install Gnochm** or **sudo apt-get install KchmViewer** will resolve your issue.

---

### Post by blur xc on 2009-08-11
I knew it was something easy...  What about dvd's though?  Do I right click on the dvd icon after it's mounted and do the same thing?

BM

---

### Post by blur xc on 2009-08-11
> **Wistful said:**
> You don't need an emulator to view .chm files in Ubuntu, there are applications created for this purpose.

Like Gnochm for Gnome and KchmViewer for KDE. 

A simple **sudo apt-get install Gnochm** or **sudo apt-get install KchmViewer** will resolve your issue.

):P

yeah- that's what I'm getting at.  I have chmsee installed which works great, but after installing wine, it launches instead.

BM

---

### Post by michy99 on 2009-08-11
I copied this from [this great thread]("http://ubuntuforums.org/showthread.php?t=766683").

DEFAULT DVD PLAYER


UBUNTU FAMILY 8.04+ USERS ONLY


To change the default DVD player to VLC (not Kubuntu, possible issues with Xubuntu), copy and paste this command into the terminal:```

gksudo gedit /etc/gnome/defaults.list
```Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to "Places > Computer > Edit > Preferences > Media > DVD Video", and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD. If playback doesn't work properly, navigate to "Video > Deinterlace" within VLC and select mode "Blend". If that still doesn't solve your issue, or you just want more features enabled upon launch (such as fullscreen upon launch), follow the intructions in the next paragraph.

Right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right. Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties", and change the launch command from "wxvlc %F" to:

vlc --volume 512 %m

or to have DVD playback automatically launch in fullscreen:

vlc --volume 512 --fullscreen %m

Close the VLC properties dialog and exit the menu editor.

Note: Remember to enable deinterlacing in "VLC > Video > Deinterlace" if you see any artifacts during playback, or if playback doesn't work correctly (the same is true with some AVI files also). To exit and enter fullscreen in VLC, just press the "f" key.

---

### Post by mcduck on 2009-08-11
> **blur xc said:**
> I knew it was something easy...  What about dvd's though?  Do I right click on the dvd icon after it's mounted and do the same thing?

BM

Open a file manager (Nautilus), go to Edit/Preferences, and in the Media-tab you'll be able to select default player for DVD video.

(These settings used to appear in System/Preferences, but for some reason I can't really understand they were moved into Nautilus preferences instead..)

---

### Post by blur xc on 2009-08-11
> **michy99 said:**
> I copied this from [this great thread]("http://ubuntuforums.org/showthread.php?t=766683").

DEFAULT DVD PLAYER


UBUNTU FAMILY 8.04+ USERS ONLY


To change the default DVD player to VLC (not Kubuntu, possible issues with Xubuntu), copy and paste this command into the terminal:```

gksudo gedit /etc/gnome/defaults.list
```Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to "Places > Computer > Edit > Preferences > Media > DVD Video", and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD. If playback doesn't work properly, navigate to "Video > Deinterlace" within VLC and select mode "Blend". If that still doesn't solve your issue, or you just want more features enabled upon launch (such as fullscreen upon launch), follow the intructions in the next paragraph.

Right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right. Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties", and change the launch command from "wxvlc %F" to:

vlc --volume 512 %m

or to have DVD playback automatically launch in fullscreen:

vlc --volume 512 --fullscreen %m

Close the VLC properties dialog and exit the menu editor.

Note: Remember to enable deinterlacing in "VLC > Video > Deinterlace" if you see any artifacts during playback, or if playback doesn't work correctly (the same is true with some AVI files also). To exit and enter fullscreen in VLC, just press the "f" key.

Awesome- that's what I was looking for, but couldn't find it...

Thanks!
BM

---

