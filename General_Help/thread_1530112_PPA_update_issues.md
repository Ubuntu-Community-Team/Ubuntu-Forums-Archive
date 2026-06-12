---
title: "PPA update issues"
date: 2010-07-13
forum: General Help
---

### Post by MorrisseyJ on 2010-07-13
Hi, 

I have some problems with updating and PPAs. I little while back i tried to get Empathy Gchat working. Somewhere i found a link to a site in which i could install some PPAs which would apparently get Gchat to work. 

In the end i think i installed the PPAs, but failed to get Gchat to work. I am now getting the following msg when trying to update my system:

> Failed to fetch [http://ppa.launchpad.net/http/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/http/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/launchpad.net/telepathy/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/launchpad.net/telepathy/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/ppa.launchpad.net/telepathy/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ppa.launchpad.net/telepathy/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.They are all PPA issues and so i am guessing this is a result of my fiddling with empathy. 

I have found a thread or two on this but they are too technical for me to understand. At the moment i am willing to scrap the Gchat stuff and so i could happily just remove/undo the PPA fiddling that i did. 

If anyone can tell me how to either remove what i have done - i can't remember exactly what it was - or tell me how to update these files, that would be very much appreciated.

---

### Post by hawthornso23 on 2010-07-13
Look in 

System - administration - software sources

and disable or delete the ppa's you no longer want. That'll get rid of the messages. 

If you want to get rid of the software they installed you might need to do that through synaptic.

---

### Post by MorrisseyJ on 2010-07-13
Thanks, that is useful.

I didn't really know what i was doing when i started fiddling with the PPAs so this may be an embarrassing question. 

Do you have any idea if i can find out what i installed when i put them on (if that is the correct verb for a PPA) so that i can remove that software?

Thanks

---

### Post by hawthornso23 on 2010-07-13
System - administration - Synaptic package manager

On the left hand side down the bottom click the button that says 'Origin'. You'll see a list of software sources which should include the ppas. Click on one of them and the right hand pane will show the packages provided by that ppa.

---

### Post by MorrisseyJ on 2010-07-13
Thanks for the help, but i think i am still missing something.

I only have one item in the left panel (with 'Origin' checked') which mentions PPA.

This is:

> LP-PPA-jason-scheunemann/lucidThis, however, is not one of the PPAs for which i am having problems updating and i can use the associated software without a problem.

The rest of the things in the left panel are:
> lucid-updates/main (no.archive.ubuntu.com)
lucid-updates/multiverse(no.archive.ubuntu.com)
lucid-updates/restricted(no.archive.ubuntu.com)
lucid-updatesuniverse(no.archive.ubuntu.com)
Lucid/main (no.archive.ubuntu.com)
Lucid/multiverse (no.archive.ubuntu.com)
Lucid/restricted (no.archive.ubuntu.com)
Lucid/universe (no.archive.ubuntu.com)
Stable/main (dl.google.com)Does this suggest that no software was installed with the new PPAs and all i need do is uncheck them from the software sources list?

---

### Post by MorrisseyJ on 2010-07-13
Ok, so i found the install command in my terminal. It seems that i had installed:

> telepathy-sofiasip 
telepathy-butterfly 
telepathy-idle 
libtelepathy-farsight0 
python-tpfarsight

I have removed them all in synaptic.

Strangely, according to my terminal, i only added the following repository:> ppa:[http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu)

Which i have now removed it from my software sources. Notably however, i only seem to have added one repository, yet i was getting error messages from 3 of them.

I have since unchecked the other two which were giving me problems and can update without a problem. Does anyone know what the other two repositories were for, or how they might have gotten there? 

Finally, is there anyway of knowing if i'll need them?

---

