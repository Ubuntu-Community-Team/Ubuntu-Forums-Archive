---
title: "Saving applications"
date: 2009-09-30
forum: General Help
---

### Post by Rhetoric Camel on 2009-09-30
Hopefully General Help is the proper section for this question.

I have a question about saving applications with ubuntu. I know with windows I'm able to select the drive and the location of any program I'm going to install. But I haven't figured out how to do this with Linux yet. I only have about 20gb dedicated to ubuntu and I've filled it up (looking into GParted Live at the moment) but was wondering if there is a way to install programs (Audacity, or Hydrogen, or even downloaded games) onto a different drive all together.

I have one 300gb hdd. Windows is on a partition (C:) of 50gb. I had installed Ubuntu on what I thought was the other 250gb section (G:) but it seemed to only install on a small 20gb section (file system) of the G: drive and the rest of the drive is listed under File System>Host, which is where I'd like to install any other programs I download. Is this possible to set up so that I don't have to go through all this defragging, trying to figure out GParted, and possibly screwing things up? I don't see options for this in add/remove programs or when I go to install something through the terminal, it always just seems to go right where I don't want it to.

Thanks in advance.

---

### Post by Rhetoric Camel on 2009-09-30
if this isn't possible, would it be better to reinstall ubuntu and select a bigger section for Ubuntu to save onto and run from, and if so is there a way that I wont lose my configurations like two monitors, sound settings, and all that stuff? Or will GParted do this without having to reinstall. Sorry for any confusion, I'm a bit confused myself.

---

### Post by Giblet5 on 2009-09-30
The easiest answer is not exactly easy.

Add a new disk drive to your PC. Even laptops usually have a bay for a second disk drive. It's easy.

Use gparted or fdisk to create a new linux partition on that new disk drive.

Use mke2fs to format it for linux.

Edit /etc/fstab to mount that new partition on /home.

Execute this:
```
sudo bash
mv /home /home.oldnbusted
mkdir /home
mount -a
mv /home.oldnbusted/* /home
rmdir /home.oldnbusted
exit
```

Now, you should have LOTS of free space on / and your new home.

---

### Post by Giblet5 on 2009-09-30
BTW: matching the installed packages from an old system to a new system is easy:
```
sudo dpkg -l | awk '{ print $2 }' > packages.txt
```

Remove the top few lines packages.txt - you'll see which ones and it's not critical...

To install all missing packages on a new install, copy packages.txt to the new install and: ```
for i in `cat packages.txt`
do
  sudo apt-get install $i -fqy
done
```

---

### Post by Rhetoric Camel on 2009-09-30
awww that sucks, I don't have any type of money for a new disk drive, and the 3 I do have are all filled to the max, looks and sounds like I'm kind of screwed.

---

