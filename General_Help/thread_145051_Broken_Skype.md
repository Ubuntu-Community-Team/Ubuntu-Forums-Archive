---
title: "Broken Skype"
date: 2006-03-15
forum: General Help
---

### Post by shiznatix on 2006-03-15
Ok so I installed skype (I thought) but I get a error on the update manager and when I goto 'synaptic package manager' it says that the broken package is skype. When I run skype from the command line there are no problems.

Sorry if this has been answered before but my search turned up nothing. I am right now running skype and talking to friends so I don't see how it is 'broken' in any way.

Edit: I just upgraded to breezy last night so I don't know if that means anything. Also I am not a *complete* beginner but I don't know my way around many things. If you spell it out for me that would be very helpful.

---

### Post by arnieboy on 2006-03-15
[QUOTE=shiznatix]Ok so I installed skype (I thought) but I get a error on the update manager and when I goto 'synaptic package manager' it says that the broken package is skype. When I run skype from the command line there are no problems.

Sorry if this has been answered before but my search turned up nothing. I am right now running skype and talking to friends so I don't see how it is 'broken' in any way.

Edit: I just upgraded to breezy last night so I don't know if that means anything. Also I am not a *complete* beginner but I don't know my way around many things. If you spell it out for me that would be very helpful.[/QUOTE]
do the following:```

sudo apt-get -f install
```

---

### Post by shiznatix on 2006-03-15
well that definatly got rid of the error but, it also uninstalled my skype :) . I don't quite remember what tutorial I used to install skype but many of these that I have seen are just too complex and many people seam to have lots of trouble. Is there a 'idiots guide' to installing skype, command by command?

edit: this is what I get when I try to install skype through synaptic
> 
skype:

Package skype has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


edit2: also, arnieboy, thanks for all your other tutorials and tips on this forum about getting ubuntu up and running. if it was not for your tutorials I would never have stayed with linux in the first place. (been with Ubuntu for 5 days and hooked for life)

---

### Post by kaamos on 2006-03-15
Try this:

0) Uninstall other versions of skype

1) Download the .rpm package from skypes website to your desktop

2) Applications->Accessories->Terminal
```
sudo apt-get install alien
sudo alien -i Desktop/the_name_of_the_file.rpm
```

---

