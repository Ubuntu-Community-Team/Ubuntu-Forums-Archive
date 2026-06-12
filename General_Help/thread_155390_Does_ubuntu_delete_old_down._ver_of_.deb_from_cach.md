---
title: "Does ubuntu delete old down. ver of .deb from cache?"
date: 2006-04-05
forum: General Help
---

### Post by jaja23bd on 2006-04-05
hi
 I would like to know that 
 Does ubuntu delete old version of deb package from local cache when its download new version (such as smb)
    /var/cache/apt/archives
  also 
  If i save some files in other folder and after new installation can i use them 

  or can i use that folder as a repository in Synaptic such as acrobat.
  Regards
  jaja
  ............
  Dapper drake flight 6

---

### Post by waster on 2006-04-05
a quick look in /var/cache/apt/archives shows that old versions are kept. You can configure apt to remove old/all downloaded files.

not sure of name, but you can use a package to create a repo from a folder of debs. Or just use the new gdebi or command line to install your own debs.

---

### Post by getglenn on 2006-04-05
I too, have been trying to come to grips with APT/Synaptic and want to create a LOCAL REPOSITORY to store packages and then put them on CD/DVD to install an other PCs...

Synaptic has the following options in --> Preferences --> Files...

[INDENT]- Leave all downloaded packages in the cache
- Delete downloaded packages after installation
- Only delete packages which are no longer available[/INDENT]

I prefer to "Leave all downloaded packages in the cache" , mainly 'cos i dont have a speedy internet connection... If i stuff-up something, and have to do a re-install, i dont want to have to download packages again.

Synaptic also has options under --> Repositories --> Software Preferences --> Settings --> Temporary Files which seems to duplicate the options in "Preferences"

Havent checked to see if they are "synched" tho.

APT-MOVE is one way to create a local repository, another uses "dpkg"

I looked at the instructions and put the task aside until i can "absorb" them.


i hope some of this helps

PS i have no idea why the HOWTOs i have read suggest complicated ways to create a LOCAL repostitory or mirror...

why not just use /var/cache/apt/archives???

all the DOWNLOADED packages to INSTALL go are there, why not leave everything there??

...just copying the .deb files into /var/cache/apt/archives doesnt work!! Synaptic doesnt see them!???

i have had no luck editing the sources.list, to point to the .deb files either, hope you have better luck

---

### Post by iamkrazee on 2008-06-17
> **waster said:**
> not sure of name, but you can use a package to create a repo from a folder of debs. Or just use the new gdebi or command line to install your own debs.

It's AptOnCD. It's in the repo. Sorry for the ultra late reply.

---

