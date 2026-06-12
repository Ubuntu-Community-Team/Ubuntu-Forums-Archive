---
title: "Problem Cleaning Up Root File System"
date: 2010-12-16
forum: General Help
---

### Post by maatghandi on 2010-12-16
Howdy,

My current installation setup has a separate partition for /, /boot, /home, /tmp, /usr, and /var. The problem I have is the root partition / is 98% full (4.3GB full). Cleaning temp files and log files won't help since they are on their own partition (and clean).

I've removed all but two linux-images. Linux images seem to run at a size of roughly 105M. My root partition is 4.6GB. I can't seem to find any other options for cleaning up space on this partition. I have no idea what is taking up 4.6GB of space.

Disk Usage Analyzer has not been helpful since I have not been able to reconcile 4.6GB of memory with what it claims the total size of the remaining directories occupy. I've tried localepurge, gtkorphan, apt-get clean, apt-get autoclean, apt-get autoremove. I've removed all packages listed under Status -> Not Installed in the package manager. My root file system is still 98% full (4.3GB full).

Any suggestions would be very much appreciated. I don't see why Ubuntu root file system needs that much space so I must be missing something.

Maat

---

### Post by JKyleOKC on 2010-12-16
Since you're dealing with the root file system, presumably you are doing so as "root" whether by using sudo on each command, or using "sudo -i" to get into a root shell where you can do the work. Unless you used shift-delete rather than simple delete each time you deleted a file, it will have gone into the trash bin for "root" rather than the one for your own user. Search for "trash" starting at the "/root" directory, and you'll probably find the files that are still taking up all that space.

You may be able to get rid of them from your normal user area by typing "gksudo nautilus" to open the file manager as root, then navigating to the /root directory and emptying the trash.

---

### Post by cariboo on 2010-12-16
I don't understand why you went old skool in partitioning, but have you checked root's trash to see if there are any large files in there. I don't use the trash bin on my system so it hasn't been created, so I can't give you the exact path.

---

### Post by maatghandi on 2010-12-17
Sorry for the long delay in replying. Thank you for your help. Unfortunately I have never deleted anything as root so there is no root trash (i.e. there is no /root/.local/share/Trash directory). Hence this is not the source of what is taking up 4.3GB of space.

I'm not sure why I'm having such a hard time finding where the space is going to. Is there a command line program or some gui that I can use to accurately look at the contents of the root directory rather than just sifting around in the dark until I come across the problem? For example, something like dpigs would be great if I could specify the program to look at a specific directory rather than the entire file system.

By the way, using dpigs, the top 20 largest packages installed on my computer total 1.7GB (not including matlab, but this is installed in the home directory which has it's own partition).

Thanks for your help,
Maat

---

### Post by Don Barzini on 2010-12-17
An easy way..... In a terminal at the root directory use the **du** command. For human readable, it is **du -h**.

It will give you a long list, so it is best to output to a text file. E.g...

```
du -h > /root/du.txt
```

Check the list, check it twice. See what directories are naughty and nice.

You can then also just check a directory itself... such as...

```
du -h /etc
```

That will give you an idea of which directories are taking up a lot of space.

---

### Post by JKyleOKC on 2010-12-17
> **maatghandi said:**
> Is there a command line program or some gui that I can use to accurately look at the contents of the root directory rather than just sifting around in the dark until I come across the problem? For example, something like dpigs would be great if I could specify the program to look at a specific directory rather than the entire file system.From the CLI you can use "find /root -size +1G" to find all files in /root that are larger than 1 GB. If you get "permission denied" you can run it as root by using "sudo -i" first to get a root prompt. Changing "root" to any other directory name or path will search only the specified one and its subdirectories. Changing the G to M will change the unit from GB to MB, and changing the 1 to some larger value will change the size threshold. If you use "sudo -i" to get a root prompt, you can use "exit" to return to the normal prompt.

This is a very powerful command but if you tell it to search the whole "/" directory it can take quite a long time to complete its search. In testing it before posting this message, I started with a +10GB threshold (which found only a couple of VM virtual disk files), then tried again with +1GB, and finally down to +100M (which needed to be piped to "less" or redirected to a text file since it found many more than one screen full of files).

If you do "man find" you'll see lots of other options and tests for this command; it's one of the best tools I know for searching the file system!

---

### Post by maatghandi on 2010-12-18
Perfect, thank you. Using du -h revealed that a backup attempt back in October seemed to have created a directory under /media rather than saving the backup to the hard drive that was mounted. The result was a 3.8GB backup file stored in /media. Ha. I never would have looked in /media.

Thanks for the du command and the -size option for find. I've never used them before. Good to know.

The problem I had was not that /root was full, but that / was full. This made it much harder to figure out what was going on. The reason I have the "old skool" partitioning is because I feel like I have more control. To be honest I'm pretty happy with this partitioning exactly because of this scenario; I know that collectively bin, sbin, dev, etc, lib, lib32, root, sys, opt, and proc should only take up ~1GB. I put all of these directories on a 4.6GB partition, plenty of space, but still small enough to contain it. Likewise with /home, /var and /tmp. It's nice to have these contained as a way to control what is going on. As with putting /usr on it's own partition, well that is left over from playing with Gentoo and has proven more annoying than anything in the past. I'll probably not do that the next time around.

Thanks again for all your help,
Maat

---

### Post by canam101 on 2010-12-29
> **JKyleOKC said:**
> If you use "sudo -i" to get a root prompt...Thank you very much for that bit of wisdom.

I discovered that my /root/.local/share/Trash/files directory had an enormous amount of space being taken up by 300+ files.

I got into nautilus as root and was tearing what was left of my hair out trying to figure out how to delete the stuff - no 'delete' on the right click; if I used the 'del' key, the file popped right back with a .2 on the end of the name.

But after entering sudo -i, I was able to navigate to the directory and did a bunch of rm * and got rid of almost all of it.

---

