---
title: "Newbie screwed up permissions"
date: 2010-10-21
forum: General Help
---

### Post by brianj.wagner on 2010-10-21
I've been running Linux Mint 9 for a few months now and it is definitely a welcome switch over from Windows.

The other day I was trying to set up a Git installation for when I do development away from my box I can still keep everything in sync. Well I was following some instructions on setting up permissions and I'm pretty sure I left out a parameter or two and ended up setting (nearly) my entire filesystem to be of the www-data group (I think). 

At the time, I didn't notice the impact. However, once I restarted my box yesterday from some updates, I was starting to get all kinds of errors at login. I researched them individually and ALL of them were due to permission issues. 

Once I individually repaired these errors (ultimately the right file or directory to chown), I was finally able to actually boot into Mint. Once there, I couldnt perform simple operations such as mount my DVD drive or any of my external storage devices, which was never a problem before.

I know I screwed up. Whats the best way to go about fixing this? Do I reinstall Mint? If I do that, will I lose what software and packages I installed?

Thanks for helping out a newbie. The more I learn, the more I love Linux.

---

### Post by efflandt on 2010-10-21
To correct your permissions or ownership, you would need another system to refer to, and that could be quite tedious, and you might miss something.  Reinstalling is likely easier.

In the future, before using any command that could have broad sweeping effects, try **ls** with the paths first to see what it will affect.  Then to make sure that you still have the same paths, hit the up cursor to bring that back and change **ls** to the command.

You have to be particularly careful about paths that start with just / and are recursive, or end with "*" not ending part of a file or directory name (like ending with /*), because that can include ".." which is the directory above the one that the path refers to.

---

### Post by brianj.wagner on 2010-10-21
> **efflandt said:**
> Reinstalling is likely easier.

I figured as much. Thats fine, Linux's installation process is a dream compared to the agony that is Windows.

Will the reinstallation effect my already installed software? Will it wipe it all out like Windows does? Or does the lack of registry allow me to preserve all of it?

Thanks for your help.

---

### Post by P4man on 2010-10-21
It will wipe everything out, unless you have created a separate /home partition and you dont format that, then you preserve your settings (also app settings) but not the apps you installed. You can create a list of all installed packages and reinstall them by doing:

```
sudo dpkg --get-selections > my-packages
```

Save that file somewhere.
restore them after the reinstall with :

```
sudo dpkg --set-selections <my-packages
sudo apt-get -u dselect-upgrade
```

If you do that, make a backup of your home folder and restore that too. Setting permissions on your homefolder should be easy.

---

### Post by brianj.wagner on 2010-10-21
Thanks for all your help! I will do this when I get home tonight.

I'll be more careful next time with my su power.

---

