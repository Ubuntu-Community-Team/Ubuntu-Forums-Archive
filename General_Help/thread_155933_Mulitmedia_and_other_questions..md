---
title: "Mulitmedia and other questions."
date: 2006-04-06
forum: General Help
---

### Post by doc_kamolly on 2006-04-06
I would like to know how can one operate movies and other multimedia on Ubuntu especially ones with divx, xvid and other formats??

Also, I don't have internet on my Ubuntu-PC, so I download the software from another computer, how can I make the OS recognize the packages I get from the other computer?? I transfer them by flashdisk.

My PC has Ubuntu only on it.

Please answer my questions.

Thank You.

---

### Post by jeremyk on 2006-04-06
Try either EasyUbuntu or Automatix. You can find both in the "3rd party projects" in the forum.

They can install all the necessary codecs and programs for a smooth multimedia experience in ubuntu (breezy).

---

### Post by nanotube on 2006-04-06
i will answer your second question first. :)
to install stuff as you say, you would download the .deb package (most likely from packages.ubuntu.com), then you can transfer it to your ubuntu machine with your flashdisk, and then run the following command:
```

cd directory/where/you/put/the/file
dpkg -i name_of_your_file.deb
```
that will install the package for you.
warning: some packages have dependencies that you may not have installed - in that case you would have to go and hunt for all the dependency .debs, too. that's why having a net connection and using apt-get is so much nicer :) but packages.ubuntu.com lists all the dependencies, so you can do that pretty easily, too.

now, for your second question:
first, you would want to install the w32codecs package, which contains all the fancy divx etc codecs. you get the .deb file from the seveas repository, here:
[http://users.lichtsnel.nl/~seveas/pool/extras/w32codecs_20050412-0.0_i386.deb](http://users.lichtsnel.nl/~seveas/pool/extras/w32codecs_20050412-0.0_i386.deb)
get this package to be able to play dvds:
[http://users.lichtsnel.nl/~seveas/pool/extras/libdvdcss2_1.2.9-0.0ubuntu0_i386.deb](http://users.lichtsnel.nl/~seveas/pool/extras/libdvdcss2_1.2.9-0.0ubuntu0_i386.deb)

Then, you would want to install the mplayer package, from here:
[http://packages.ubuntu.com/breezy/allpackages](http://packages.ubuntu.com/breezy/allpackages)
(choose the 386 or the 586 package, depending on your cpu). the mplayer one will have a bunch of dependencies... just try a dpkg -i, and it will tell you what's missing.

well, this oughtta get you started. but you really should consider connecting your ubuntu computer to the net - that will save you a lot of headache.

---

### Post by nanotube on 2006-04-06
[QUOTE=jeremyk]Try either EasyUbuntu or Automatix. You can find both in the "3rd party projects" in the forum.

They can install all the necessary codecs and programs for a smooth multimedia experience in ubuntu (breezy).[/QUOTE]

hmm... dont those require the use of the net, to download all the stuff? i never used either of those, but that has been my impression...

---

### Post by karthik085 on 2006-04-06
If you are a beginner, try Automatix. It can install multimedia codecs 
[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

Also, read more about Restricted formats. What to install for what codec, etc...
[https://wiki.ubuntu.com/RestrictedFormats#head-fda9cc5147253891fe3047263b82d787ab025bba](https://wiki.ubuntu.com/RestrictedFormats#head-fda9cc5147253891fe3047263b82d787ab025bba)

I am not sure of what you mean, when you say - how can the OS recognize the packages you get from other computer?
I am assuming, what type of packages you need to download?
If that's the case, .deb is the type you are looking for and you can install them by
sudo dpkg -i <Package Names>

---

### Post by doc_kamolly on 2006-04-06
Thanks Guys, very helpful.

I meant packages that I can't get from the net directly from linux.

Linux can't seem to find my modem.

Also, I have a Creative MUVO Nomad, and I want to get it's driver for UBUNTU, can you tell me where to find it?

You've been very helpful guys, THNX A BUNCH.

---

### Post by doc_kamolly on 2006-04-06
[QUOTE=nanotube]Then, you would want to install the mplayer package, from here:
[http://packages.ubuntu.com/breezy/allpackages](http://packages.ubuntu.com/breezy/allpackages)
(choose the 386 or the 586 package, depending on your cpu). the mplayer one will have a bunch of dependencies... just try a dpkg -i, and it will tell you what's missing.[/QUOTE]

What does dpkg -i mean??

You use it in package installation, and finding dependencies, am I right?

---

### Post by nanotube on 2006-04-06
for more information about dpkg, type "man dpkg" in a terminal, it will give you a help file, explaining all the command line options. the "-i" switch means "install", for example. :)

---

### Post by doc_kamolly on 2006-04-07
Thnx A Lot Guys!

---

