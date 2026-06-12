---
title: "Can't change mouse pointer theme"
date: 2010-06-12
forum: General Help
---

### Post by alem189 on 2010-06-12
Okay - I'm using 10.04, and my problem is that I can't change the default mouse pointer(the one that is visible when you're not doing anything special) to another theme using System > Preferences  > Appearance > Customize > Pointer. It seems to change the text cursor, but the default pointer is still from the default theme. I've read in some other people's posts on how to fix this, but they're either applying to older versions of Ubuntu, or they're not comprehensive, or they plain just don't work. Anyone have some simple instructions on how to fix this?

---

### Post by kerry_s on 2010-06-12
set the default to the same theme.
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

turn accessibility back off in preferences-> keyboard

changing the background will change gdm(login screen) background.

---

### Post by alem189 on 2010-06-12
Nope... Still got the black pointer & white text bar...:confused:

---

### Post by WorMzy on 2010-06-12
Did you restart after changing it? From my experience, changing the cursor doesn't take effect immediately (except within a Firefox window, for some reason that recognises the change immediately)

---

### Post by alem189 on 2010-06-12
Yes, I probably should have restarted first. When I did, the pointer had the white theme on the login screen, but the black theme as soon as I logged in. The pointer doesn't change when I hover over a Firefox window, either.

P.S. - After 'gksudo -u gdm dbus-launch gnome-appearance-propertiesNow', my mounted drives are snowflakes and my Computer icon is the Ubuntu logo:lolflag: How do you change that back?

---

### Post by kerry_s on 2010-06-12
forgot, make sure the things you select are system accessible, for example: mouse & icons should be in /usr/share/icons, themes should be in /usr/share/themes, backgrounds in /usr/share/backgrounds. the system does not have access to your home folder.

alem189, what did you change while you were in there?

---

### Post by alem189 on 2010-06-12
I checked, the whiteglass pointer is in /usr/share/icons/whiteglass. I think the problem with the changed icons is that the folder icons are set to login icons, I'll restart and let you know if that fixed it. Also, I've researched this problem more, and one person said that if they take a screenshot, the pointer icon changes to the one they want - this happens to me too. Strange, but not sure if that helps.

---

### Post by alem189 on 2010-06-12
Yep, the icons are back to normal.

---

### Post by alem189 on 2010-06-13
I still can;t change the pointer though. Anyone got any other ideas?

---

### Post by alem189 on 2010-06-17
*bump*

---

### Post by artemgab on 2010-06-19
same here *bump*
I moved my mouse cursor themes to /usr/share/icons. then I set the same theme for my user, for gdm but it didn't help. I have my pointer at the login screen now (wow! :) ) but not for my user. set the same theme even for root, but it didn't help. However I do have my cursor theme in some apps: mozilla, OO writer...

---

### Post by WorMzy on 2010-06-20
I've since found a way to force the icon to switch.

[LIST=1]
[*]Create the following directory: ~/.icons/default
[*]Create a text file inside it, called "index.theme"
[*]Open the text file and write the following:
```
[Icon Theme]
Name = <Any name you want>
Comment = <Any comment you want>
Example = <Any example you want>
Inherits = <Name of the cursor theme you want to use>
```
[*]Save the file and log out and log back in (or possibly restart gdm, if that doesn't work)
[/LIST]

---

### Post by artemgab on 2010-06-20
Thanks, WorMzy, your solution worked!
Moreover, it also solved the problem of my cursor theme not being used in SMPlayer.

---

### Post by abhot on 2010-06-20
sudo update-alternatives --config x-cursor-theme
select the theme you want to use then log out:guitar:

---

### Post by alem189 on 2010-06-20
Thanks abhot, your solution worked too! Finally, I don't have to look at that ugly black theme...

---

### Post by ranger29 on 2010-07-10
nice one abhot! that worked for me in Lucid as well! It was nothing particularly vital, just one of those things that you just want to work!

Cheers!

---

### Post by ian760105 on 2010-10-03
> **WorMzy said:**
> I've since found a way to force the icon to switch.

[LIST=1]
[*]Create the following directory: ~/.icons/default
[*]Create a text file inside it, called "index.theme"
[*]Open the text file and write the following:
```
[Icon Theme]
Name = <Any name you want>
Comment = <Any comment you want>
Example = <Any example you want>
Inherits = <Name of the cursor theme you want to use>
```
[*]Save the file and log out and log back in (or possibly restart gdm, if that doesn't work)
[/LIST]

I can't believe this work. How do you know to do this?!?! I have spend hours trying to get my new cursor theme work. 
Thanks for everything. If anyone can't get their new cursor theme to work, this is it. THIS WORKS, GUYS!!

---

### Post by Mi11z on 2010-10-08
> **abhot said:**
> sudo update-alternatives --config x-cursor-theme
select the theme you want to use then log out:guitar:

Thank you, i consider this the best solution and simplest, thank you! i was stuck somewhere between the KDE cursor and dmz-white cheers. :D

---

### Post by prylux on 2011-02-23
If compiz is the issue you can try this...

You can set the pointer settings in compiz by following the instructions here:

[URL="http://ubuntuforums.org/showthread.php?t=1693831"][I][U]Can't change pointer 10.10 / compiz wont let you...
[/U][/I][COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1693831[/COLOR][/URL]

---

### Post by AbangBoltok on 2011-09-09
another way to do this is like this:

1. Open Appearance application:
Type appearance on Unity, or go to System->Preferences->Appearance

2. Select Customize.., Pointer, and select your preferred pointer. and then close.

3. edit pointer default:
```
sudo gedit /usr/share/icons/default/index.theme
```or you can use any text editor you prefer. :)
the content of the code look like this:
```
[Icon Theme]
Inherits=yourcurrentpointertheme
```and change yourcurrrentpontertheme with the one that you have selected in the appearance application.
for example:
```
[Icon Theme]
Inherits=Bazinga
```Don't forget, it's case sensitive
save, and close.

Logout, and log back in. :)

---

### Post by Dyar on 2011-09-14
Thank you!! It works in 11.04 too. Thanks *AbangBoltok*!!!

---

### Post by drillerccg on 2011-09-28
This worked for me in Ubuntu Natty 11.04. 
I never had any use for eye-candy hence no need to change themes or
 cursor icons. That is until my 78 year-old mother-in-law complained
 that the cursor was too small. I tried to change the size on default
 cursor and it did in some windows but not on desktop or system
 windows. The search began and I came across this you tube video that
 solved my problem, the link at the end. Here is a step by step of what
 I did courtesy of AbhiramH on you tube:
 
 1-Go to [http://gnome-look.org/](http://gnome-look.org/) , click on X11 Mouse Themes in the left
 margin, and download a pointer theme you like. I needed a large cursor
 so I downloaded Large Mouse Cursor 1.0
  [http://gnome-look.org/content/show.php/Large+Mouse+Cursors?content=140787](http://gnome-look.org/content/show.php/Large+Mouse+Cursors?content=140787)
 
 2-go to download folder and extract to desktop, you now have a folder
 on desktop named as the downloaded theme
 
 ****MY extracted folder was named Large Mouse Cursor and I had to
 rename it Large-Mouse-Cursor (with dashes) to get this to work, it
 seems like spaces don't really work in this process. Themes without
 spaces worked without renaming.
 
 3-Fire up the terminal, type sudo nautilus, enter password
 4- once browsing as root in the file browser, copy the folder on the
 desktop and paste to usr/share/icons folder
 5-close nautilus and terminal
 6- Fire terminal again and type sudo gedit
 /usr/share/icons/default/ index.theme
7-enter password
8- when the file opens, you will see Inherits=name of your current
pointer theme, change that to Inherits=name of new pointer theme which
is the name of the extracted folder you copied in step 4. Mine was
Inherits=Large-Mouse-Cursors  (again note the lack of space and
addition of dashes)
9-save and exit.
10- now go to system/preferences/appearance, click customize, click
pointer tab, and choose your new pointer theme, and exit
11- shut down and restart. Log in and out did not work for me. That's
it, it should work.

Other than a few exceptions above, I take no credit for this. All the
credit goes to this dude AbhiramH on you tube

[http://www.youtube.com/watch?v=CvS9kh_bMyM](http://www.youtube.com/watch?v=CvS9kh_bMyM)

---

### Post by Denver Dave on 2011-09-29
I'm running an Acer Aspire 7741 with ubuntu 11.04.  Might be a related question.  Is there a way to turn mouse trails on?

When I use my my touch pad, it works to move the cursor and click, but the right side scroll area is not functional.  

Could these be driver issues?   If so, where is the best place to get linux drivers for an Acer Aspire laptop?

Thanks.

---

