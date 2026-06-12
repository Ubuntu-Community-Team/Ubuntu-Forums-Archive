---
title: "Places Menu Paths"
date: 2009-09-22
forum: General Help
---

### Post by Zelandeth on 2009-09-22
Figured it was about time that I did something about this...

Is there any way that you can change the default paths of the Pictures, Music, Documents and such items in the places menu?

This is a relevant question both for my main PC running Hardy, and my netbook (EeePC 4G) running Jaunty UNR.

In the case of the Eee, with only 4Gb worth of space to play with - needless to say, everything aside from the OS and the software itself lives on an 8Gb SDHC card.  This is something I'd like to have the menus and such reflect - so that rather than pointing to /home/user/pictures for example, it'd point to /media/volumename/pictures instead.

My PC suffers from a similar issue, in that my documents folders are in an imaginatively named partition called "Stuff" on a separate physical drive to Ubuntu.  Surprise surprise, the other partition on that drive contains Vista (which hasn't been started up in months...) and is equally imaginatively named as "System."  Ideally, I'd like to have the menu items pointing towards /media/stuff and the relevant folders in there.

So, my two questions.

A: Is there a way to do this?

and 

B: Is there an easy way to do this?

---

### Post by blur xc on 2009-09-22
If I'm reading right (comprehension lacks sometimes) what you are asking is can you mount these other drives in some more meaningful location.  If you have a 2nd drive with say music on it, there's no reason you can't have it automount to your /home/username/Music folder.

To do this, you have to edit your fstab.  Google fstab- and you will find plenty of information on the subject.  One bit of advice- mount it by the UUID number, rather than the sdb1 name.  The drive name (letters) can change sometimes, but the UUID is fixed.

If that's not what you are asking- to add these items to your "places" menu, simply bookmark them in Nautilus.  Browse to the folder, click bookmark -> add bookmark and it'll show up in your places menu.

BM

---

### Post by Zelandeth on 2009-09-22
You've answered my question in two ways there...both of which are valid solutions I think!  Thanks for that!

I'm going to need to read up on fstab as that's not something I've yet dabbled with - need to be careful as the second drive on the PC is an NTFS drive - as I need to be able to access it from Windows as well (for work unfortunately, or I'd probably have ditched it altogether by now).

At least for the time being, editing the bookmarks in there has at least made things look a bit more sensible!  Didn't realise you could edit them...I'd tried right clicking...never thought of the bookmarks menu though!

Learn something every day...some days it's just more obvious than others!

---

### Post by blur xc on 2009-09-22
No sweat-

On my system, I have my main 500gig hdd, and in that I have a separate partition for all my users' home folders, and it's mounted at /home.  I also have an external 1tb drive w/ all my photos and some other crap.  I have that drive mounted at /media/FreeAgent_Drive (not a good name when working at the command line), and on that drive, all the photos are in a subfolder called- you guessed it- Photos, and to that I have a bookmark.  Makes life easy for my wife when she's looking for our photos.  I'd get trouble if I told her she had to navigate to the direct path every time she wanted to look at a photo.

BM

[edit]
PS- I just thought of another solution- symbolic links...  I have a /home/shared/Music (among other things in the shared folder) directory.  I executed a cp -s /home/shared/Music /home/<username>/Music so that my Music folder points to the /shared/Music folder.   For example, from my home folder, cd Music takes me to the /home/shared/Music path.  To do that, first you have to rmdir your Music folder (as long as it's empty).  I have however, heard warnings against using too many symbolic links...

---

