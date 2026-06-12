---
title: "E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong"
date: 2009-11-09
forum: General Help
---

### Post by micio8 on 2009-11-09
Hi,

trying to install from cd rom on ubuntu but:

E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?

what can i do?

---

### Post by Bunnybugs on 2009-11-09
Well, you have to shutdown your computer, and start it up with the disk inside...

The BIOS will pick up your CD and give you a menu...

The packages on the disc are unknown to your old Ubuntu system, so it refuses to use the packages...

I think that you should wait with rebooting/upgrading your system untill it's more stable, or just update from the updatemanager (System>Administration>Update Manager)

---

### Post by snowpine on 2009-11-09
Not a lot of details to go on, but I'd recommend:

1) Read this guide (if you haven't already) [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

2) use the "check disk for defects" option on the initial screen

3) use the Search feature on these forums to find other users with the same hardware, maybe others have had the same problem

---

### Post by mechro on 2009-11-09
> **micio8 said:**
> Hi,

trying to install from cd rom on ubuntu but:

E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?

what can i do?

Explain again what you are trying to do. Are you trying to install packages from a Ubuntu CD to your Ubuntu system?

---

### Post by khelben1979 on 2009-11-09
Which method are you using when you're trying to install from the cd-rom? For example: are you just double clicking on the package files or are you using the [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager")?
[I]
Note that you need super user priviliges to be able to install packages on the system.[/I]

---

### Post by Bunnybugs on 2009-11-09
He tries to get the Karmic packages straight from the disc, he already burned the ISO file...

Synaptic doesn't recognize the disc as debian, because the packages are not supported by jaunty...

If he had some kind of update disc, instead of a brandnew bootable OS disc, it would have worked... but the disc is made to install a new OS to the system, not for updating an older version

---

### Post by micio8 on 2009-11-09
when i clicl on .exe

Archive:  /media/cdrom0/M263-setup.exe
[/media/cdrom0/M263-setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/M263-setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/M263-setup.exe or
          /media/cdrom0/M263-setup.exe.zip, and cannot find /media/cdrom0/M263-setup.exe.ZIP, period.

????

---

### Post by mechro on 2009-11-09
.exe??

Windows application??

Might run in Wine or Virtual Box, but plain Ubuntu can't do anything with it.

---

### Post by micio8 on 2009-11-09
[I]

I have tried both synaptic and double click but....
[/I]

---

### Post by Bunnybugs on 2009-11-09
The wubi installer is created to install a dual boot, from within windows...

this doesn't work on Ubuntu itself...

.EXE files are programs, designed to be used with OS like windows... not Ubuntu...

You have to go to Update Manager (System>Administration>Update Manager), Check your updates a couple of times, and there will be a bar that says New Distribution Release '9.10' Is Available, with a button next to it that says 'Upgrade'...

Click that button, and the upgrade will start!

Follow the onscreen instructions, and everything will be fine!

If the message doesn't appear, go to System>Administration>Software Sources, go to the 'Updates'-tab, and almost at the bottom of the screen is a header that says: Release Upgrade, With it is a dialog-box with 3 options: Never, Normal Releases, Only Long term support releases.... Make sure that the 'Normal Releases' function is enabled, and try the update manager again (don't forget to reload all packages when it asks you to do that!

---

### Post by wojox on 2009-11-09
You need to go download the .iso and burn it to a disk. There are no Exe's here. And it's not wubi either.

---

### Post by Bunnybugs on 2009-11-09
> **wojox said:**
> You need to go download the .iso and burn it to a disk. There are no Exe's here.

Why should he burn a whole new disc, if he's just trying to upgrade his distro??

---

### Post by wojox on 2009-11-09
> **micio8 said:**
> Hi,

trying to install from cd rom on ubuntu but:

E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?

what can i do?

Where does it state he's upgrading his system?

---

### Post by mechro on 2009-11-09
> **Bunnybugs said:**
> Why should he burn a whole new disc, if he's just trying to upgrade his distro??

Where has he/she said they are upgrading?

Edit: Snap!

---

### Post by micio8 on 2009-11-09
It was update an hour ago.....however ive checked it again there are not update available.....as the OS is update

---

### Post by Bunnybugs on 2009-11-09
Well, the E:blablabla tells me that he's upgrading;)

I have a DVD with karmic, but booted Jaunty back on my Laptop, and every time i close the disctray, it gives me that message....

If i pull it into the vista PC of my GF, it doesn't give me that message... so guess what:o he's trying to upgrade:O

There is no other explanation for putting and Karmic disc into a Jaunty system, or is there?:o

And didn't I tell him/her already how to install a new Ubuntu, while leaving the old one for what it is?:o

Ow, I did:p

Edit: And why i put the karmix disc into my laptop? I'm a little short in CD/DVD boxes xD So I won't let it get scratchy!

---

### Post by Bunnybugs on 2009-11-09
Blaaaaaaaablabla:)

Tnx for the comment guys, 

But didn't this person made the point clearly?:D

---

### Post by wojox on 2009-11-09
E: is error not E: Drive

---

### Post by mechro on 2009-11-09
> **Bunnybugs said:**
> 

But didn't this person made the point clearly?:D

Er... No... remember, some of us are old and senile and find it difficult to process information. :D

---

### Post by mechro on 2009-11-09
[IMG]http://i38.tinypic.com/15cj0jb.jpg[/IMG]

---

