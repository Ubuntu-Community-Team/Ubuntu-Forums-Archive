---
title: "Flashplayer"
date: 2009-12-04
forum: General Help
---

### Post by Stepho_62 on 2009-12-04
Ok. I'm really gettin pissed now.

I used the "janitor" app the other day n inadvertently clicked on the line that said that flash player "hasn't been used for some time"  What ********!  

I've now inadvertently deleted flashplayer but of course it won't reinstall cleanly.  

Someone please help.  I'm seriously considering buying a copy of windows 7

Additionally I need help with this too.

[http://ubuntuforums.org/search.php?searchid=67868073](http://ubuntuforums.org/search.php?searchid=67868073)

---

### Post by MelDJ on 2009-12-04
what error comes up when you try to reinstall flash?

---

### Post by Johnny B on 2009-12-04
echo "Removing any other flash plugin previously installed:"
# sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
# sudo rm -f /usr/lib/mozilla/plugins/*flash*
# sudo rm -f ~/.mozilla/plugins/*flash*
# sudo rm -f /usr/lib/firefox/plugins/*flash*
# sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
# sudo rm -rfd /usr/lib/nspluginwrapper

---

### Post by Stepho_62 on 2009-12-05
Johnny,

Thanks for that.

Sorry to sound like a dunce but I'm assuming that you run this from the Terminal thingy?

Do I just cut n paste the script that you have given me?

Thanks for your patience,

Stepho.

---

### Post by MelDJ on 2009-12-05
yes except  		echo "Removing any other flash plugin previously installed:"

---

### Post by 3rdalbum on 2009-12-05
> **Stepho_62 said:**
> 
Additionally I need help with this too.

[http://ubuntuforums.org/search.php?searchid=67868073](http://ubuntuforums.org/search.php?searchid=67868073)

Sorry, no matches.

Also with that script that was posted, you need to get rid of the "#" symbols.

---

### Post by Stepho_62 on 2009-12-07
All,

Thanks for your responses.  I tried the script as suggested, cutting and pasting into Terminal on an individual basis and removing any # marks.

I got this result.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
boss@boss-laptop:~$

I tried to run the subsequent script line by line n got nothing.

Please help, I just want my flashplayer stuff to work.

Incidentally, I noticed that even tho I subscribed to this thread its not listed as a subscription.  Go figure :D

---

### Post by wojox on 2009-12-07
Here you go Boss:

```

#Remove Flash
# Deletes a troublesome config file
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
# Force-reconfigures adobe-flashplugin
sudo dpkg-reconfigure adobe-flashplugin --force
# Force-removes adobe-flashplugin
sudo dpkg --purge --force-all adobe-flashplugin
# Installs flashplayer the easy way
sudo apt-get install flashplugin-nonfree


```

---

### Post by Stepho_62 on 2009-12-07
Wojox,

I'm getting warmer.  :)

I was going really well until this happened.

boss@boss-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnss3-dev libnspr4-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.4kB of archives.
After this operation, 229kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  flashplugin-installer flashplugin-nonfree
Install these packages without verification [y/N]? y
0% [Connecting to au.archive.ubuntu.com (32.1.3.136)]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/multiverse flashplugin-installer 10.0.32.18ubuntu1
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/multiverse flashplugin-nonfree 10.0.32.18ubuntu1
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.32.18ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.32.18ubuntu1_i386.deb)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.32.18ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.32.18ubuntu1_i386.deb)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Can I just re install it from the Adobe sight?

---

### Post by Stepho_62 on 2009-12-07
and I'm unashamedly bumping this too  :D

[http://ubuntuforums.org/showthread.php?t=1340824](http://ubuntuforums.org/showthread.php?t=1340824)

---

### Post by Stepho_62 on 2009-12-08
Ok, I'm guessing from below that the archive here downunder in Oz is unreachable or the archive is corrupt.

Can someone please confirm this and give me an alternative?

Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/multiverse flashplugin-installer 10.0.32.18ubuntu1
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/multiverse flashplugin-nonfree 10.0.32.18ubuntu1
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.32.18ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.32.18ubuntu1_i386.deb)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.32.18ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.32.18ubuntu1_i386.deb)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

