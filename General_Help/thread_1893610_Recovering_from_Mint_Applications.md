---
title: "Recovering from Mint Applications"
date: 2011-12-10
forum: General Help
---

### Post by SevenThunders on 2011-12-10
I wanted to see what all the fuss regarding Mint was about, in part due to the complaints regarding Unity.  I don't hate Unity per se, though I don't like the way it messes with compiz and it seems that cairo does about the same thing only better.

Well I went and installed Mint Mate,  mintmenu and their gnome 3 desktop just to see what it was about, following the instructions posted here:
[http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/]("http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/")

Oh boy was that a mistake.  Not that the Mint UI was bad, (though it isn't that special either),  but rather because it really trashed my Ubuntu setup.

It basically,
1) disables ubuntu software center, 
2) changes your splash screens and 
3) changes your grub boot menu,  I think it might have even messed with the kernel but I'm not sure.

So to fix 1) you have to repair /etc/lsb-release, e.g.
sudo gedit /etc/lsb-release

and then put the right fields back in namely,
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric"
Unfortunately I didn't have all this information and had the wrong codename which in turn made the program software-properties-gtk fail.  I finally figured this out after a couple of days of pulling my hair out.

Now after you make that change you immediately have to remove all mint related packages,  searching for mint in synaptic, otherwise mint will overwrite all of your changes.  I also disabled the depository by commenting it out in /etc/apt/sources.list

That fixes 1) and partially fixes 2).  To fix 3) I had to install grub-customizer from
[http://ubuntuforums.org/showthread.php?p=10340183#post10340183]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183")

All I did there was edit the descriptions since I think the menu points to the right kernel now anyway.  Well I'm almost back but I still have a few issues and concerns.  One is that I don't have the ubuntu flash screen anymore after going through the main grub menu selection after boot up.  The other nagging concern is,  did I miss something?  Is my ubuntu ok now or do have some hidden system scripts trashed forever?

---

### Post by SevenThunders on 2011-12-10
OK I figured out how to fix the splash screen problem.  That was pretty easy actually.  You just need to edit:
gksu gedit /etc/lightdm/unity-greeter.conf

and look at the background field.  There are a bunch of .jpg files in the /usr/share/backgrounds directory.

---

