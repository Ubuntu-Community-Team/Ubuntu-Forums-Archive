---
title: "I was dumb enough to do a chmod -R on /"
date: 2011-09-07
forum: General Help
---

### Post by piyush.popli on 2011-09-07
Hello everyone,
So I was stupid enough to this ```
chmod -R 700 .
``` at /.. and basically everything got screwed up.. don't ask me what was going though my mind but it just happened.. :mad:

I wasn't able to boot up so I reduced the runlevel to 3.. logged in as root and and did a ```
chmod -R 777
``` at /.. I can now boot up.. there are a host of problems and I know that they would take quite sometime to figure out... I've been able to get my head around a few but there are 2 that I would really appreciate some help on as I've run out of ideas on those..
1.) My Audacious complains after boot up.. posting the error msg is irrelevant as I was able to narrow down the problem.. it basically was because after startup my /dev/snd looks like this

```
piyush@Piyush-Desktop:/dev/snd$ ll
total 0
drwxr-xr-x  3 root root      220 2011-09-07 18:54 ./
drwxr-xr-x 19 root root     4240 2011-09-07 18:54 ../
drwxr-xr-x  2 root root       60 2011-09-07 18:54 by-path/
crw-rw----  1 root audio 116,  7 2011-09-07 18:54 controlC0
crw-rw----  1 root audio 116,  6 2011-09-07 18:54 hwC0D0
crw-rw----  1 root audio 116,  5 2011-09-07 18:54 hwC0D3
crw-rw----  1 root audio 116,  4 2011-09-07 18:54 pcmC0D0c
crw-rw----  1 root audio 116,  3 2011-09-07 18:54 pcmC0D0p
crw-rw----  1 root audio 116,  2 2011-09-07 18:54 pcmC0D3p
crw-rw----  1 root audio 116,  1 2011-09-07 18:54 seq
crw-rw----  1 root audio 116, 33 2011-09-07 18:54 timer
```whereas for it to work properly it should look like this
```
piyush@Piyush-Desktop:/dev/snd$ ll
total 0
drwxr-xr-x  3 root root      220 2011-09-07 18:54 ./
drwxr-xr-x 19 root root     4240 2011-09-07 18:54 ../
drw-rw-rw-  2 root root       60 2011-09-07 18:54 by-path/
crw-rw-rw-  1 root audio 116,  7 2011-09-07 18:54 controlC0
crw-rw-rw-  1 root audio 116,  6 2011-09-07 18:54 hwC0D0
crw-rw-rw-  1 root audio 116,  5 2011-09-07 18:54 hwC0D3
crw-rw-rw-  1 root audio 116,  4 2011-09-07 18:58 pcmC0D0c
crw-rw-rw-  1 root audio 116,  3 2011-09-07 18:58 pcmC0D0p
crw-rw-rw-  1 root audio 116,  2 2011-09-07 18:58 pcmC0D3p
crw-rw-rw-  1 root audio 116,  1 2011-09-07 18:54 seq
crw-rw-rw-  1 root audio 116, 33 2011-09-07 18:54 timer
```so after every boot I have to do a chmod on this dir.. I know I can solve this with a startup script but I was hoping for a cleaner soln..


2.) My gnome-volume-applet has suddenly disappeared.. So I use the notification area in my bottom panel (and yes I hate the new Unity L&F of Natty).. I can see all other icons (like thunderbird, artha, pidgin, audacious etc etc) but the volume-applet... when I do a ps I can see that the applet is running.. it's just that somehow it's not getting rendered in the notification area.. I've deleted and created the notification area again but that doesn't seem to do the trick.. the applet runs at startup through the startup applications.

Eagerly awaiting responses..  

Ps: I'm on Ubuntu 11.04 (Natty)

Thanks
Piyush

---

### Post by Wayne_V on 2011-09-07
I don't know of any easy way to do this on Debian based systems, but you can set the file permissions back to what they were 'as delivered' if you have the .deb files.

You would have to do something like:

cd <directory holding .deb files of all installed packages>
for F in *.deb
do
  dpkg--contents $F | awk '{print $1,$6}' | cut -c2- | while read PERMS FNAME
  do
     (convert $PERMS to something usable by chmod)
     chmod $PERMS $FNAME
  done
done

It would probably be easier to back up your user files and then reinstall.

---

### Post by bodhi.zazen on 2011-09-07
Easiest fix by far is to back up your data and re-install.

I have seen several people struggle to try to fix this mistake over the years, typically they spend weeks at it and re-install in the end.

I have seen one user "fix" the problem, although I am not convinced it was a long term fix.

If you wish, boot a live CD and start going through all the files and directories in / one - by - one and setting permissions and ownership in your Ubuntu / directory.

---

### Post by Habitual on 2011-09-07
> **bodhi.zazen said:**
> Easiest fix by far is to back up your data and re-install.

+1 and Amen.

---

### Post by WyleECoyote on 2011-09-07
yep, I just did nearly the same thing 2 days ago but my mistake was to chown -R root:root /usr

needless to say it broke a few packages and booted me out of sudoers, since I have spent countless hours setting my Debian up custom, I did not want to reistall all of debian, however if you do and you still want all your packages back you can make a backup list of everything installed, here is that link:

[http://lglinux.blogspot.com/2007/11/backup-ubuntu-debian-package-selection.html](http://lglinux.blogspot.com/2007/11/backup-ubuntu-debian-package-selection.html)

however as I said that is only a last ditch effort for me, I then came across this link:

[http://hyperlogos.org/Restoring-Permissions-Debian-System](http://hyperlogos.org/Restoring-Permissions-Debian-System)

that may work but will take a VERY VERY long time, is far easier to reinstall so I just ran my programs as I normally do after I fixed my sudoers permissions then just reinstalled any package that had problems which were few, I only had big issues with mail and policykit-1 which did remove other packages, I just listed all of them then reinstalled, now all my permissions are mostly back together and so far have no issues and some actually run far better than they did before

---

### Post by piyush.popli on 2011-09-09
Thanks for all the help guys.. I ran out of steam and finally reinstalled..
Anyways, anyone who has been "adventurous" enough to do this and doesn't have that option available ASAP.. this might help:
```
chmod 4111 /usr/bin/sudo
``` .. will atleast let you sudo stuff and try and rectify the damage done.. (and best of luck to you for that):lolflag:


Ps: if you're fond of su (like myself :P) do the same to /bin/su

Thanks
Piyush

---

