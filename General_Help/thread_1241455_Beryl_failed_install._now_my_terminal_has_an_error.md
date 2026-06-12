---
title: "Beryl failed install. now my terminal has an error...HELP!"
date: 2009-08-16
forum: General Help
---

### Post by zkriesse on 2009-08-16
Hey all, I tried not to long ago to install Beryl just to give it a try. It couldn't install and now when I run sudo apt-get update my Terminal comes back with an error. Here it is. 

Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages
  404 Not Found [IP: 88.191.250.18 80]
Fetched 1B in 1s (1B/s)  
W: Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages](http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages)  404 Not Found [IP: 88.191.250.18 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
zach@zach-laptop:~$ 

How can I fix that? And, when I try to install Ubuntu Restricted Add-ons it can't install because of a package error. Says that something that I installed is conflicting with that...HELP PLEASE!

---

### Post by SoftwareExplorer on 2009-08-16
It means that your computer wasn't able to connect to the beryl repository. 
Is there a good reason that you are trying to run beryl and not compiz? Compiz is the up-to-date version of beryl and can be installed in ubuntu without having to add any software sources/repositories. It does all the stuff beryl did and is easier to install.

To take the beryl souftware source off so that you don't have the error anymore, go to System->Administration->Software Sources. Go to the third party software tab and uncheck the entry for beryl. Close the window and It will ask if you want to reload the package information. Go ahead and do that and the problem should be fixed. If you want help setting up compiz let me know, it's my favorite linux program by far.  :)

---

### Post by zkriesse on 2009-08-16
Hey man thanks...! and yes...compiz help would be nice....

---

### Post by SoftwareExplorer on 2009-08-17
> **Zachk18 said:**
> Hey man thanks...! and yes...compiz help would be nice....
You welcome. I was in almost the same spot a year and a half ago. I was trying to compile beryl on Debian as a linux noob and to say the least it didn't work. Then I found out what I really should be trying to get to work was Compiz Fusion and that ubuntu had it installed by default. The rest is history.
OK, enough chat, on to compiz help. First, I would go to the Add / Remove Applications and search for ccsm. Make sure that 'Show' Is set to All available applications. Check Advanced Desktop Effect settings. Apply the changes. (This will install a tool to let us configure compiz.) 
Go to System->Administration->Hardware Drivers and see if there are any that need to be installed.
Go to System->Preferences->Appearance. Go to the visual effects tab and try setting it to normal or extra. If it works, you now have compiz running. Next, tell me what effects you want and I'll tell you how to turn them on or set them up.

---

### Post by zkriesse on 2009-08-17
Thanks for the info but I decided to not go and add that stuff. Just finished re-loading my system...trying to not junk up my hd with extra stuff I really don't need. Thanks again. But! Do you know how to mark a thread as solved?

---

### Post by SoftwareExplorer on 2009-08-17
Well, there used to be an option to mark it as solved, but it took to much server power or something so they took it off. Now you are supposed to edit the title or something, but I haven't figured that out yet.

---

### Post by zkriesse on 2009-08-17
Ok, thanks man.

---

### Post by SoftwareExplorer on 2009-08-17
> **Zachk18 said:**
> Ok, thanks man.
You're welcome. And I like your signature.

---

### Post by zkriesse on 2009-08-19
Awesome...

---

