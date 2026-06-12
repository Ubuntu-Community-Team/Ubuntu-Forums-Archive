---
title: "Remastersys alternate or install solution????"
date: 2010-01-14
forum: General Help
---

### Post by studmf on 2010-01-14
Hi all as looking at a recent article on Ubuntugeek.com concerning Remastersys [Found [HERE]("http://www.ubuntugeek.com/create-custom-ubuntu-live-cd-with-remastersys-in-karmic.html")].  I tried to install and ran into an issue, output 

[PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  remastersys: Depends: ubiquity but it is not going to be installed
E: Broken packages[/PHP]I do not necessarily need to install this program; however, I would like to make an exact backup of my current OS and setup to include themes, icons, programs...well, everything.  Any help is greatly appreciated, what will the Backup Tool in the control panel do...what I want?

---

### Post by quixote on 2010-01-16
I struggled for weeks with that very issue.  Remastersys is the only thing that will supposedly mirror your install, but in my case it wouldn't work on any computer I tried it on (three different laptops, a Dell, an MSI, and an HP Mini 311).  I spent a couple of weeks on the forums, very helpful people, but still no luck.

The only thing that works for me is to use [Clonezilla]("http://clonezilla.org/") to make an image of your root partition and at least the hidden files and dirs in your home directory since you want to keep your customized settings.  It's easiest to use if you have a USB hard drive that you can put backups on.  You'd probably want the single user "Clonezilla live".

(My install doesn't have the "Backup Tool" so I'm not sure what it'll do for you.  If it'll mirror your install, let me know!)

---

