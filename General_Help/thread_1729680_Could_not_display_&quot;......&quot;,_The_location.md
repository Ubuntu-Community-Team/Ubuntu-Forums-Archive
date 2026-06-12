---
title: "Could not display &quot;......&quot;, The location is not a folder."
date: 2011-04-15
forum: General Help
---

### Post by badou on 2011-04-15
I updated from ubuntu 10.10 to ubuntu 11.04 beta 1 a month ago, and since then this problem exists.

Everytime I open a file from google desktop search or firefox download
I got this message.
Could not display "......", The location is not a folder.

But if I open a folder from google desktop search, there is no problem.

For example, I search for a .pdf and open from google desktop, I got:
Could not display "/home/yikai/Dropbox/Books/Ma...rise Macroeconomic Theory.pdf", The location is not a folder.


This problem exists in my laptop and desktop. 
But after I did a clean installation of 11.04 beta 1 on the laptop, this problem disappears.
However I could not do this in the desktop, since it belongs to the office.

I tried reinstall nautilus, ubuntu-desktop, and google desktop, this problem still exists.
What can I do? 
Many thanks!

---

### Post by badou on 2011-04-15
Now I installed nautilus-elementary to replace nautilus.

The problem becomes that it automatically open the folder containing the file but not the file itself.

So I guess it is somewhere the ubuntu tells google desktop and firefox to do:
"nautilus aaaa.pdf" or something
How can I change this? Thanks!

(The file association in firefox and nautilus are correct, for example, .pdf is associated with DocumentViewer )

Thank again for help!

---

### Post by badou on 2011-04-17
Anyone find a solution for this?
Thanks a lot!

---

### Post by calcfreak89 on 2011-04-17
I am having the same issue here. Chrome and Firefox both have this problem.

---

### Post by PWill on 2011-04-18
I have this problem too, using Chrome. Still looking for a solution.

---

### Post by NRDNick on 2011-04-19
Seems like it's a problem with xdg-utils, as I understand most programs use xdg-open to open files. I have this same problem trying to open an avi directly from deluge and also while trying to open a video file through the android gmote application while trying to use mplayer instead of vlc by changing the player line to```
filegroup:VIDEO:org.gmote.server.media.basic.DefaultFilePlayer
``` . I found this bug report that seems relevant. [https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/743859]("https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/743859") 

It looks like xdg-open wants to use nautilus to open stuff.

---

### Post by shantiq on 2011-04-20
> **badou said:**
> I updated from ubuntu 10.10 to ubuntu 11.04 beta 1 a month ago, and since then this problem exists.

Everytime I open a file from google desktop search or firefox download
I got this message.
Could not display "......", The location is not a folder.

But if I open a folder from google desktop search, there is no problem.

For example, I search for a .pdf and open from google desktop, I got:
Could not display "/home/yikai/Dropbox/Books/Ma...rise Macroeconomic Theory.pdf", The location is not a folder.


This problem exists in my laptop and desktop. 
But after I did a clean installation of 11.04 beta 1 on the laptop, this problem disappears.
However I could not do this in the desktop, since it belongs to the office.

I tried reinstall nautilus, ubuntu-desktop, and google desktop, this problem still exists.
What can I do? 
Many thanks!



got [the exact same ]("http://ubuntuforums.org/showthread.php?t=1719689") with google-chrome :KS:KS:KS

no idea what to do    also reinstalled and looked around nothing so far

the download was working fine at first so some setting clearly has set itself to something new and each time sends this annoying message   the location is not a folder




how to correct that?    surely someone knows :KS:KS

---

### Post by sean.tnl on 2011-04-28
Found this post which helped me resolve the issue:

[https://bbs.archlinux.org/viewtopic.php?id=112069](https://bbs.archlinux.org/viewtopic.php?id=112069)

I removed exo-utils and the click->open function has returned to normal.

---

### Post by NRDNick on 2011-04-29
> **sean.tnl said:**
> Found this post which helped me resolve the issue:

[https://bbs.archlinux.org/viewtopic.php?id=112069](https://bbs.archlinux.org/viewtopic.php?id=112069)

I removed exo-utils and the click->open function has returned to normal.

Worked great, thank you!

---

### Post by shantiq on 2011-04-29
> **sean.tnl said:**
> Found this post which helped me resolve the issue:

[https://bbs.archlinux.org/viewtopic.php?id=112069](https://bbs.archlinux.org/viewtopic.php?id=112069)

I removed exo-utils and the click->open function has returned to normal.[SIZE="2"]**dude**[/SIZE] after 3 or 4 weeks the answer drops thanx

why do they put software in the repositories which clash   hmmmmmmmmmm????   is that not a good question   GoogleChrome is a pretty major part of many people's setup



so why have  exo in there which really upsets it/?

anyway no more bitching.   this is really cool    i had asked the question elsewhere. will link this answer:KS

---

### Post by badou on 2011-05-02
> **sean.tnl said:**
> Found this post which helped me resolve the issue:

[https://bbs.archlinux.org/viewtopic.php?id=112069](https://bbs.archlinux.org/viewtopic.php?id=112069)

I removed exo-utils and the click->open function has returned to normal.



Thanks a lot!
"sudo apt-get remove exo-utils"
works!

---

### Post by uniq on 2011-05-05
> **badou said:**
> Thanks a lot!
"sudo apt-get remove exo-utils"
works!

perfect :)

---

### Post by alexcuervo on 2011-05-11
> **badou said:**
> Thanks a lot!
"sudo apt-get remove exo-utils"
works!

This solution is not optimal as it also removes thunar.

I need both thunar and nautilus in my daily workflow.

Is there a solution that keeps thunar installed?

Thanks

---

### Post by alexcuervo on 2011-05-11
I have found a solution if you need to keep Thunar at:

[http://queleimporta.com/thunar-nautilus-exo-utils-and-the-location-is-not-a-folder-error-solution-under-gnome/](http://queleimporta.com/thunar-nautilus-exo-utils-and-the-location-is-not-a-folder-error-solution-under-gnome/)

Removing exo-utils also removes thunar. Some of us need to have both thunar and nautilus installed in gnome:
Since the problem is exo-utils, I have built a thunar .deb without the exo-utils dependency.
Here is how for 64bit:
```
wget http://launchpadlibrarian.net/69753654/thunar_1.2.1-3ubuntu2_amd64.deb
dpkg-deb -x thunar_1.2.1-3ubuntu2_amd64.deb tmpdir
dpkg-deb --control thunar_1.2.1-3ubuntu2_amd64.deb tmpdir/DEBIAN
gedit tmpdir/DEBIAN/control

```
Remove ‘exo-utils’ from the ‘Depends’ line and save
```
dpkg -b tmpdir thunar_1.2.1-3ubuntu2_amd64-no_exo-utils_dependency.deb
sudo apt-get remove exo-utils
sudo dpkg -i thunar_1.2.1-3ubuntu2_amd64-no_exo-utils_dependency.deb
sudo apt-get -f install

```Done!

---

### Post by Katerinka on 2011-05-18
Thanxs a lot!!!

:D

---

### Post by mmc on 2011-05-31
if you want to retain xfce installed and simply fix the opening of files then you can;

 - open 'exo-preferred-applications' 
 - change the preferred "file manager" under "utilities" to Thunar"

you should be good to go.
I think the installation of XFCE changed the default back to nautilis and this borks unity/thunar.

mmc.

---

### Post by Aquix on 2011-07-11
> **mmc said:**
> if you want to retain xfce installed and simply fix the opening of files then you can;

 - open 'exo-preferred-applications' 
 - change the preferred "file manager" under "utilities" to Thunar"

you should be good to go.
I think the installation of XFCE changed the default back to nautilis and this borks unity/thunar.

mmc.


You are a legend! That worked like a charm. Now I have my beloved thunar and miro playing nicely together.
Thanks.

---

### Post by castorls on 2011-07-21
Excellent, this is working for me too. Great thanks

Castor

---

### Post by ihadanny on 2011-10-08
> **sean.tnl said:**
> Found this post which helped me resolve the issue:

[https://bbs.archlinux.org/viewtopic.php?id=112069](https://bbs.archlinux.org/viewtopic.php?id=112069)

I removed exo-utils and the click->open function has returned to normal.

life saver. bye bye thunar.

---

### Post by ewenss on 2012-12-05
I realize this is an older thread, but the fix at [http://uberstudent.com/phpBB/viewtopic.php?f=5&t=75&p=181#p181](http://uberstudent.com/phpBB/viewtopic.php?f=5&t=75&p=181#p181) may be useful and is much more straightforward and does not involve recompiling packages or removing components of XFCE.

---

### Post by oldos2er on 2012-12-05
Old thread closed.

---

