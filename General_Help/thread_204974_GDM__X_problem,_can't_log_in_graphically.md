---
title: "GDM / X problem, can't log in graphically"
date: 2006-06-27
forum: General Help
---

### Post by nalmeth on 2006-06-27
My problem started right around the same time as these apparent problems people have been having with auto-login, after the update.

My problem is much worse though, after the system starts, and right when GDM is supposed to load, I'm stuck at an OLD looking x cursor, and a black screen. GDM NEVER loads.

I can of course switch to virtual terminals and back, but never get past the black screen and x cursor.

How would I go about installing an older GDM through apt? 

Never been in this sort of position before, never had to hunt down old versions..

---

### Post by nalmeth on 2006-06-27
I can now get into xfce by stopping GDM and starting X through tty, but would still like to fix this GDM business. 

Anyone able to suggest a method?

---

### Post by nalmeth on 2006-06-28
As I dig deeper it seems nothing gnome related is working, and debugging it looks like something with gnomes libraries is messed up.
```
sdcb@vaiobuntu:~$ sudo gdmsetup
Password:
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.
``` ```
sdcb@vaiobuntu:~$ totem
totem: error while loading shared libraries: /usr/lib/liblaunchpad-integration.so.0: invalid ELF header
``` Since everything went wrong, I haven't been able to get these updates:
```
The following packages have been kept back:
  libecore0 libedb1 libedje0 libeet0 libembryo0 libepeg0 libepsilon0
  libesmart0 libevas0 libewl0 libimlib2
``` Just now I was able to download some updates, and I'm getting this weird output. I remember seeing it before, but nothing went wrong, so I ignored it. I know, ignorance will catch up to you:
```
Setting up libgtk2.0-0 (2.8.18-0ubuntu2) ...
ldconfig: /usr/lib/libgnomecanvas-2.so.0.1400.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libgnome-2.so.0.1401.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libgnomecanvas-2.so.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libgnome-2.so.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libbonoboui-2.so.0.0.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libbonoboui-2.so.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libebook-1.2.so.5.2.1 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libgnomeui-2.so.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libebook-1.2.so.5 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/liblaunchpad-integration.so.0.0.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/liblaunchpad-integration.so.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libgnomeui-2.so.0.1401.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libfltk.so.1.1 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libkpinterfaces.so.1.0.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libkpinterfaces.so.1 is not an ELF file - it has the wrong magic bytes at the start.


Setting up gtk2-engines-pixbuf (2.8.18-0ubuntu2) ...
Setting up libgtk2.0-bin (2.8.18-0ubuntu2) ...
Updating the IM modules list for GTK+-2.4.0...done.
Updating the gdk-pixbuf loaders list for GTK+-2.4.0...done.
```
Anyone know whats up with this ELF and magic stuff? Gnome is floating in fantasyland

---

### Post by Ramses de Norre on 2006-06-28
The not starting of the applications is normal, they need an X server. But those libgtk2.0-0 errors are pretty scary.. Have you tried reinstalling gdm? And maybe ubuntu-desktop? (sudo aptitude reinstall package_name)

---

### Post by aysiu on 2006-06-28
[QUOTE=Ramses de Norre]But those libgtk2.0-0 errors are pretty scary.. [/QUOTE] I agree. When [nothing in a Google search comes up for an error](http://www.google.com/search?hl=en&q=ldconfig%3A+%2Fusr%2Flib%2Flibkpinterfaces.so.1+is+not+an+ELF+file+-+it+has+the+wrong+magic+bytes+at+the+start.&btnG=Google+Search), it's pretty scary.

I think you're on the right track, though: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
sudo /etc/init.d/gdm start
``` is a good first thing to try.

---

### Post by nalmeth on 2006-06-28
Thanks for the reply's guys!

I have reverted to KDM for the moment, and thankfully it is working.

It appears though, that everything gnome related is broken.
The output with gdmsetup and totem was from xfce, I did get X back up again. The same type of thing goes for eog evince and other gnome apps.

I don't really know what to do, short of completely removing gnome and its remnants, then perhaps reinstalling, perhaps not.

All xfce and kde components work well (I've got kde gnome and xfce install BTW), but I don't like using KDE stuff in xfce, as it bogs it down majorly with all the qt libraries.

The more I think about it, I get some more details about when things went wrong. I believe I was doing a dist-upgrade, and left and took a nap. When I got back, the laptop was mysteriously shutoff (power *was* plugged in). Also, I have been using prelink on this machine for some time, so I'm thinking that the laptop powered off (for whatever reason) during the prelink, as when I tried to resume the upgrade, I got the same message as above. 
```
The following packages have been kept back:
  libecore0 libedb1 libedje0 libeet0 libembryo0 libepeg0 libepsilon0
  libesmart0 libevas0 libewl0 libimlib2
``` 
So either the upgrade was interupted and caused some breakage, or prelink was interupted and caused some breakage.

Anyone up to wager a guess?

PS indeed scary, but kind of funny little errors eh? Next I'll be hearing that my pixie fairies are short on fairy dust.

---

### Post by trent dillman on 2006-06-28
You installed E17, didn't you?

Those updates are held back from a non-official repo. Comment out 
```
deb http://gefechtsdienst.de/uman/files/ unstable main
```
from your /etc/apt/sources.list.

---

### Post by nalmeth on 2006-06-29
ahh, yes of course. Should have recognized that. ](*,)

ecore or epsilon should have given it away

thanks!

---

