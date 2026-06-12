---
title: "Installing Kubuntu on 100 identical computers - The fastest way?"
date: 2006-04-14
forum: General Help
---

### Post by daller on 2006-04-14
Hi There,

Working on a project for an African community.

We are going to ship 100 computers to them (for education) - And they should be as cheap as possible. (No licenses)

Therefore we install Kubuntu!

I do NOT want to connect every computer to the internet, and use over an hour to install on each computer!

What do I do?

---

### Post by gingermark on 2006-04-14
Wouldn't it be possible to mirror the harddrives?

Depending on each motherboard's capacity (assuming the PCs are identical) you could plug say four of the harddrives into one PC, and then maybe use RAID when installing? I'm just guessing here. Sorry. But to my mind you'd only have to install on 25 PCs in that case.

You can also create a CD for additional sources (like multimedia stuff for example, as well as updates). This would speed up the process considerably. There was a post (or maybe a wiki page) on this that I remember reading, but I can't find it. Best I could find was this: [http://ubuntuforums.org/showthread.php?t=16757](http://ubuntuforums.org/showthread.php?t=16757)

I'm just putting forward a couple of ideas, I don't know for certain, so feel free to tell me where to go :)

Good luck!

---

### Post by Paulo Wageck on 2006-04-14
if all computers are the same...
clone the hd after install and customizing.... and save the image in a serial manner... only with one computer...
maybe 1 source and 3 destinations at a time...
after... put the hdds at the computers....


what about thin clients? remote xwindow session????

---

### Post by fdoving on 2006-04-14
You could try: [http://www.partimage.org/](http://www.partimage.org/)

---

### Post by Al3xanR0 on 2006-04-14
[QUOTE=fdoving]You could try: [http://www.partimage.org/](http://www.partimage.org/)[/QUOTE]

dd and or g4l comes to mind..

---

### Post by helfrez on 2006-04-14
I alway thought it would be nice to have a network install method of 2 flavors, 1 being a mini install disc similiar to debian netinst..benefit being u get the latest software from server without having to install then wait for all the updates to run...and 2 being a easy method for lan installation for distributed installs similar to kickstart for anaconda...I suppose one might be able to get really creative. 

You could for instance one one master box with ubuntu installed, boot all the other boxes onto the network with a live cd and use the live cd to export the local drive to say a master machine via nfs or something
then u could run a debootstrap from the master box into the filesystem remotely...you would still need to do some network updates though, but at least u can processes more than one box at a time...otherwise ur gonna have to go the partimage route or just clone the drives...as it stands without getting jazy with maybe pxe booting a cd filesystem or something, there is no predefined method for network installs of ubuntu...If I get a chance later..I will see how hard it would be to setup say a tftp server and pxe boot the installation filesystem...i think I have seen reference to that in the forums before...good luck

---

### Post by daller on 2006-04-14
About PartImage,

Do I understand it correctly, if it just creates an archive with the whole filesystem?

Does it also create a bootable cd, so that "restoring" (on another machine) is possible? - Very easily?

If so, I really love PartImage - Seems nice!

---

### Post by Lin-X on 2006-05-03
If you want to create a bootable rescue cd or dvd, Mondo is your game. I think it is installed in Dapper already. There were some problems with the last one (in Breezy) and it won't let me use it, but try it:
 just <sudo mondoarchive> and let us know. A complete and very helpful descrip-
tion of this is given in Carla Schroeder's Linux Cookbook. You could also try Partimage. I have been trying for a week to use it from a Knoppix cd but can't seem to get it to let me save an image. Anyway, those are two that, according to my ex-
tensive reading, seem to be favored and widely used. Good luck to you; it sounds 
like a great project.

---

### Post by yabbadabbadont on 2006-05-03
/me puts on asbestos firefighter suit

If you have it available, you could use Norton's Ghost.

---

### Post by CyberAngel on 2006-05-04
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

I had used some time ago the above System Rescue CD that it uses partimage to make ghost images and I had succesfully made a ghost of an slamd64 installation .
After that the restoration (again to my system after formating) had only one little problem :rolleyes: 
It was needed to run the lilo again [from a bootable linux disc. SystemRescueCD wasn`t working because gentoo (that it is based) had recognise my discs as hdx and slackware was recognised them as sdx (like ubuntu)] to fix the MBR that it wasn`t working after restoration..

Partimage has a feature to make backup of mbr too but I haven`t tried it yet because I didn`t know how to do it for sure :)

If anyone has more knowledge on that please let me know :)

---

### Post by Prospero2006 on 2006-05-04
Someone earlier mentioned ltsp. (Linux terminal server project) (Thin clients) This is how I would do it for sure.

Although you don't want all the computers connected to the internet, 
a setup where you have one master machine and a series of maybe 50 thin clients routed to it would save you thousands of dollars. Every machine you connect to the host computer using ltsb requires that the host machine have 64 megabytes of memory to manage it. The thin client would then need 512 at least, but the savings and ability to upgrade this kind of setup is well worth it. Want to go cheap? ltsp.

Pros

---

### Post by jonnymccullagh on 2006-05-05
Although I do not need to do anything like this at present I am wondering what I might do if I had installed 100 computers with Kubuntu or Ubuntu for that matter and I decide at some point to upgrade them all to a newer version (e.g. Dapper to Dapper+1).
If I did sudo apt-get upgrade on each machine it would go get it all from the internet so:
1. Would I be able to set up a local apt server
2. What if I just wanted to update 1 item of software on all machines at once - can that be done remotely and pushed out onto the 100 computers?

Just asking questions in case someone here asks me in future.
thanks,
jonny

---

### Post by MrSquishy on 2006-05-05
I do educational installs too, and I prefer to use free (better) tools.

_Partimage_ is what I use to do image backups to keep on file, and I use a great tool called UDP Cast to send them out to student labs.

_UDP Cast_ will do multicasting from a source drive to any client computer that is listening.
It goes fast too.  Uncompressed, I regularly hit speeds of 92Mbits/s, so I recommend doing it on an isolated network.

[http://udpcast.linux.lu/](http://udpcast.linux.lu/)

I make custom knoppix cds for backup tools.  Including the partimage file on disc to do an automated restore would be a piece of cake.  Assuming you had enough freespace for the image file to fit on the CD.

Another idea would be to partition the hard drive up so that there was a read-only copy of the image on the same drive, and a rescue CD would just copy the data over the "used" partition.

LTSP is definately awesome (had fun with a couple of those/k12ltsp), but I assume you already have the 100 boxes ready to go.

---

