---
title: "Problem installing Gnome Commander and Tux Commander on 12.04.1"
date: 2012-10-13
forum: General Help
---

### Post by dragonfly41 on 2012-10-13
Having used Total Commander in windows (I still have a dual boot configuration) it was natural to use Gnome Commander in Ubuntu.  I tried Midnight Commander and others on Ubuntu 10.10 but Gnome Commander was my preferred choice.

Now in Ubuntu 12.04 (a recent upgrade from 10.10 through intermediate upgrade paths, 11.04, 11.10) I again go to Ubuntu Software Upgrade to install Gnome Commander in Ubuntu 12.04.1.

But this time on installing I hit this popup message ..

[COLOR=Navy]Gnome Commander
CD/DVD 'Ubuntu 12.04.1 LTS_Precise Pangolin_-Release i386(201208.17.3)' is required.
Please insert the above CD/DVD into the drive /cdrom/ to install packages from it.[/COLOR]

I'm surprised that a CD is required by Ubuntu Software Center but when I rummage around to find one (not sure if it is the correct release date) I place it in CD reader to continue and the installation crashes.

As a next best option I try to install Tux Commander 

 "tuxcmd - Tux Commander, a GTK2 based File Manager"

but after installing it doesn't launch from the Applications > Accessories menu where it is listed.

So I try [COLOR=Navy]man tuxcmd[/COLOR] command and that works.

Next I try a command line launch

[COLOR=Navy]sudo tuxcmd
An unhandled exception occurred at $B70168EE :
EAccessViolation : Access violation
  $B70168EE
  $B701F453

An unhandled exception occurred at $540A303D :
EAccessViolation : Access violation
  $540A303D
  $0811B9BF
  $08111802
  $08111C19[/COLOR]


To my question:

Are there any (perhaps Gnome) dependencies for Gnome Commander and Tux Commander I need to pre-install in Ubuntu 12.04.1 before installing Gnome Commander and Tux Commander?

---

### Post by dragonfly41 on 2012-10-13
Partly solved ..

The Tux Commander access violation in 12.04 I report above is confirmed here ..
[https://apps.ubuntu.com/cat/applications/precise/tuxcmd/reviews/](https://apps.ubuntu.com/cat/applications/precise/tuxcmd/reviews/)

However on same page this reviewer suggests a solution .. which launches Tux Commander GUI.
[INDENT][COLOR=Navy]If you get the error with access violation when starting tuxcmd in Ubuntu 12.04, try
 $ sudo LIBOVERLAY_SCROLLBAR=0 tuxcmd
instead. I just put this line into a script named 'tux' (not tuxcmd!) in usr/bin/ and made it executable (sudo chmod 777 tux). Then simply call tux.[/COLOR]
[/INDENT].....................................................................................................................................................

Now .. is there a similar'fix' for Gnome Commander to allow it to be installed?

---

### Post by dragonfly41 on 2012-10-13
I've now installed Synaptic Package Manager and tried again to install Gnome Commander.   This is the error report I get.  However if I try testing one or two of these *.deb links in firefox I can manually download them. What can be preventing them being fetched?

[INDENT][COLOR=Navy]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libb/libbonobo/libbonobo2-common_2.32.1-0ubuntu1.1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libb/libbonobo/libbonobo2-common_2.32.1-0ubuntu1.1_all.deb)[/COLOR]

[COLOR=Navy]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libb/libbonobo/libbonobo2-0_2.32.1-0ubuntu1.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libb/libbonobo/libbonobo2-0_2.32.1-0ubuntu1.1_i386.deb)[/COLOR]

[COLOR=Navy]W: Failed to fetch cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/pool/main/libg/libglade2/libglade2-0_2.6.4-1ubuntu1.1_i386.deb[/COLOR]

[COLOR=Navy]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs/libgnomevfs2-common_2.24.4-1ubuntu2.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs/libgnomevfs2-common_2.24.4-1ubuntu2.1_i386.deb)[/COLOR]
[COLOR=Navy]  [/COLOR]
[COLOR=Navy]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs/libgnomevfs2-0_2.24.4-1ubuntu2.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs/libgnomevfs2-0_2.24.4-1ubuntu2.1_i386.deb)[/COLOR]
[COLOR=Navy]  [/COLOR]
[COLOR=Navy]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgnome/libgnome2-bin_2.32.1-2ubuntu1.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgnome/libgnome2-bin_2.32.1-2ubuntu1.1_i386.deb)[/COLOR]
[/INDENT][INDENT][COLOR=Navy]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgnome/libgnome2-0_2.32.1-2ubuntu1.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgnome/libgnome2-0_2.32.1-2ubuntu1.1_i386.deb)[/COLOR]
[COLOR=Navy]  [/COLOR]
[COLOR=Navy]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-common_2.30.3-1ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-common_2.30.3-1ubuntu1_all.deb)[/COLOR]
[COLOR=Navy]  [/COLOR]
[COLOR=Navy]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-0_2.30.3-1ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-0_2.30.3-1ubuntu1_i386.deb)[/COLOR]
[COLOR=Navy]  [/COLOR]
[COLOR=Navy]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libb/libbonoboui/libbonoboui2-common_2.24.5-0ubuntu1.1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libb/libbonoboui/libbonoboui2-common_2.24.5-0ubuntu1.1_all.deb)[/COLOR]
[COLOR=Navy]  [/COLOR]
[COLOR=Navy]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libb/libbonoboui/libbonoboui2-0_2.24.5-0ubuntu1.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libb/libbonoboui/libbonoboui2-0_2.24.5-0ubuntu1.1_i386.deb)[/COLOR]
[/INDENT]

---

### Post by dragonfly41 on 2012-10-14
I've not been able to solve these errors so I'm having to adopt Krusader as an alternative.  Krusader installed without errors.

---

### Post by Fajer on 2012-11-24
I have same problem with Tux Commander. I'm still looking for fix.

---

### Post by uriel1998 on 2013-09-24
> **Fajer said:**
> I have same problem with Tux Commander. I'm still looking for fix.

For those who haven't found the fix yet:

```
gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false
``` 

That's it.  If you want to run Tux Commander as root, then you need to run the above command as root as well.

---

