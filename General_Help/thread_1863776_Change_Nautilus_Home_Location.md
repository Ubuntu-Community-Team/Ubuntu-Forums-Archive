---
title: "Change Nautilus Home Location"
date: 2011-10-18
forum: General Help
---

### Post by Vapourstreak on 2011-10-18
Is it possible to change the location Nautilus takes me to when I click the "Home" places on the sidebar?  I have an NTFS partition that I already set as the Music, Downloads, Pictures, etc. folders, but I cant' seem to figure out how to change the home. 

Thanks,
Vapour

---

### Post by Jacobonbuntu on 2011-10-18
to change the actual "home" location, you need to edit the fstab file, might be tricky and risky if you never did that before. To change the location where the "home" icon takes you, or to add locations to it, look here:
[http://ubuntuforums.org/showthread.php?t=1780002&highlight=launcher](http://ubuntuforums.org/showthread.php?t=1780002&highlight=launcher)

reading it back it looks more complicated than it is :)

---

### Post by Vapourstreak on 2011-10-18
I'm just trying to change where Nautilus "thinks" my Home is, which I want to be the NTFS partition, but I can't change that to the actual Home, because then PulseAudio breaks.

I'm using Gnome Shell 3.2, and Nautilus 3.

I'm pretty okay with editing fstab, and I have edited it before to make my NTFS partition mount the way I wanted it to, so that's no problem.

---

### Post by Jacobonbuntu on 2011-10-18
> **Vapourstreak said:**
> I'm just trying to change where Nautilus "thinks" my Home is, which I want to be the NTFS partition, but I can't change that to the actual Home, because then PulseAudio breaks.

I'm using Gnome Shell 3.2, and Nautilus 3.

I'm pretty okay with editing fstab, and I have edited it before to make my NTFS partition mount the way I wanted it to, so that's no problem.

ah, I see, 
but to change the location the icon is pointing to, you can easily change the location in the /home/yourname/.local/share/applications/nautilus-home.desktop -file

---

### Post by collisionystm on 2011-10-18
> **Vapourstreak said:**
> I'm just trying to change where Nautilus "thinks" my Home is, which I want to be the NTFS partition, but I can't change that to the actual Home, because then PulseAudio breaks.

I'm using Gnome Shell 3.2, and Nautilus 3.

I'm pretty okay with editing fstab, and I have edited it before to make my NTFS partition mount the way I wanted it to, so that's no problem.


Change your home in /etc/passwd

Just edit the line to reflect your new home. Your username will be at the bottom of the file.

NOTE: Using an NTFS as your home is not a good idea because Linux  cannot set permissions on an NTFS file system. Just an fyi...

---

### Post by collisionystm on 2011-10-18
> **collisionystm said:**
> Change your home in /etc/passwd

Just edit the line to reflect your new home. Your username will be at the bottom of the file.

NOTE: Using an NTFS as your home is not a good idea because Linux  cannot set permissions on an NTFS file system. Just an fyi...

Just to double check myself, I made myself a new home directly on /

I pointed myself to it in /etc/passwd

logged out and back in

the system automatically created the default folders in my new home. Theme was set to ubuntu default. It works.

---

### Post by Vapourstreak on 2011-10-18
Sorry, I think you're misunderstanding me.  I can't change my actual Home folder location, because if I set it to my NTFS, it breaks PulseAudio.  What I'm looking for is a way to make Nautilus think that NTFS is my home, so when I click the "Home" button on the sidebar, and when I start the application, it will take my to my NTFS partition instead of my actual Home.

---

### Post by Vapourstreak on 2011-10-18
> **Jacobonbuntu said:**
> ah, I see, 
but to change the location the icon is pointing to, you can easily change the location in the /home/yourname/.local/share/applications/nautilus-home.desktop -file

No such file for me, apparently.  I checked through Gedit, Terminal, and Nautilus.  Is there any other location where the file might be?  It seems logical that it would be in a .desktop file, no idea why I hadn't thought of it before. :)

---

### Post by collisionystm on 2011-10-18
> **Vapourstreak said:**
> Sorry, I think you're misunderstanding me.  I can't change my actual Home folder location, because if I set it to my NTFS, it breaks PulseAudio.  What I'm looking for is a way to make Nautilus think that NTFS is my home, so when I click the "Home" button on the sidebar, and when I start the application, it will take my to my NTFS partition instead of my actual Home.

Okay

Open your ubuntu home folder

make a new document

Edit it

Put this


> [Desktop Entry]
Name=NTFS_Home
Comment=Link to NTFS
Exec=nautilus /pathToNtfs
Icon=/home/YOURUSERNAME/whateverpictureyouwant
Type=Application

right click it when done, go to properties, make executable

you can drag it onto your unity launcher

---

### Post by Jacobonbuntu on 2011-10-18
> **Vapourstreak said:**
> No such file for me, apparently.  I checked through Gedit, Terminal, and Nautilus.  Is there any other location where the file might be?  It seems logical that it would be in a .desktop file, no idea why I hadn't thought of it before. :)

you probably know it is hidden by default? it really must be there! what happens if you open your personal folder, press ctrl-h? and navigate manually to .local > share > applications > 
there should be a file named nautilus-home.desktop

if not you could create one :) (but it must be there...)

---

### Post by Vapourstreak on 2011-10-18
I'm using gnome shell. /:

And I'm not looking for a launcher, I'm looking to edit some kind of Nautilus settings or something.

---

### Post by Vapourstreak on 2011-10-18
And yeah, I checked the actually .local/share/applications, but all I find is some stuff from WINE, and some mimeinfo stuff from chrome.  And the only subfolder is Wine/Programs, which is empty.

---

### Post by Jacobonbuntu on 2011-10-18
> **Vapourstreak said:**
> I'm using gnome shell. /:

ooops, sorry, I looked over it.... never tried that for a long(er) time

---

### Post by collisionystm on 2011-10-18
> **Vapourstreak said:**
> I'm using gnome shell. /:

it doesn't matter. My previous instructions still work. Just use the edit menu program and put the application in.

---

### Post by Vapourstreak on 2011-10-18
> **collisionystm said:**
> it doesn't matter. My previous instructions still work. Just use the edit menu program and put the application in.
Yeah, I know what you mean, I've played around with .desktops before to create launchers, but that's not what I'm aiming at.  

I'm aiming to change Nautilus, so that even the sidebar link leads me to a custom Home, as it can lead me to as custom Music, Download, Picture, Video, Public, and Template folders that I have set on my NTFS.  The only folder that I can't seem to move is the Home.

The moved folders recognized above is natively recognized by Nautilus as the folders, through modifications of the userdir.dirs file, but there's no Home entry there.

---

### Post by collisionystm on 2011-10-18
> **Vapourstreak said:**
> Yeah, I know what you mean, I've played around with .desktops before to create launchers, but that's not what I'm aiming at.  

I'm aiming to change Nautilus, so that even the sidebar link leads me to a custom Home, as it can lead me to as custom Music, Download, Picture, Video, Public, and Template folders that I have set on my NTFS.  The only folder that I can't seem to move is the Home.

The moved folders recognized above is natively recognized by Nautilus as the folders, through modifications of the userdir.dirs file, but there's no Home entry there.

That is because HOME itself is designated in /etc/passwd.

---

### Post by Vapourstreak on 2011-10-18
Oh, so I guess it isn't possible.

Thanks though. :)

---

