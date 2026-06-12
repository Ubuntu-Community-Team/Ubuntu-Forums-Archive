---
title: "Help installing tar.gz?"
date: 2011-05-20
forum: General Help
---

### Post by Zibbsy on 2011-05-20
Hey everyone!
I'm new here but have been on ubuntu since 9.04.
I just upgraded from 10.10 to 11.04

I love it, except for the fact emesene 1.6.3 has been replaced with 2.11.4

I really would like emesene 1.6.3 back
I have downloaded the tar.gz file online and have no idea where to go from here.

Any help would be much appreciated

Thanks in advance! :D

---

### Post by hwttdz on 2011-05-20
You're going to need to extract that, and it will probably be either a deb or a directory containing a file named INSTALL or README.  If you read README or install it will probably tell you to run "./configure && make && sudo make install".  An alternative might be adding the 10.10 repo that contained the program you're looking for, and then going in to synaptic and setting that program to the desired version.  I think it's click on the package name, and the right click and something like force version...

---

### Post by Mr. Shannon on 2011-05-20
I don't use that software but I just downloaded it to see how to install it.  It is set up so you can extract it and then run it from the command line right there.  The way I will describe below is longer but will give you a system that will work more like other software in Ubuntu (except for updates).

The method below assumes that is was downloaded to the Download folder in your home directory.

Open a terminal using **Ctrl+Alt+t** and type
```

cd /usr/local/

sudo tar -xzf ~/Downloads/emesene-1.6.2.tar.gz

cd /usr/local/bin/

sudo ln -s /usr/local/emesene-1.6.2/emesene

```

now you can close the terminal.  At this point you can start emesen from the terminal.  Note: Uninstall the other emesene in the repository so you don't have naming conflictions, or rename **emesene** link you made in ```
/usr/local/bin/
``` to something else.

If you want a menu entry then make a custom application launcher using ```
/usr/local/emesene-1.6.2/emesene
```
for the command field.  For instructions on how to do this see: [http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html]("http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html") for GNOME.  For Unity see here: [http://itshouldbeuseful.wordpress.com/2011/05/05/create-a-custom-launcher-for-unity-in-ubuntu-11-04/](http://itshouldbeuseful.wordpress.com/2011/05/05/create-a-custom-launcher-for-unity-in-ubuntu-11-04/) and look at the first comment.

---

