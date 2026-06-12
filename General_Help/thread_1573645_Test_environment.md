---
title: "Test environment"
date: 2010-09-13
forum: General Help
---

### Post by asemoon on 2010-09-13
recently I have been playing around with packages and packaging stuff a lot and I've messed up with my Ubuntu couple of times, I wonder if you could give some hints so I could setup a test environment .as a result if I mess up again I could revert to my previously working system again.I already install my compiled programs using checkinstall to make it easier to install and remove softwares and I know about chroot too.
for example I want to compile gstreamer and its plugins from scratch so I have to remove the installed packages coming from ubuntu repositories and a lot of programs already rely on gstreamer so If I remove them all and install my newly compiled gstreamer and if it doesn't work I endup with a mess!and that point it would be a great relief to be able to go back to time when everything was working or setup a test environment for these tests.

---

### Post by sikander3786 on 2010-09-13
I will advise you to run a testing environment in a Virtual Machine. I prefer VirtualBox.

Search for VirtualBox OSE in Software Center and install from there. There is also a close source edition available on the VirtualBox website.

Install your desired OS in Virtualbox. You can play with lots of OS there and it doesn't cause your host OS to go down or get corrupted. Post back if you've got any queries.

---

### Post by nothingspecial on 2010-09-13
I have 2 linuxes on every computer.

On my netbook at the moment, I have Ubuntu and Xubuntu.

I use Xubuntu day to day and don`t mess with it. If however I want to mess about and try some stuff, I boot Ubuntu.

I have a /home partition so both instalations have exactly the same home directory.

If I add a firefox bookmark in one, it`s there in the other. If I update my music library in one, it`s updated in the other etc

However, apart from my files and user settings (ie the contents on my home), everything else is completely seperate. I have different packages on both systems, different sources lists. 

The thing is, if I totally mess up Ubuntu, critically, then Xubuntu is fine.

---

