---
title: "/Home partitions opinions wanted"
date: 2010-03-06
forum: General Help
---

### Post by BrockStrongo on 2010-03-06
I am trying to decide whether or not to move my home folder to its own partition, and thought I would gather some opinions first. Plus, there are a couple key questions that I have to answer before I am ready to do this.
 
1) I am using ext4 and remember reading that there is a possibility of corruption when moving large files. Is this still true? 
 
2) Will this actually save all my personal files when changing distros, ie; programs downloaded, visual settings, plugins, restricted extras,, flash, drivers, etc? Basically all the little things I have spent the last 8 months collecting, tweaking and compiling. 
 
3) Would it be possible (or easier) to just dual boot the other distro and mount the existing partition to access my files? 
 
Any input on this would be greatly appreciated. 
I would like to hear your experiences doing this.
Thanks for you time and knowledge.
Cheers

---

### Post by nothingspecial on 2010-03-06
1. I use ext3 for my /home partition (ext4 for /) for this reason. As you have to create a new one for /home why not make it ext3. You should back up any vital data to external media anyway.

2. No. Anything you have installed is in / and therefore not in /home so you would have to reinstall flash etc. Your Wallpapers, themes, music libraries in players etc are saved. There are ways of making the reinstallation of stuff easy though. Once you reinstall an app, if you have a seperate /home, that apps settings will be the same. But be aware that different distros do thimgs differently so there may be conflicts. You should be pretty much ok with debian based distros in my experience.

3. Yes and Yes. The main advantage of a seperate /home is to keep your settings, and not to have to copy data from backup, when you reinstall the distro you are already using.

---

### Post by BrockStrongo on 2010-03-06
Thanks, I am asking these questions in anticipation of Lucid, I want to be ready when the stable release comes out April 29th.
Additional Question; Is creating the /home partition and having it automount really as easy as the walkthroughs make it seem?

---

### Post by joeknoodle on 2010-03-06
> **BrockStrongo said:**
> I am trying to decide whether or not to move my home folder to its own partition, and thought I would gather some opinions first. Plus, there are a couple key questions that I have to answer before I am ready to do this.
 
1) I am using ext4 and remember reading that there is a possibility of corruption when moving large files. Is this still true? 
 
I'm an amateur, so all cautions apply, including backing up important files.

It's only slightly tedious, but I recommend you create and use a /home folder on a separate partition. Create it, and then use copy / paste to move a few files or folders at a time. I recommend copy / paste over simply moving in case there is corruption, power outage, crash, etc.
Using a partitioned /home folder can help prevent data loss due to OS crashes and reinstalls.

> 
2) Will this actually save all my personal files when changing distros, ie; programs downloaded, visual settings, plugins, restricted extras,, flash, drivers, etc? Basically all the little things I have spent the last 8 months collecting, tweaking and compiling.
 Not sure when distro hopping, but under Ubuntu I've had success.

> 
3) Would it be possible (or easier) to just dual boot the other distro and mount the existing partition to access my files? 
 I'd be wary of doing this, as one distro may overwrite files or settings the other one would need.

If you did go this route, I'd say create a partitioned folder such as /MyStuff that holds non-OS or non-Application stuff, like pics, music, docs, etc.

Then the various OSes could access those with less chance of corruption other than your /home application settings and etc.

Remember, I'm an amateur, but I've used this advice myself with no ill effect (so far :) ).

---

### Post by nothingspecial on 2010-03-06
Yes.

If you are reading psychocats, one thing I have found is that you do need to put the sudo in this command
```

find . -depth -print0 | [COLOR="Red"]sudo[/COLOR] cpio --null --sparse -pvd /new/
```

---

### Post by oldfred on 2010-03-06
If your hard drive space and desires are to just have Ubuntu and upgrade by doing a fresh install then you should have a separate /home. You can export all the packages you have installed and reimport them. (you may get some older stuff also). I do this occasionally and include in my normal backups. 
If you are thinking about multiple distributions or even several versions of Ubuntu you should have a separate data partition. Separate /home then is not required as it is small and very easy to backup.

Separate Data partition:
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of blog
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

---

### Post by BrockStrongo on 2010-03-06
Thanks for all the input so far. Additional Question;Correct me if I'm wrong, but, increasing or decreasing the size of the /home partition would be easy as booting  the live disk and using gparted. Right? 
sorry for all the addition questions

---

### Post by nothingspecial on 2010-03-06
Maybe

Messing with partitions is a good way to loose your stuff.......

.....which is part of the reason having a seperate /home (once you have it) is a good idea.

---

### Post by blueridgedog on 2010-03-06
I generally don't want to restore the config files when I do a clean build (other that firefox and virtualbox) so I keep a separate /documents partition that I simply link to in my home directory.  I get the benefit of easy restore/back/reinstall without a lot of conflicting config files when I do a fresh install.

---

### Post by BrockStrongo on 2010-03-08
Thanks for all the comments. I am going to setup that partition when I get home from work tonight.
I appreciate all the help from everybody here at ubuntuforums, you have all made my linux experience educational and quite enjoyable.
THANK YOU ALL VERY MUCH

---

