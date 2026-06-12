---
title: "Nautilus&gt;Edit Preferences&gt;Media options issue"
date: 2011-01-12
forum: General Help
---

### Post by cscj01 on 2011-01-12
If I insert an Audio CD into my CD/DVD Writer, I cannot choose an application.  So I launched Nautilus and chose Edit>Preferences>Media.  Here's the problem.  All options under Media Handling are grayed out and show "No application found" except for Software.  Why can I not select any applications for CD Audio, DVD Video, Music Player, or Photos?

I use Ubuntu 10.10 x64.

---

### Post by mc4man on 2011-01-12
The only 'proper' reason they'd be greyed out would be if, in fact, there were no applications installed that registered for each particular type.

In a default install - 
for Cd Audio - Rhythmbox, Brasero
DVD Video - Movie Player (Totem), Brasero
Music Player - Rhythmbox
Photos - Shotwell

Did you remove all of the above and install apps that fail to register?

---

### Post by cscj01 on 2011-01-12
No, all the original apps are there.  I have installed quite a bit of the Ubuntu Studio apps, but I have not changed any settings.

---

### Post by mc4man on 2011-01-13
You could try a couple of things.
One would be to remove and then install the apps I mentioned relative to each, that may 'open' up the options (and or any app you think should be available.
When re-installed then hopefully the menus will get active


The other would be to open this file and look for these lines (cd, dvd, music player, photos
```
gedit ~/.local/share/applications/mimeapps.list
```
x-content/audio-cdda=
x-content/video-dvd=
x-content/audio-player=
x-content/image-dcf=  

If not there then add some or all  with the above apps (if installed)  - ex.

x-content/audio-cdda=rhythmbox.desktop;
x-content/video-dvd=totem.desktop;
x-content/audio-player=rhythmbox.desktop;
x-content/image-dcf=shotwell.desktop; 

Then do a restart and hopefully the menu's will open up

(if still not then add any existing  .desktop even if not suited and restart
Ex.
x-content/audio-cdda=rhythmbox.desktop;gedit.desktop;

---

### Post by cscj01 on 2011-01-13
> **mc4man said:**
> You could try a couple of things.
One would be to remove and then install the apps I mentioned relative to each, that may 'open' up the options (and or any app you think should be available.
When re-installed then hopefully the menus will get active


The other would be to open this file and look for these lines (cd, dvd, music player, photos
```
gedit ~/.local/share/applications/mimeapps.list
```
x-content/audio-cdda=
x-content/video-dvd=
x-content/audio-player=
x-content/image-dcf=  

If not there then add some or all  with the above apps (if installed)  - ex.

x-content/audio-cdda=rhythmbox.desktop;
x-content/video-dvd=totem.desktop;
x-content/audio-player=rhythmbox.desktop;
x-content/image-dcf=shotwell.desktop; 

Then do a restart and hopefully the menu's will open up

(if still not then add any existing  .desktop even if not suited and restart
Ex.
x-content/audio-cdda=rhythmbox.desktop;gedit.desktop;

Okay, I checked the mimeapps.list file and all the x-content lines are there.

```
x-content/video-dvd=vlc.desktop;totem.desktop;brasero-copy-medium.desktop;mplayer.desktop;
x-content/audio-cdda=rhythmbox.desktop;userapp-quodlibet-GO5L4U.desktop;sound-juicer.desktop;brasero-copy-medium.desktop;vlc.desktop;
x-content/audio-player=userapp-quodlibet-GO5L4U.desktop;rhythmbox.desktop;vlc.desktop;
x-content/image-dcf=f-spot-import.desktop;
x-content/audio-dvd=vlc.desktop;rhythmbox.desktop;

```
  Also there are desktop files for all the apps listed in the mimeapps.list file.

However, I have several desktop files for many of the apps listed on the x-content lines.  For example, I have the following desktop files listed for Rhythmbox: rhythmbox.desktop, Rhythmbox.desktop, Rhythmbox-1.desktop, and rhythmbox-device.desktop.  I have moved some of my menu locations to other locations, and I understand that a new desktop file is created by alacarte.  So I suppose that is why I have the multiple desktop files for the given applications.

If I try to execute these desktop files, I get the following message:
> Untrusted application launcher  Perhaps this is correct because in the Properties of these desktop files, the executable box is not checked, but I wonder if it has anything to do with not being able to assign applications to the Nautilus actions.  Obviously, I am at a loss as to why nothing shows when I try to set the actions in Nautilus or when I insert an audio CD for example.

---

### Post by mc4man on 2011-01-13
> but I wonder if it has anything to do with not being able to assign applications to the Nautilus actions
Most likely not, usually marking those .desktops as 'trusted' (executable) will just allow them to display with an icon and 'display' name

> I have moved some of my menu locations to other locations, 

Not sure what you mean there, have you moved them from their orig. install location, typically /usr/share/applications

> and I understand that a new desktop file is created by alacarte
Those are always userapp .desktops which can be available by their 'display' name which by default is what comes after userapp- in lowercase

Have you tried removing an app completely and re-installing (inc. any 'moved' ?? .desktop 
For instance vlc which should show up for both dvd and audio cd
(won't hurt to also remove or edit out all the .desktops in  those 2 lines in mimeapps.list

Edit:
you could also try, for the moment, creating another use. Logout and then login to the new user and ck. File Management . media there.
If available then it's something you've borked locally, if not then system -wide.
(users can set their own defaults

---

### Post by cscj01 on 2011-01-13
> **mc4man said:**
> Most likely not, usually marking those .desktops as 'trusted' (executable) will just allow them to display with an icon and 'display' name

 

Not sure what you mean there, have you moved them from their orig. install location, typically /usr/share/applications


Those are always userapp .desktops which can be available by their 'display' name which by default is what comes after userapp- in lowercase

Have you tried removing an app completely and re-installing (inc. any 'moved' ?? .desktop 
For instance vlc which should show up for both dvd and audio cd
(won't hurt to also remove or edit out all the .desktops in  those 2 lines in mimeapps.list

Edit:
you could also try, for the moment, creating another use. Logout and then login to the new user and ck. File Management . media there.
If available then it's something you've borked locally, if not then system -wide.
(users can set their own defaults

I used the System>Preferences>Main Menu to move where the application appeared in the Applications menu.  For example, I created a new menu named Photography and moved Gimp, F-Spot, etc. to that menu from the Graphics menu.  That is what I meant by "moving" applications.  I should have been more clear on that point.  I have not moved any app from it's install location.

I have not tried removing and re-installing any apps as yet.  I was hoping there might be an easier way to correct this.  If that is what I must do, so be it.

I do have a question about your statement concerning removing .desktops in the lines in mimeapps.list.  Would I just edit (remove) everything after the =?  I presume I would do this prior to re-installing the app?  Also, should I also remove the app .desktop files from ~/.local/share/applications after removing an app and before I re-install it?

As to your edit comment: could I just login as root to check that?  If I login as a different user and the Nautilus File>Preferences>Media allows me to select actions, can I copy that mimeapps.list file to my user directory ~/.local/share/applications and fix the problem?

Thanks for your help to this point.

---

### Post by mc4man on 2011-01-13
The ~/.local/share/applications/mimeapps.list doesn't exist by default,
you can freely remove any entry(s) from the = out or just delete the  whole file itself
It's initially created the first time you set a default in File management or associate a mimetype thru the r. click context menu, whether from 'other application' or 'use a custom command' or fom the properties of any file type.

The only thing 'lost' if you delete the file is any associations you  previously created, whether directly to the default app.desktop or thru a custom command (a userapp.desktop
No big deal as you can simply 'reset' them thru the context menu and  if you get working the FM > Media > ..

> could I just login as root to check that? 
No I wouldn't do that. Root actually has it's own nautilus preferences that for the most part should be left alone.

An example of the one useful root pref. that I do edit is adding a delete command
To see what I mean
Alt+F2 - gksu nautilus > edit > preferences > behavior
(the only other 'root' preference I'd touch is the 'show hidden files', would not change much of anything else, certainly nothing in Media
Edit: though you could ck. and see if the Media options are open, though again may be more useful to ck. w/ a new user.

Vlc would be an easy app to remove and re-install, maybe if trying also remove the 2 lines in mimeapps.list (cd and dvd ) or just delete or rename mimeapps.list (mimeapps.list.bak

---

### Post by cscj01 on 2011-01-13
Well, all I've done so far is add a new user and logged in as that user.  All the options are there in Nautilus for the various types of media, none are grayed out, and I can select any that show or any other app I want.  So I guess it is just hosed for me.  I am still wondering what I did that could have caused this.  I am supicious of the Menu restructuring I did because items got all moved around from where I had them, and I had to drag them back to the menus one at a time.  I have a thread in this forum asking about alacarte.  It is here: [http://ubuntuforums.org/showthread.php?t=1650631]("http://ubuntuforums.org/showthread.php?t=1650631")

---

### Post by mc4man on 2011-01-15
you could try opening ~/.local/share and deleting or renaming the applications folder. Then do a restart and see

---

### Post by cscj01 on 2011-01-15
> **mc4man said:**
> you could try opening ~/.local/share and deleting or renaming the applications folder. Then do a restart and see

Okay, here's what I did.
[LIST=1]
[*]I renamed the Applications folder as you suggested.
[*]I restarted the system.  When I checked the ~/.local/share directory, I had no Applications folder.
[*]I opened Nautilus>Edit>Preferences>Media and, lo and behold, all the options were available.
[*]I chose the appropriate applications for each (CD Audio, DVD Video, Music Player, Photos, Software, and some of the other Media) and closed the Preferences dialog.
[*]I then checked ~/.local/share and an Applications folder had been created with a new mimeapps.list file that only contained the x-content lines, and they were all correct.
[*]I renamed the mimeapps.list file in the old Applications folder.
[*]I copied the new mimeapps.list file to the old Applications folder.
[*]I renamed the the new Applications folder and renamed the old Applications folder back to Applications.
[*]I restarted the system.
[*]I checked the Applications menu and my old menus and items where all present.
[*]I opened Nautilus>Edit>Preferences>Media and every option was as I had set it in step 4 above except Music Player which was grayed out with the message "No applications found".
[*]I opened the mimeapps.list file and all the x-content lines were there and were correct.
[/LIST]
So I have all of my options back except Music Player.  The odd thing is, if I choose "Open with other Application" in any of the other options such as CD Audio, my players all show as available to choose.  Rhythmbox, Exaile, Quod Libet, VLC, etc. are all there.

So where is the system indicating that there are no apps for Music Player?

---

### Post by mc4man on 2011-01-15
I'm not sure about the music player deal - the default on an install would be rhythmbox I believe.
What had you set it to Before copying back.

(there would be no real need to restore back the 'old' applications folder, you could simplt re-create any userapp.desktops if needed from the r. click context menu

---

### Post by mc4man on 2011-01-15
I'm not sure about the music player deal - the default on an install would be rhythmbox I believe.
What had you set it to Before copying back.

(there would be no real need to restore back the 'old' applications folder, you could simplt re-create any userapp.desktops if needed from the r. click context menu

(this may end up as a d. post

---

### Post by cscj01 on 2011-01-15
> **mc4man said:**
> I'm not sure about the music player deal - the default on an install would be rhythmbox I believe.
What had you set it to Before copying back.

(there would be no real need to restore back the 'old' applications folder, you could simplt re-create any userapp.desktops if needed from the r. click context menu
I had it set to Rhythmbox.

By right click, do you mean on the Applications menu and then add?  This is the same as System>Preferences>Main Menu.

---

### Post by mc4man on 2011-01-15
> By right click, do you mean on the Applications menu 
No, I was actually thinking more of any file associations like a r. click on a flac - open with - other application - use a custom command (I saw you had some originally

For the FM > Media ,you can use the dropdown below the listed choices to add new ones or again proceed to 'use a custom command' from there.


Edit. in other words there is no reason to keep the old applications folder, - it for some reason you'd want to then try  opening  it up and delete any .desktop with rhythmbox in the name.

---

### Post by guyl6308 on 2013-03-09
> **cscj01 said:**
> Okay, here's what I did.
[LIST=1]
[*]I renamed the Applications folder as you suggested. 
[*]I restarted the system.  When I checked the ~/.local/share directory, I had no Applications folder. 
[*]I opened Nautilus>Edit>Preferences>Media and, lo and behold, all the options were available. 
[*]I chose the appropriate applications for each (CD Audio, DVD Video, Music Player, Photos, Software, and some of the other Media) and closed the Preferences dialog. 
[*]I then checked ~/.local/share and an Applications folder had been created with a new mimeapps.list file that only contained the x-content lines, and they were all correct. 
[*]I renamed the mimeapps.list file in the old Applications folder. 
[*]I copied the new mimeapps.list file to the old Applications folder. 
[*]I renamed the the new Applications folder and renamed the old Applications folder back to Applications. 
[*]I restarted the system. 
[*]I checked the Applications menu and my old menus and items where all present. 
[*]I opened Nautilus>Edit>Preferences>Media and every option was as I had set it in step 4 above except Music Player which was grayed out with the message "No applications found". 
[*]I opened the mimeapps.list file and all the x-content lines were there and were correct. 
[/LIST]
So I have all of my options back except Music Player.  The odd thing is, if I choose "Open with other Application" in any of the other options such as CD Audio, my players all show as available to choose.  Rhythmbox, Exaile, Quod Libet, VLC, etc. are all there.

So where is the system indicating that there are no apps for Music Player?

Thank you a lot for sharing your experience. I was plagued by the same problem after re-arranging my menu items with "alacarte" ... 

I removed all the recently added .desktop files from the ~/application folder and sure enough the problem went away. I could then add the one that had no possible effect on the problem (the applications that cannot possibly get started by inserting a CD/DVD/music player). Only eight remained "banned", all of them were not needed...

THANK YOU all for helping solve this issue. This is March 2013 and yes I am still using Ubuntu 10.04 and I love it.

---

### Post by oldos2er on 2013-03-10
Old thread closed.

---

