---
title: "advice please...."
date: 2011-06-08
forum: General Help
---

### Post by K4NEB on 2011-06-08
I downloaded ubuntu about a month ago now and put it on a disk ready to install.

BUT i have been unable to install as i cannot shrink my windows partition! 

damn i hate windows!

so i was going to just install it over the top and get rid of windows.

should i download and burn a new copy of ubuntu for install?

will there be critical updates i might need?

---

### Post by mike555 on 2011-06-08
You should run Ubuntu live for a while to be sure it will work with your hardware , printers , etc. before installing ......

---

### Post by doas777 on 2011-06-08
> **K4NEB said:**
> I downloaded ubuntu about a month ago now and put it on a disk ready to install.

BUT i have been unable to install as i cannot shrink my windows partition! 

damn i hate windows!

so i was going to just install it over the top and get rid of windows.

should i download and burn a new copy of ubuntu for install?

will there be critical updates i might need?
depends on how long it's been. 6 months after an LTS release they put out x.x.1, which rolls up all the security updates and upgrades into the live CD. I don't think they do this for incremental releases like maverick or natty though.  

so, no, just install off the disk you have and then run an online update.

a peice of unsolicited advice: backup your content files before installing overtop windows. if you have good backups, no computery problem can hurt you, but without them, you may find yourself wishing you hadn't clicked "format".

also when setting up your new system, consider a seperate home partition:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by aeronutt on 2011-06-08
Were you using gparted on the liveCD to resize your windows partition? (That's what I'd recommend, it's always worked for me.) What size hard drive do you have?

Until you know how ubuntu works, and how it works on your hardware, I'd either run from liveCD or figure out the partition resize problem so you can load ubuntu next to windows for dual boot.

---

### Post by linuxinstalledfromhdd on 2011-06-08
> **aeronutt said:**
> Were you using gparted on the liveCD to resize your windows partition? (That's what I'd recommend, it's always worked for me.) What size hard drive do you have?

Until you know how ubuntu works, and how it works on your hardware, I'd either run from liveCD or figure out the partition resize problem so you can load ubuntu next to windows for dual boot.

Also just so they know, it will ask you if you would like to resize your partition automatically during the installation process, as long as you select side-by-side as the partitioning options, it will shrink it for you to make room to install Ubuntu.

---

### Post by K4NEB on 2011-06-08
thanks for the replys everyone.

yes ubuntu works fine and dandy on my machine had it running with wubi for a month. now deleted it so i can install it properly.

BUT i cannot shrink my hardrive to  partition it because stupid windows has put files at the end of the drive that will not move! :@

backing up im not worried about i have nothing of any importance on my machine its just purely for web browsing.

and if it goes wrong. then hey i just install windows back again :(

---

### Post by hal8000 on 2011-06-08
What you have to do is defrag your windows drive first so that all files are moved to front.
Problem is that some files e.g. page file may not move, you may be able to
defrag it with auslogics

[http://www.auslogics.com/en/articles/how-to-defrag/](http://www.auslogics.com/en/articles/how-to-defrag/)

Then try gparted again.
h8k

---

### Post by K4NEB on 2011-06-09
> **hal8000 said:**
> What you have to do is defrag your windows drive first so that all files are moved to front.
Problem is that some files e.g. page file may not move, you may be able to
defrag it with auslogics

[http://www.auslogics.com/en/articles/how-to-defrag/](http://www.auslogics.com/en/articles/how-to-defrag/)

Then try gparted again.
h8k


ive defragged & boot defragged it for a good month  and everything is at at the front of the disk.

exept a few files it insists on putting at the end of the disk! :( so i cant shrink it even though i have gigs and gigs of space :'(

---

### Post by K4NEB on 2011-06-09
SOLVED IT!

dont know what i was worrying about i just installed it off the live CD alongside windows and it worked fine. 

MEGA HAPPY BUNNY NOW ! :D

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **K4NEB said:**
> SOLVED IT!

dont know what i was worrying about i just installed it off the live CD alongside windows and it worked fine. 

MEGA HAPPY BUNNY NOW ! :D

Here is a handy couple of guides for your version:

11.04
[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

10.10
[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

