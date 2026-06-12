---
title: "unable to use wine"
date: 2011-03-09
forum: General Help
---

### Post by harkumar on 2011-03-09
Hi,

I am using ubuntu 10.10 net-book edition. I installed wine to work with some .exe files.
But as soon as I open it using WINE the message appears every time. I have attached the screen shot.

Any help will be appreciated.

---

### Post by ~Plue on 2011-03-10
right click the .exe >> properties >> permissions tab >> check 'allow executing file as a program'

if the .exe is on a cd/dvd (read-only media) right click >> open with other application >> use custom command >> *wine*

~hope that helps

---

### Post by harkumar on 2011-03-11
nope...the option "allow executing file as a program" cannot be clicked.

---

### Post by ~Plue on 2011-03-11
just noticed that its on a fat/ntfs drive..iirc, ubuntu mounts them with the noexec flag.. try the second method in my previous post

and if that doesn't work, copy the .exe to your hard-drive (desktop or home folder) and then try to set the permissions

---

### Post by Morbius1 on 2011-03-11
[http://ubuntuforums.org/showthread.php?p=10478279#post10478279](http://ubuntuforums.org/showthread.php?p=10478279#post10478279)

Easy way:
> The irony of all this is that wine doesn't care if it's executable. Wine  is incapable of determining if a file has a Linux executable bit set.  Wine isn't stopping you from running an exe file Ubuntu is through  something called "cautious-launcher".

Open up "Properties" on /usr/share/applications/wine. The first thing you see in the Command Box is "cautious-launcher".

Now go to /usr/bin/cautious-launcher -  it's a script that checks to see if it has a Linux executable bit set.

[COLOR=Blue]If you right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine
In the "Open With" tab mark the "wine"[/COLOR][COLOR=Blue] you added as  the default ( from the Wine that's already selected) and theoretically  every time you run an exe it should select the wine without the cautious  launcher script.[/COLOR]Slightly more involved way that nips the problem at it's source:
> Thanks Morbius; Opened a root privileged file browser with "gksudo  nautilus" command in Terminal. From that window that popped up from the  "gksudo nautilus" command, [COLOR=Blue]opened /usr/share/applications/wine and  changed the "Command" box in "Wine Windows Program Loader" from  "cautious-launcher %f wine start /unix" to "wine start /unix"[/COLOR]. 


---

