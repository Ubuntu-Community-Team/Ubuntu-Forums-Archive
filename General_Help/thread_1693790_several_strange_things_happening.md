---
title: "several strange things happening"
date: 2011-02-23
forum: General Help
---

### Post by ewaynec on 2011-02-23
Sometime around Feb 15 I started having several problems. Some of which are, the reported free space on my hard drive changed (from 81Gbt to 365Gbt), I go to "places> home folder- it ask for a password (this has never happened before), my 4Gbt USB drive now has 3.4Gbts and an AVI file stored on it will no longer play on my DVD player, I have tried re-formatting, changeing the partition, when I want to look at a text file (ie places> home folder> documents> xxxx) it pops up a window that ask "Do you want to run "xxxx", or display its contents? It gives me options [run in terminal] [display]  [cancel]  [run], When I click on anything but "display" I get an error.
  There are several other little things, like additional options and pop ups while running a program that were not there before.
  I am using Lucid Lynx ver. 10.04 and have been since it came out. I have a 500Gbt HD with 1 partition, Linux is my only OS.
  I remember a similar problem in 8.04 caused by an upgrade, and I wonder if this is the case. If so is there a way to find out what upgrade was issued about that time and can I un-do it?
  Thanks for any help,
    Wayne.

---

### Post by ewaynec on 2011-02-25
I guess I can add one more strange thing,   no one is responding.

---

### Post by Bcrowes11 on 2011-02-25
I hate to say, sounds like you got one of the rare viruses for linux. You might want to format your drive and reinstall Ubuntu. This time get 10.10.:guitar:

---

### Post by ewaynec on 2011-02-28
I guess if you are not held to any kind of accountability you can say anything you want.

---

### Post by Habeouscorpus on 2011-02-28
Or maybe they know what they're talking about?

I have to agree. If things are getting weird, flatten and rebuild. Just back up your home folder first.

---

### Post by cchhrriiss121212 on 2011-02-28
> the reported free space on my hard drive changed (from 81Gbt to 365Gbt)
Did you delete a large amount of data? Do you regularly empty the wastebasket?
> I go to "places> home folder- it ask for a password (this has never happened before)
What happens when you enter your password? What are the permissions of the folder when you right click it?
> my 4Gbt USB drive now has 3.4Gbts and an AVI file stored on it will no longer play on my DVD player
Could be a corrupted file.
> when I want to look at a text file (ie places> home folder> documents> xxxx) it pops up a window that ask "Do you want to run "xxxx", or display its contents? It gives me options [run in terminal] [display] [cancel] [run], When I click on anything but "display" I get an error.
That is normal.
> There are several other little things, like additional options and pop ups while running a program that were not there before.
Sometimes updates add extra features or change appearance, it is nothing unusual.

---

### Post by blackmail on 2011-02-28
There could be a more simple version without reinstalling...
Mainly you could should see what process is active when you get those prompts trace it back to the files that cause this and just remove them, after that to get rid of the upgrade and to still improve your system you could just compile the kernel from kernel.or and get the new gnome/kde depends on what you prefer and just install it and also be sure to check on  gnome-look.org or kde-look.org to get some nice sking and you could also quit using Firefox and install a nice little netscape style browser...

Or then again you could just reinstall your system...

---

### Post by ewaynec on 2011-03-01
It could be that my keyboard is "off white", my computer case is "gray" and the monitor is "black" causing a terrible mismatch.

---

### Post by ankspo71 on 2011-03-04
Hi,
Some people avoid upgrading from release to release because they experience strange things happening or failed upgrades.

What you describe sounds like having a corrupted file system, that is giving you possible data loss and damaged un-openable files. It could have been because of the upgrades, or maybe something else. An fsck might be in order. [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck) [http://ubuntu4beginners.blogspot.com/2011/02/tune-filesystem-check-fsck-on-ext.html](http://ubuntu4beginners.blogspot.com/2011/02/tune-filesystem-check-fsck-on-ext.html)

I stopped using ext4  file systems because it just don't feel stable enough for my set of hardware yet (personal opinion only). It would seem great for a while then all of a sudden I would notice missing files and poor performance. I was having problems with ext3 too, just not as much. I then started using XFS because it has been around alot longer. Well, so has ext2 too, but I wanted to try something different. I haven't noticed any unusual file system behavior ever since going with XFS, which has probably been about a year now. If you have any doubts about ext4 (or even ext3), try using an older but popular file system. 

Also, it might help you to have multiple partitions such as a separate one for /home and maybe a separate one for /my-data just in case the system ever goes down and needs to be reinstalled. All of my data is kept on a second hard drive just in case something ever goes wrong.

Hope this helps.

---

### Post by ewaynec on 2011-03-04
Thanks for the reply, I could be wrong but I don't think the problem is a corrupt file system, I would get errors if that were the case, fsck is run automatically at boot time when the system detects that a file system is in an inconsistent state, indicating a non-graceful shutdown, such as a crash or power loss. 
  The biggest problem I have is; when I go into "file browser" it ask for the ROOT password, so it is opening File Browser as root, It opens in the Root folder, Then I enter the Root password and I can then go where ever I want. ( It does not do this every time, just most of the time.)
  When I open File Browser the first things listed are ROOT, DESKTOP, (which is the root desktop), then FILE SYSTEMS, etc.
  I think all the little differences I am experiencing are a result of logging on as ROOT user. I think that when I open File Browser (I use this a lot) and it ask for the ROOT password I am then ROOT and remain ROOT until I log off (I never do, because I am the only user). When I am root, things will look and feel different than when I am logged on as Wayne, but there are some things that I cannot do as Wayne (such as open File Browser). 
  If I am right, how do I fix it?

---

### Post by ankspo71 on 2011-03-04
Hi again,
You might not be wrong at all. My advice was based on the other symptoms, not so much on your folder requiring root access. If ownership of the contents of your home folder have changed to root, it might be easy to fix if that is all that has changed.

Open a terminal and paste this command:
```
ls -l 
```

You should see results that look like this:
```
drwxr-xr-x 2 wayne wayne       23 2011-03-04 08:24 Desktop
drwxr-xr-x 2 wayne wayne        6 2011-03-01 22:28 Documents
drwxr-xr-x 2 wayne wayne        6 2011-03-02 10:55 Downloads
```
and so on. If you see "root" instead of "wayne", then root has taken over ownership of your home directory. 

You can use the following command to also see the hidden files loccated in your home directory: 
```
ls -al 
```

To attempt to fix it back so that you have ownership of the files in your home directory, you could try this command:

```
sudo chown -R wayne:wayne /home/wayne
```

Explaination of the above command:
Change ownership recursively using wayne's userid and groupid in the folder of /home/wayne

There shouldn't be errors but if you do see errors, then you might have to refer to this thread:
Solving .dmrc and $HOME Permission Errors
[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

Hope this helps.

---

### Post by ewaynec on 2011-03-09
I posted this problem on another forum and got a solution without re-installing anything.

---

### Post by rg4w on 2011-03-09
What was the solution?

---

### Post by ewaynec on 2011-03-10
First, make sure you are not root (login as yourself, do not open nautilus)

Use gedit to open the file ~/.local/share/applications/mimeapps.list

Find the line that starts inode/directory=something-that-it-should-not-be
and edit so it reads as inode/directory=nautilus-folder-handler.desktop

Save the file.

Logout & back in again. Hopefully that will fix it.

Mine looked like this,
inode/directory=userapp-gksudo-VR2WQV.desktop;nautilus-folder-handler.desktop;firefox.desk

I changed it and not the File browser opens without a password.

The opening a document with the four options was corrected by changing "file management preferences", "behavior", Executable text files", second button.
  Something so weird, seems so simple once the solution is known.

---

