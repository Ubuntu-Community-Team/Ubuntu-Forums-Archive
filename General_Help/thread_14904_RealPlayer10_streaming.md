---
title: "RealPlayer10 streaming"
date: 2005-02-10
forum: General Help
---

### Post by alof8k on 2005-02-10
I've recently have done a fresh installation of warty and have just installed the Real Player 10 application as directed over at ubuntuguide.org.  Everything seems to work fine except for one thing.  I am unable to stream files from realguide.com.  Those .ra files can only be viewed if I save them to the harddisk, and then open them from realplayer10.  If I clicking on the link from the site and try to open it, then realplayer10 gives me an error saying it can't play the file.  I'm really sorry if this has been answered before but I was unable to find a similar thread even relating to this problem.  By the way, I know this can be fixed because I remember being able to watch these streams a few weeks ago when I was going insane and installing everything as per ubuntuguide.org.  Any help would be greately appreciated.  :-)

---

### Post by alof8k on 2005-02-10
Seems like this wasn't much of a stumper.  All I had to do was upgrade to firefox 1.0, by changing the repositories as per ubuntu guide.  Then upgrade firefox 1.0, and also added the firefox-gnome integration file aswell (ofcourse close firefox when doing this).  Then it seems to play the .ra files off realguide.   \\:D/

---

### Post by T31 on 2005-02-11
in my case even doing that i cant get any image from the player just sound  ](*,) 

by the way anyone knows how to force firefox to use only one application for video? mplayer plugin doesnt work to me and when opens a .mov file with totem is ok but when does with xine crash

please heeeeeelp!!!

---

### Post by alof8k on 2005-02-11
[QUOTE=T31]in my case even doing that i cant get any image from the player just sound  ](*,) 

by the way anyone knows how to force firefox to use only one application for video? mplayer plugin doesnt work to me and when opens a .mov file with totem is ok but when does with xine crash

please heeeeeelp!!![/QUOTE]

Well you could download the file, right click on it, goto properties and change the 
application which handles the file in the "open with..." tab.  Also try opening up firefox, goto preferences | downloads, and change the the file types associated with the application.    These should help. 

if the problem still presists, then goto Computer | Home.  then from the menu, View | Show Hidden Files.  Open .mozilla then firefox and delete pluginreg.dat .  Oh and make sure all firefox windows are closed while doing this.  then just open up firefox again. 

Hope this helps.

---

