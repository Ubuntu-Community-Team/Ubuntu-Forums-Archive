---
title: "Adding Program to Launcher in Ubuntu 10.10"
date: 2010-10-15
forum: General Help
---

### Post by sventhebrit on 2010-10-15
Hi,

I have just completed a clean install of Ubuntu 10.10 on my Acer Aspire Netbook.  The first program I installed was WINE and then I installed "Spotify for Windows".  All works well, but I need to start it by opening a terminal and typing - Wine "C:\Program Files\Spotify\Spotify.exe" which is a little cumbersome.

I want to add a shortcut to the launcher but I cannot find a way to do this.  I have found a "Main Menu" option in Applications, but the options and items in there don't seem to correspond to the launcher in any way.

Is there a way of adding something to the launcher or to get the main menu to display so I can customize it from the Main Menu utility.

Thanks
Steve

---

### Post by tea for one on 2010-10-15
Good Evening

After a bit of trial and error, it seems that, when a program is started, a program icon appears in the vertical (left side) quick launcher area.

Right click the new icon and select "Keep in launcher"

Kind regards

---

### Post by sventhebrit on 2010-10-15
Thanks for the response.  I have tried this and it does work with Terminal and others.  I am trying to do this with Spotify which is running under Wine, but I cannot get Spotify to stay in the launcher -- just Wine stays there and it errors when I click on it.
 
The interface seems a backword step ... it is less cluttered, but it appears to have lost some basic functionality which is required.  On the previous version, there was a favourites and it was easy to add to the favourites by right clicking on the icon.
 
The Main Menu configuration is still there and Spotify is part of the configuration.  Is there any way of switching it back on so it is displayed?
 
Thanks
Steve

---

### Post by tea for one on 2010-10-16
Good morning

I do not use Wine so I regret that I am unable to help with this difficulty.

Hopefully somebody else may be able to offer advice.

On a general note, I agree the the new interface on the Ubuntu 10.10 Netbook OS is challenging. I intend to persevere but perhaps it just needs day to day use to become comfortable with it.

By the way, I expect that you can still boot into the usual Gnome interface (desktop edition), where you may be able to park your Wine and Spotify quick launchers.

Kind regards

---

### Post by baskvald on 2010-10-16
Hi,
I noticed that when running terminal server in fullscreen mode, the program launcher invisibly stays on top and makes it impossible to use anything to the left on the remote desktop fullscreen.

It would be really great if someone clever knew of a way to customize the program launcher. Reordering the items would be nice too.

---

### Post by AndresM on 2010-10-24
HI, 

Tried adding the aplication Gramps to the launcher in ubuntu netbook remix 10.10. There is no menu that will let me keep it there once the program is running. If I close the program it goes away. 

Reckon it's a bug?

---

### Post by jensaug on 2010-10-24
Finally found a workaround for the "how-to-restart-wine-apps-in-Unity" problem - I had the same prob with Spotify

* When installing spotify, make sure Wine adds a shortcut on the Desktop.

* Launch spotify using that shortcut. Even this seems hard to do in Unity...
** Either directly launch nautilus (I do that command line since I can't figure out how to do it using Unity). Navigate to Desktop and click on Spotify.
** Or browse to any folder using the Unity interface (Files and Folders, choose eg. Video). Then click on the folder symbol up in the right corner, nautilus will then be launched. Navigate to Desktop and click on Spotify.
** Don't attempt to execute the spotify shortcut command line, that'll only give you the same darn wine icon in your Launcher.

* Now you'll finally have a Spotify symbol in the Launcher.... right click on it and add

I assume the same can be applied for any wine app.

Unity will probably be great one day, but to me today it feels like beta stuff.

br,
Jens

---

### Post by jgcamp99 on 2010-10-25
> **AndresM said:**
> HI, 

Tried adding the aplication Gramps to the launcher in ubuntu netbook remix 10.10. There is no menu that will let me keep it there once the program is running. If I close the program it goes away. 

Reckon it's a bug?

When the icon appears on the launcher to your left after opening the program, simply right click and select "keep in launcher". Right click again to "remove from launcher"

And after doing this for a few test icons, it appears to put them in alphabetical order.

---

### Post by smithintaiwan on 2010-10-26
Hi,

It seems that you can reorder the items in the launcher side bar by drag-and-drop. You have to click on the icon and initially pull it to the right before dragging it up or down.
Hope that helps.

---

### Post by adonix on 2010-11-03
Hi, with Ubuntu 10.04 we were able to add to the main menu/favorite/launcher the different varieties of web apps that we could create with Prism . However, currently if you launch any prism-app from the shortcut that gets created at the desktop folder, the launcher will display the boring prism icon (instead of the user selected icon) then doing a right click on it and selecting to keep it in the launcher will keep prism and not the prism web app.

Is there a way to add the actual prism-created-web-apps (which are basically shortcuts of different websites but convenient since they run independently) to the launcher?

And last, I like running grooveshark-desktop, which I think runs out of adobe air. The launcher does display the correct icon for groovershark, but right clicking on this icon does not display an option to keep it in the launcher. Any help with this also? Thank you in advance.

---

### Post by kerry_s on 2010-11-03
for custom launchers i been using awn(avant-window-navigator) just stick it where you like.

currently i only got grun in mine. :)

---

### Post by Morganvd on 2010-11-05
> **kerry_s said:**
> for custom launchers i been using awn(avant-window-navigator) just stick it where you like.

currently i only got grun in mine. :)


This is great but I think its really silly that the we need to go through the trouble of doing this. It just feels like no one has thought this through when they made 10.10 netbook edition

---

### Post by vietsb on 2010-11-07
Appears the issue with adding Wine Apps to Ubuntu 10.10 Netbook Unity Launcher was and is being actively discussed at the core level.  Not sure if they'll release a patch or wait until 11.04 Natty, assuming the details can be sorted out into a workable solution.

[https://bugs.launchpad.net/unity/+bug/635223]("https://bugs.launchpad.net/unity/+bug/635223")

BTW:
I was trying to get the latest Window RSA SecurID Soft Token to be easily available via Unity Launcher or otherwise, so  [Adam Guthrie's work-around Post #23]("https://bugs.launchpad.net/unity/+bug/635223/comments/23") at least got me to see the Icon in Unity Applications under [B]All Applications[/B[.  I tried changing the file addition to *Category=Accessories* to see if I could group it easier, but it didn't work.  Also, unlike the previous post regarding getting a desktop shortcut to be installed via Wine and launching from there and pinning to Unity Launcher, I was only able to get the Wine icon on Launcher and it doesn't work to run a specific Windows App.  Work-around is still good for now though, but if anyone has had better luck getting their particular Wine app to show and be added to Launcher, please share since I'm just learning. :)

---

### Post by Kalyan-sg on 2011-02-10
I am new to Ubuntu.
I want to add an html file in the Launcher, which resides on CD. Can this be done?
Thanks in advance.
Kalyan

---

### Post by justerson on 2011-03-31
I found a solution to this issue here: [http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity](http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity). I tried it for an application that did not give me the "keep in launcher" option in the right-click menu and it works great. A bit tedious and I wouldn't want to do it for every app, but for one or two it's not all that hard. The instructions are for 11.04 Unity but I am running UNR 10.10 on an HP Mini 110 and these instructions worked for me. 
[[COLOR=Black][/COLOR]]("http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity")

---

### Post by Spyderkid on 2011-03-31
to wsit the menus right click on the menu and click edit menu, then go to wine, programs and click on spotify and then apply or ok and it should appear on your menu.

this applys with all things really

---

