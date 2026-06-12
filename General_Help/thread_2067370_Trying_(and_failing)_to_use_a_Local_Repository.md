---
title: "Trying (and failing) to use a Local Repository"
date: 2012-10-06
forum: General Help
---

### Post by cainram on 2012-10-06
I've got a fresh install of Precise Pangolin. I was connected to the Internet during the installation but did not choose to download updates while installing. The computer is now offline and will stay that way. 

I've used debmirror to create a local repository of the Main and Universe repos.
I've added it to my software sources and ran apt-get update.
In the 'Software Sources' window on the Ubuntu Software tab I have unchecked all of the sources. In the Other Software tab I have unchecked everything except my local repository -> _file:///home/gill/ubuntuRepo precise universe main_.
When I check for updates I'm told none are available. When I try to install from the software center, the install button is grayed out. What am I missing? I know there are a few tutorials out there for creating keys to make my repo 'trusted' but I feel like there has to be a more elegant (easier) way to get the system to install software from this repo. I've done this before on an earlier version of Ubuntu, I just can't figure out what I'm missing. Any ideas?
I'm doing all of this in VirtualBox, if that makes a difference...

Thanks in advance...

Update - I went into the Software Sources and tried importing the Releases.gpg file and got an error saying that it is either corrupt or not a gpg file...
I also tried installing a package from the local repository directly (the 'synaptic' .deb) and it opened in Software Center but, again, the Install button was gray.

---

