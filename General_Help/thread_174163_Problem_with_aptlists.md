---
title: "Problem with apt/lists"
date: 2006-05-11
forum: General Help
---

### Post by Isoss on 2006-05-11
I am getting this error when running software update:

The following problems were found on your system:
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)


This doesn't really exist in the apt/lists ... and it's kinda halting everything I try to install ... any clues guys?
thanks

---

### Post by Dr. Nick on 2006-05-11
[quote=Isoss]I am getting this error when running software update:

The following problems were found on your system:
W: Couldn't stat source package list [http://theli.free.fr]("http://theli.free.fr") ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)


This doesn't really exist in the apt/lists ... and it's kinda halting everything I try to install ... any clues guys?
thanks[/quote] 
Look in the file /etc/apt/sources.list and delete the refrence If you dont want it. then re-run apt-get update. If you want it this is the correct line to use, pulled from my sources.list and modified for breezy I think

deb [http://theli.free.fr/packages/_breezy_obsoltete/]("http://theli.free.fr/packages/_breezy_obsoltete/") ./

If you have already removed it then just try apt-get update

---

### Post by Zdravko on 2006-05-11
I have the same problem. I found a "sources.list" generator in Ubuntu's web site. I followed the instructions to overwrite the old contents. Then I started Synaptic... and I got about 10-15 W's :( But my list should be clean, now, uhm?

---

### Post by Dr. Nick on 2006-05-11
[quote=Zdravko]I have the same problem. I found a "sources.list" generator in Ubuntu's web site. I followed the instructions to overwrite the old contents. Then I started Synaptic... and I got about 10-15 W's :( But my list should be clean, now, uhm?[/quote]

run > cat /etc/apt/sources.list from a terminal and post the output here if you want someone to review it.

---

### Post by Zdravko on 2006-05-11
I found a sollution - I did "sudo apt-get update".
And then - voila! No more errors or warnings.
But yes - I will post the sources.list here - if there is something bad, tell me :)
> 
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse


---

### Post by Isoss on 2006-05-11
GUYS I accedently removed all the contents of /var/lib/apt/lists/ including partial!!! what can I do? update is not working and it keeps prompting that partical wasn't found!!!! 

Please help .. that was something very stupid I know ... but things just happen and hope I can get a help soon.

---

### Post by Dr. Nick on 2006-05-11
[quote=Zdravko]I found a sollution - I did "sudo apt-get update".
And then - voila! No more errors or warnings.
But yes - I will post the sources.list here - if there is something bad, tell me :)[/quote]

Looks fine, you can comment out the src lines if you wish, unless you ever compile from souce. It really wont matter to much though

---

### Post by Dr. Nick on 2006-05-11
[quote=Isoss]GUYS I accedently removed all the contents of /var/lib/apt/lists/ including partial!!! what can I do? update is not working and it keeps prompting that partical wasn't found!!!! 

Please help .. that was something very stupid I know ... but things just happen and hope I can get a help soon.[/quote] 
Just remake the folder from a terminal, try ```
sudo mkdir /var/lib/apt/lists/partial
``` My partial folder is empty so it shouldn't be a problem just to make a new one. After that try to re-run apt-get update

---

### Post by Isoss on 2006-05-11
Alright, everything is back on track ... I did that before you tell me and created one but it just wouldn't prompt that same error, so I reinstalled my repositories with synaptic and everything went fine.

---

