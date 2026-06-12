---
title: "ntfs and totem"
date: 2005-03-11
forum: General Help
---

### Post by jhands on 2005-03-11
Hi

i want to know if ubuntu can read from my ntfs (windoze) partitions? 
also can totem play formats like real, windows media etc etc. or do i have to install the win32codecs?

also the audio player with hoary does not play radio streams using mpeg. do i have to install codecs for it too or install aother player?
thanks

---

### Post by bored2k on 2005-03-11
[QUOTE=jhands]Hi

i want to know if ubuntu can read from my ntfs (windoze) partitions? 
also can totem play formats like real, windows media etc etc. or do i have to install the win32codecs?

also the audio player with hoary does not play radio streams using mpeg. do i have to install codecs for it too or install aother player?
thanks[/QUOTE]
 Yes it can read windows ntfs partitions
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

Yes totem can read them, with the help of w32codecs yes.
Also try vlc, its an excellent flexible media player. <- do your mpeg streams here or mplayer.


Chances are, you're not going to need any other codecs than those in w32codecs package

You can see the vast codecs you have by reviewing /usr/lib/win32
Make sure totem reads them ]preferences > add plugins > linking/copying the codecs here[

---

### Post by dermotti on 2005-03-11
Yes ubuntu can play off your windowz partitions. I belive ubuntu came with all the codecs except the one to play wmv's. I downloaded a codec pack from [www.mplayerhq.hu](www.mplayerhq.hu) that had all codecs and instructions.

---

### Post by bored2k on 2005-03-11
[QUOTE=dermotti]Yes ubuntu can play off your windowz partitions. I belive ubuntu came with all the codecs except the one to play wmv's. I downloaded a codec pack from [www.mplayerhq.hu](www.mplayerhq.hu) that had all codecs and instructions.[/QUOTE]


So how is Kubuntu working for you? Im a KDE hater but just wanted to know how good the distro is as it was almost some sort of quick surprise.

---

### Post by jhands on 2005-03-11
oh thanks 4 ur replies. I want to know that will I have to mount the partition every time i boot up the system or will it mount by itself.

now i have to ask sum other questions too. :p  

umm how do i make gnome open a directory in the same window rather than opening new windows each time. Also i cant add links to deskktop. How do i do that?

alsooo how do i extract an archive into a folder whose access is restricted? i dunno how to do that in console. i want to extract all the win32codewcs in /usr/lib/win32

---

### Post by Mark Marple on 2005-03-11
[QUOTE=jhands]oh thanks 4 ur replies. I want to know that will I have to mount the partition every time i boot up the system or will it mount by itself.

now i have to ask sum other questions too. :p  

umm how do i make gnome open a directory in the same window rather than opening new windows each time. Also i cant add links to deskktop. How do i do that?

alsooo how do i extract an archive into a folder whose access is restricted? i dunno how to do that in console. i want to extract all the win32codewcs in /usr/lib/win32[/QUOTE]


I'm not a linux guru by any means, so maybe someone else has a better way of doing what you ask, but here is what i did.

1.  Have to look at the exact text for the auto mounting of the ntfs file system
2.  when you open nautilus (the gnome file manager) go to "edit", "preferences", "behaviour tab" and select the 3rd from top "always open in browser window"......that has worked for me.  You will also notice that this gives you a toolbar for back and forth, etc.
3. what I would do for this (extracting) is create a folder in your home directory called "downloads" or something like that.  Select the "essentials" file with a right click and go to 2nd from bottom "extract here".............it will place a folder, inside that folder will be the files for the codecs.  You can then just copy and paste them into the /usr/lib/win32 folder..............of course you have to be root or sudo to do this.  How you do that is open a root terminal under "applications", "system tools"
then type "nautilus" (without quotes)

I hope this helps and I will look into the automount ntfs

PLEASE.....if anyone else has a better way, let me know as well, because I always need to learn.

---

### Post by Mark Marple on 2005-03-11
[QUOTE=jhands]oh thanks 4 ur replies. I want to know that will I have to mount the partition every time i boot up the system or will it mount by itself.

now i have to ask sum other questions too. :p  

umm how do i make gnome open a directory in the same window rather than opening new windows each time. Also i cant add links to deskktop. How do i do that?

alsooo how do i extract an archive into a folder whose access is restricted? i dunno how to do that in console. i want to extract all the win32codewcs in /usr/lib/win32[/QUOTE]

as i look to see what others have done for mounting ntfs, you may want to look in the forums for "mounting ntfs"  there are many ways to mount this..........being in your /home folder or under the /mnt folder......etc etc.  there are also many commands that you can give as well.............i'm not sure what they all mean, and I'm sorry but I had this working GREAT last week, but have since erase the windXP drive to make more room for Ubuntu, so I can't share my fstab file with ya.

Good luck with your ?'s...........alot of knowledgeable people here that are just great to deal with.

---

### Post by jhands on 2005-03-12
[QUOTE=Mark Marple]I'm not a linux guru by any means, so maybe someone else has a better way of doing what you ask, but here is what i did.

1.  Have to look at the exact text for the auto mounting of the ntfs file system
2.  when you open nautilus (the gnome file manager) go to "edit", "preferences", "behaviour tab" and select the 3rd from top "always open in browser window"......that has worked for me.  You will also notice that this gives you a toolbar for back and forth, etc.
3. what I would do for this (extracting) is create a folder in your home directory called "downloads" or something like that.  Select the "essentials" file with a right click and go to 2nd from bottom "extract here".............it will place a folder, inside that folder will be the files for the codecs.  You can then just copy and paste them into the /usr/lib/win32 folder..............of course you have to be root or sudo to do this.  How you do that is open a root terminal under "applications", "system tools"
then type "nautilus" (without quotes)

I hope this helps and I will look into the automount ntfs

PLEASE.....if anyone else has a better way, let me know as well, because I always need to learn.[/QUOTE]

oh thank u sooo much, as for the automounting, i found a tutorial in the ubuntu guide. :)

---

### Post by Mark Marple on 2005-03-12
your welcome jhands.......just glad I could help.

---

