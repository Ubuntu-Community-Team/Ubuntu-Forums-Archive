---
title: "PCMANFM - Sort order problem"
date: 2010-05-28
forum: General Help
---

### Post by rjb-356 on 2010-05-28
I'm running Ubuntu 10.04 and PCMANFM v0.9.5.  I'm having problems with sort order (I'm set on sort by Ascending, By Name and viewing Detailed List View).  I started using PCMANFM in Ubuntu 8.04 because of Nautilus's bad sorting order. Now I'm having this problem in PCMANFM

View the following images to see the sort order that is a occurring on my computer:

[http://mysite.verizon.net/resrmb94/MyWebsite/sort-order-problem-sample-1.png](http://mysite.verizon.net/resrmb94/MyWebsite/sort-order-problem-sample-1.png)

Notice where !-Hardware falls in the list.

[http://mysite.verizon.net/resrmb94/MyWebsite/sort-order-problem-sample-2.png](http://mysite.verizon.net/resrmb94/MyWebsite/sort-order-problem-sample-2.png)

Notice the Examples folders at the very bottom of the list?

Any help would be appreciated.  I'm don't understand what's happening.  This problem with PCMANFM is new to me.

RJB

---

### Post by dino99 on 2010-05-28
the latest into maverick is 0.5.2  :P

[http://igurublog.wordpress.com/downloads/mod-pcmanfm/](http://igurublog.wordpress.com/downloads/mod-pcmanfm/)

---

### Post by rjb-356 on 2010-05-28
Thanks dino99 for the quick response.  I went to the link suggested and found no reference to helping resolve the sort order problem mentioned in my first post.  On the other hand, the referenced mod looks like it adds some nice desirable functions.  But I'm really now focused on resolving my sort order problem.

---

### Post by Zill on 2010-05-28
rjb-356:  Sorting works fine for me with PCManFM v0.5.

I am not sure why you are using v0.9.5 as I cannot find this deb package listed in the Ubuntu repositories.  Have you used a package for a different distro or compiled this version from source?

I suggest you uninstall v0.9.5 and then reinstall the appropriate deb package (v0.5-x) for your Ubuntu version as detailed on the following webpage...
[URL="http://packages.ubuntu.com/search?keywords=pcmanfm"]
http://packages.ubuntu.com/search?keywords=pcmanfm[/URL]

---

### Post by DoctorBho on 2011-05-25
I'm with the newer version on my netbook (Linux Mint Debian edition, though, and usually using LXDE).

No settings were saving at all (wallpaper, sort order, sort type, etc).

I solved it by copying the .conf file from the ~/.config/pcmanfm/LXDE folder to:

~/.config/pcmanfm/pcmanfm.conf

That is, up one level.

Irritatingly, I now have three slightly different versions of that file: there, and in the default and LXDE folders.

I am calling this a bug...

---

### Post by linuxinstalledfromhdd on 2011-05-25
I have installed PCManFM 0.9.7

And I use it all the time to sort. 

Just click on View and then Sort Files. 

Is that what you mean?

---

### Post by DoctorBho on 2011-05-25
I'm on version 0.9.5, like the original poster.

In a nutshell, on my machine, this version starts up in icon view with some bizarre sort order, while the menu option indicates Name, Ascending.

Changing away from the "Name" option seems to free it up, so you can do what you want and if you then switch back to "Name" it sorts correctly - but this is not persistent. If you shut down PCManfm and reopen, you are back to square one.

Wallpaper changes didn’t save either, or default view (I prefer compact...).

Copying the conf file one level up solved this on my machine, but maybe 0.9.7 has fixed this problem. I will have to see if it is in the repos as an update - it wasn’t two days ago (Mint Debian Testing).

I never had this problem with 0.5.

---

### Post by linuxinstalledfromhdd on 2011-05-25
When I install a pure openbox environment, I still use pcmanfm 0.5. I still use it when I need it. If somebody wants to write a better version, go for it. It's not a bug issue afaik.

---

### Post by DoctorBho on 2011-05-25
The hard core solution:

[http://lists.debian.org/debian-knoppix/2011/01/msg00008.html](http://lists.debian.org/debian-knoppix/2011/01/msg00008.html)

Used after an update killed my hack above...

---

