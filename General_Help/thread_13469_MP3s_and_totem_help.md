---
title: "MP3s and totem help"
date: 2005-01-31
forum: General Help
---

### Post by pumpkinpatch on 2005-01-31
I can not get either totem or my music player to work.  I have tryed to download other players such as gnomemp3 and also xmms pluggins but nothing seems to be working.  I'm using apt-get to install but can't find them once they have downloaded.  Please let me know if you have ideas on how to fix it.

---

### Post by CowPie on 2005-01-31
[QUOTE=pumpkinpatch]I can not get either totem or my music player to work.  I have tryed to download other players such as gnomemp3 and also xmms pluggins but nothing seems to be working.  I'm using apt-get to install but can't find them once they have downloaded.  Please let me know if you have ideas on how to fix it.[/QUOTE]

Try apt-get remove totem-gstreamer 

and then 

apt-get install totem-xine

---

### Post by pumpkinpatch on 2005-01-31
I tryed the  apt-get remove totem-gstreamer and that seem to work. However when I tryed  apt-get install totem-xine it said  Package totem-xine has no installation candidate.  This is what it usually says when I attempt to install a package.

---

### Post by CowPie on 2005-01-31
[QUOTE=pumpkinpatch]I tryed the  apt-get remove totem-gstreamer and that seem to work. However when I tryed  apt-get install totem-xine it said  Package totem-xine has no installation candidate.  This is what it usually says when I attempt to install a package.[/QUOTE]
 OK, what does your /etc/apt/sources.list look like?

---

### Post by pumpkinpatch on 2005-01-31
permission denied

---

### Post by jdodson on 2005-01-31
there is good info on adding mp3 playback here: [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by pumpkinpatch on 2005-01-31
I'll give it a go.

Cools hot to me.  I don't have any web sites to share though.  I sure I'll be asking for more help soon.

---

### Post by pumpkinpatch on 2005-01-31
I have tryed apt-get install xmms and it says it has installed however it doesn't show up anywhere. I have tryed to update totem but apt-get can't find it.  any other ideas?

---

### Post by pumpkinpatch on 2005-01-31
when i try to access my source list it said this

Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
I/O warning : failed to load external entity "/root/.gnome2/gedit-metadata.xml"

---

### Post by carlc on 2005-01-31
XMMS should show up under "multimedia"
Try logging out and then back into gnome

---

### Post by carlc on 2005-01-31
Have you tried Rhythmbox?

---

### Post by carlc on 2005-01-31
This is from the

[Unofficial Ubuntu Starter Guide]( http://ubuntuguide.org/) 


> How to install Multimedia Codecs?

   1. Read General Notes
   2. Read How to add extra repositories?
   3. $ sudo apt-get install gstreamer0.8-plugins
       $ sudo apt-get install w32codecs



---

### Post by pumpkinpatch on 2005-01-31
xmms is now working however it can't access music that is saved on my house network only files on my computer.  Any ideas as to why? 

I could really use a video player as well.  I can't seem to access totem.  are there any other media players like windows media player that do it all in one?

---

### Post by carlc on 2005-01-31
Hey, try this. Click computer, then network. If your home network shows up, navigate to a mp3. Then right click the song, and chose "open with Music Player" (or which ever program that is listed that will play MP3's). This worked on mine and is fine for single songs but not music directories. 

I have not figured out yet how to use xmms to open a song or directory on the network through.   

I tried entering the location ...... 

smb://nameofhomenetwork/SharedDocs/MyMusic/She_Loves_You.mp3   

but that did NOT work.

If the home network files are mounted in the filesystem, then it would be easy but I can not tell of they are or not.  :confused:

---

### Post by CowPie on 2005-01-31
[QUOTE=pumpkinpatch]when i try to access my source list it said this

Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
I/O warning : failed to load external entity "/root/.gnome2/gedit-metadata.xml"[/QUOTE]

I think that's because there is not root account so thats why gedit is failing.

show me it using nano -w as the editor (sudo apt-get install nano).  In any terms you should add multiverse and universe for what your looking for.

---

### Post by pumpkinpatch on 2005-02-01
Thanx ya'll. totem almost works and I can listen to music now.  Your help is much appreciated.

---

### Post by pumpkinpatch on 2005-02-01
So I attempted to install both rythembox and Kaffiene through apt-get and it seem to download but I can't seem to find it.  Oh, and yes I rebooted the puter.  Anyone know where they might be hiding?

---

### Post by john_c on 2005-02-01
re: finding program files

go to a terminal

Try "which" command (without quotes) and then the name of the program.  eg.

to find the directory containing the executable for xmms

which xmms

If you wish to put this command into your applications menu note the result.  In case the command is not in your application menu you can right click in the submenu in which you wish to put it and follow  ENTIRE MENU > ADD NEW ITEM TO THIS MENU and then fill in the blanks.

Hope this helps.  Took me a lot of looking through directories before I discovered this - lots to learn.

John_c

---

