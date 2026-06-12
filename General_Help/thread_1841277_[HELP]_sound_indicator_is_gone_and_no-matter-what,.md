---
title: "[HELP] sound indicator is gone and no-matter-what, can't restore it"
date: 2011-09-09
forum: General Help
---

### Post by glósóli on 2011-09-09
Hi!

I will try to be concise and understandable.
Under 10.10, one day the sound indicator in the upper right corner was gone, the bar was sort of grey and un-clickable.

I used to regulate sound then by starting alsamixer in terminal, even more complete than the standard indicator, so, no big fuss.

yesterday I installed 11.04.
Upon first reboot, the sound indicator was there ofc. Even lovelier, the combo keys of my laptop to regulate the volume were finally working, out of the box! incredible!

then I pointed the new home directory to MY home directory, rebooted, everything was in place and all the settings restored. Including the NOT working sound indicator. Now that even my laptop keys *would* work, I definitely want it back!

I tried to install indicator-sound, says it is already in the system, but if I launch it in the terminal, says command not found
I tried gnome-volume-control-applet, installing it, fine; launching it, it is already running.
Tried to put both commands on startup, but nothing.
If I click on Sounds in System Settings, it will just say 'waiting system to respond' ...

please, can you help me find a solution to this problem? the impediment is for sure in my home directory, but I don't know what to look for, I am still sort of a newbie here :(

Many thanks in advance!!

---

### Post by Wayne_V on 2011-09-09
you would be better off going back to the home directory with the working config files and then mv'ng your documents from the old home directory to there (skipping the "dot" files for the most part -- other than .mozilla and maybe a few others).

---

### Post by Bodsda on 2011-09-09
> **Wayne_V said:**
> you would be better off going back to the home directory with the working config files and then mv'ng your documents from the old home directory to there (skipping the "dot" files for the most part -- other than .mozilla and maybe a few others).
 
+1
 
Go back to the working home dir, and then migrate your documents and folders a few at a time, testing the sound applet as you go. This is the easiest way of resolving the problem.
 
Bodsda

---

### Post by glósóli on 2011-09-09
thank you for your replies.
Just wondering (maybe I am missing out something), so shall I erase the link from etc/conf, this way it points back to the original, fresh, untouched home folder, and then I move my folders here, and then I move everything back to the home _partition_?
I am having quite some stuff in the home folder, like Chrome settings etcetc, it seems to me quite a time-demanding task :(

---

### Post by Bodsda on 2011-09-09
> **glósóli said:**
> thank you for your replies.
Just wondering (maybe I am missing out something), so shall I erase the link from etc/conf, this way it points back to the original, fresh, untouched home folder, and then I move my folders here, and then I move everything back to the home _partition_?
I am having quite some stuff in the home folder, like Chrome settings etcetc, it seems to me quite a time-demanding task :(
 
Install1 - home folder1 (broken)(files are here)
Install2 - home folder2 (working)(no files)
 
Change your settings so that 'home folder2' is your home folder. Then move everything from 'home folder1' to 'home folder2' - this doesnt have to be time consuming, you could copy and paste half of the stuff, test, then copy the rest and test.
 
Bodsda

---

### Post by glósóli on 2011-09-09
> **Bodsda said:**
> Install1 - home folder1 (broken)(files are here)
Install2 - home folder2 (working)(no files)
 
Change your settings so that 'home folder2' is your home folder. Then move everything from 'home folder1' to 'home folder2' - this doesnt have to be time consuming, you could copy and paste half of the stuff, test, then copy the rest and test.
 
Bodsda

well, I wasted another half day and, besides trying your way with lack of success, did also:

- clean re-install of Ubuntu 11.04 on the appropriate partition
- follow howto to move the current (hence new, and with working sound applet) home folder to a separate partition
- as soon as I did this, sound stopped to work. didn't even need to restore my files to the new home partition.

resulting in waste of time, increase of my ubuntu love/hate, proliferation of hundreds of home folders, and a general feelings of frustration.

Seriously, it seems like there is some sort of daemon or whatnot running in the main partition, which expects to find some files in the home directory, located in the same partition as it resides. As soon as the home dir is relocated, everything pops down.
Guess I have to stick to the bloody alsamixer.

---

### Post by Wayne_V on 2011-09-09
I don't understand - why are you moving the new home directory?  and why to a new partition?  and what howto?

---

### Post by magicland on 2011-09-14
Hi there,

can you run this command in the terminal:

```
lspci
```

and then post the results? I'm having a similar problem and would like to compare the audio devices to see if it might be the issue or not.

Thanks

---

### Post by magicland on 2011-09-14
Here is the fix (worked for me at least):

> **magicland said:**
> Hey guys, found a fix for the volume indicator.

Source: [http://askubuntu.com/questions/30742/how-do-i-access-and-enable-more-icons-to-be-in-the-system-tray](http://askubuntu.com/questions/30742/how-do-i-access-and-enable-more-icons-to-be-in-the-system-tray)

Code to copy/paste in the terminal:

```
gsettings set com.canonical.Unity.Panel systray-whitelist  "['all']"
```

This will whitelist all programs to use the unity's  panel.

---

### Post by glósóli on 2011-09-14
> **Wayne_V said:**
> I don't understand - why are you moving the new home directory?  and why to a new partition?  and what howto?

sorry for late reply, I am deeply busy in completing my thesis.

I have my home directory in a dedicated partition, so i can
- restore/update the system in a painless way (I thought)
- having all my data in a partition external to Ubuntu system, let me access the data from e.g. Windows or other OSs

so that is why i am 'moving' the home directory.
and indeed all this troubles are really annoying me, seems like it is really impossible to have a double system accessing the same data, also with chrome/chromium sharing the same folder I was having a lot of issues (password saved in ubuntu not saved under windows, some bookmarks as well etc.etc.)
so maybe in the end it is not worth the spent time.

but I will try the advice of magicland (thankx!), though my whole ubuntu system and home partition are pretty wrecked now :(

---

### Post by CatKiller on 2011-09-14
Why didn't you use a separate /home partition from the off when you installed if you already knew it was something you wanted to have?

---

