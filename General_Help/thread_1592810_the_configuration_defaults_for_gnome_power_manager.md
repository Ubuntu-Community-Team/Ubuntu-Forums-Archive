---
title: "the configuration defaults for gnome power manager have not been installed correctly"
date: 2010-10-10
forum: General Help
---

### Post by kevlar93 on 2010-10-10
I was using simple backup config to backup home to an external drive and it was working fine for the past week or so and today after the backup the computer was restarted and I am unable to log on. I get an error message saying. "the configuration defaults for gnome power manager have not been installed correctly "

I did some googling and the problem is that / is full. I have been trying for the past three hours to delete some space on / so that I can log on. I used ctr-alt-f1 and I can log on there but whatever command I use to delete the root trash it fails. I get an error message saying /root/.local/share/Trash/files/ is not a file or directory.

Somebody please assist me to delete root trash so I can log onto this computer. I have used every variant of sudo rm -r /root/.local/share/Trash/files/ that I could find including one using Chmod. I have already tried the commands found in this tutorial [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

I also reinstalled gnome but that did nothing. 

Thanks.

---

### Post by fishexe on 2010-11-27
I am having a similar problem, same error message although in my case /home was full, / never was.  I have freed up plenty of space but I still get the error message.  Have tried everything in this thread with no luck:
[http://ubuntuforums.org/archive/index.php/t-980711.html](http://ubuntuforums.org/archive/index.php/t-980711.html)

Fortunately one of my user accounts does not have the problem, so I can log on and use the system as that user, or even su to other users, but all other users are locked out from gnome.

---

### Post by fishexe on 2010-11-27
I have solved the problem.  The solution on my system was to delete the .gconfd/ directory from the affected users' home directories.  After deleting this everything worked fine.  You may lose some settings if you do this, however.

If this doesn't work there are a few more files you can try getting rid of, described here:
[http://forum.nginx.org/read.php?26,135674](http://forum.nginx.org/read.php?26,135674)
Be warned that if you delete all of the files mentioned in this thread you WILL lose most of your desktop settings (your panel, for instance, will revert to a default panel)

This appears to be a bug that sometimes happens during routine updates.  It's hard to find information on because aside from that one thread, most are from several years ago when the same error message was occurring when people filled up their hard drives, and then could fix it by making space and using apt-get to fix things, but the old approach doesn't seem to work on the current incarnation of this error.

---

### Post by MelodiesonMusic on 2011-01-30
I know this is an old thread, but this happened to me last night and just in case it randomly happens to someone else i'll tell you exactly what I did. You may want to write this down if you don't have an amazing memory or two computers ;)

1. Press and hold the keys Ctrl, Alt and F1 (In that order)
2. Sign in
3. Copy and paste this code one line at a time:
 ```

sudo apt-get update
sudo apt-get upgrade
rm -rf .gconfd
```
4. Restart your computer
5. Sadly, you'll notice everything looks a little different. Just change things back to the way you like them. If you've installed a system-backup manager go back to the day before it happened. Just make sure you manually delete .gconfd, it'll be a hidden file in your home directory

Thanks to fishexe for the solution

---

### Post by Jetro on 2011-04-03
I\m getting so tired of this, I want it to work...
I can\t log in, so I can\t do any fancy commands from there.

Wanted to try to delete the .gconfd folder from the affected partition, but I cannot remove, delete or cut anything from it. ._.

---

