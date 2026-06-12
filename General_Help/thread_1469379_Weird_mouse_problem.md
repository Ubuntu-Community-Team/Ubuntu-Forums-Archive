---
title: "Weird mouse problem"
date: 2010-05-02
forum: General Help
---

### Post by lerrup on 2010-05-02
I have just updated the family desktop to lucid and have run into a very odd problem with the mouse.  It stops accepting left clicks and needs to be reset with right clicks/locks up and is generally a pain.

After testing it appears to be a problem in the user configuration.  I am sure it is**not**:

1 a hardware problem;
2 an x-server problem
3 a gnome/kde problem.

Basically, if a new user is created it works fine-on any old user it does not.

Clearly, there is one file that means that is incompatible.  Any idea what that might be?

---

### Post by dino99 on 2010-05-02
as it is an upgrade, maybe its time to clean the room a little:

install and run gconf-cleaner (yes when asked to all)

install bleachbit but take time to read comment about each setting you check, and use it as admin, it will wipe the caches and old symlinks and more (take care about your bookmarks and passwords, dont check)

be sure you only have Lucid genuine repo into sources.list

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

---

