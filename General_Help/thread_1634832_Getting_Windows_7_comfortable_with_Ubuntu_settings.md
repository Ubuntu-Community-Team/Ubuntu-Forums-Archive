---
title: "Getting Windows 7 comfortable with Ubuntu settings"
date: 2010-12-01
forum: General Help
---

### Post by Oxwivi on 2010-12-01
I need to use Windows to use a certain electronic edition of a book that comes in a CD with the book. And while I'm using it, I'd like to do what I usually do in Ubuntu, that is browse, occasionally play some music and chat.

I know I can copy the Firefox profile, but I just want the settings in the preferences and my addons, I'm not sure what exactly to copy.

And IM, is there any Empathy port? I don't like Trillian, and I sure am not getting each of the chat messengers, since I got comfortable with all my accounts in one program.

Can anyone help me with this?

Oh, and is it possible to share the Home folder with Windows 7? With 7 and Vista, Windows also have some sort of home folder with identical folders (Documents, Downloads, etc). Nothing important to be blown there, and it'd be nice if I don't have to keep two copies each for Windows and Ubuntu.

**EDIT** Forgot to mention, it's gonna be a dual-boot.

---

### Post by Mark Phelps on 2010-12-01
I would NOT share /home between Win7 and Ubuntu.  Even if you DO get the Win7 Ext4 filesystem driver to work (there are mixed results on this), Win7 does NOT understand Linux permissions and vice-versa.

If you want to share files, a much better solution is to put them all into an NTFS data partition.  Both Ubuntu and Win7 can read&write NTFS files.

---

### Post by Oxwivi on 2010-12-01
Hey, it can be other way round. Letting Ubuntu have it's /home folder in the one in Windows.

---

### Post by oldfred on 2010-12-01
I do not believe in writing into system partitions from another system. Eventually leads to problems.

Even windows users suggest a separate data partition so when you have to reinstall windows you do not have to reinstall all your data. Backups still required and regular chkdsk on NTFS partitions.

I have a shared NTFS partition with my Firefox and Thunderbird profiles in the NTFS /shared partition. I just edited profile.ini to point to the new path and it works. I also copy the entire profile to my portable (and back) when we travel so I have all the same settings, bookmarks & emails. On reboot Firefox will complain about add-ins as some do not work in one or the other, but I have not had any major issues even as I updated from old version to new.

[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by uidb4056 on 2010-12-01
> **Oxwivi said:**
> I need to use Windows to use a certain electronic edition of a book that comes in a CD with the book. And while I'm using it, I'd like to do what I usually do in Ubuntu, that is browse, occasionally play some music and chat.

I know I can copy the Firefox profile, but I just want the settings in the preferences and my addons, I'm not sure what exactly to copy.

And IM, is there any Empathy port? I don't like Trillian, and I sure am not getting each of the chat messengers, since I got comfortable with all my accounts in one program.

Can anyone help me with this?

Oh, and is it possible to share the Home folder with Windows 7? With 7 and Vista, Windows also have some sort of home folder with identical folders (Documents, Downloads, etc). Nothing important to be blown there, and it'd be nice if I don't have to keep two copies each for Windows and Ubuntu.

**EDIT** Forgot to mention, it's gonna be a dual-boot.

Have you considered the possibilty to install W7 on a virtual machine like virtualbox in your Ubuntu?, then you can have W7 running in a window on your Ubuntu.

---

### Post by Oxwivi on 2010-12-02
> **oldfred said:**
> I do not believe in writing into system partitions from another system. Eventually leads to problems.

Even windows users suggest a separate data partition so when you have to reinstall windows you do not have to reinstall all your data. Backups still required and regular chkdsk on NTFS partitions.

I have a shared NTFS partition with my Firefox and Thunderbird profiles in the NTFS /shared partition. I just edited profile.ini to point to the new path and it works. I also copy the entire profile to my portable (and back) when we travel so I have all the same settings, bookmarks & emails. On reboot Firefox will complain about add-ins as some do not work in one or the other, but I have not had any major issues even as I updated from old version to new.

[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
Okay, I understand about the profile. But can the user folders from both Ubuntu and Windows be on a separate partition?

> **uidb4056 said:**
> Have you considered the possibilty to install W7 on a virtual machine like virtualbox in your Ubuntu?, then you can have W7 running in a window on your Ubuntu.
Games.

---

### Post by Mark Phelps on 2010-12-02
> **Oxwivi said:**
> Hey, it can be other way round. Letting Ubuntu have it's /home folder in the one in Windows.

Bad idea ... really Bad idea.  NTFS does not understand Linux permissions, and while this CAN work, writing into an NTFS OS partition from inside Ubuntu is just asking for problems.

> But can the user folders from both Ubuntu and Windows be on a separate partition?


If you mean files critical to Ubuntu configuration settings, I would NOT put them in an NTFS partition; instead, I would keep them in a Linux partition.  The shard partition is really for data files -- music, videos, pictures, other such stuff.

---

### Post by WorMzy on 2010-12-02
You can make ~/Documents, ~/Music, etc symbolic links to folders on a shared partition for easy sharing between partitions. Or alternatively, you can bind the shared folders over the top of the normal folders (which is what I do).

You can do the symlink method by middle-click-dragging the shared folders into the home folder and choosing "Link Here". The bind method requires editing of /etc/fstab (which you will need to do for the symlink method too, to automount the shared partition).

fstab bind entries look like this:
```
/media/Terastore/Videos/ /home/wormzy/Videos none bind 0 0
```
and it works just like a symlink.

There are risks involved: Linux-to-NTFS isn't supported by Microsoft, and there's no guarantees that it will work as expected. Also, you can't defrag NTFS partitions from Linux, so you will need to use Windows for that. You also can't run chkdsk from Linux (although there are tools to fix some minor NTFS problems in ntfsprogs), so you will need WIndows for that as well. Personally, I haven't seen any problems in the past couple of years, so I would say that, while there *is* a risk, it's minimal.

---

### Post by Oxwivi on 2010-12-02
> **WorMzy said:**
> You can make ~/Documents, ~/Music, etc symbolic links to folders on a shared partition for easy sharing between partitions. Or alternatively, you can bind the shared folders over the top of the normal folders (which is what I do).

You can do the symlink method by middle-click-dragging the shared folders into the home folder and choosing "Link Here". The bind method requires editing of /etc/fstab (which you will need to do for the symlink method too, to automount the shared partition).

fstab bind entries look like this:
```
/media/Terastore/Videos/ /home/wormzy/Videos none bind 0 0
```and it works just like a symlink.

There are risks involved: Linux-to-NTFS isn't supported by Microsoft, and there's no guarantees that it will work as expected. Also, you can't defrag NTFS partitions from Linux, so you will need to use Windows for that. You also can't run chkdsk from Linux (although there are tools to fix some minor NTFS problems in ntfsprogs), so you will need WIndows for that as well. Personally, I haven't seen any problems in the past couple of years, so I would say that, while there *is* a risk, it's minimal.
A step-by-step how-to guide please? I really don't know anything about symbolic links (I understand the concept more or less, just don't know how to use it).

---

### Post by WorMzy on 2010-12-02
See this for a tutorial on how to mount your NTFS storage partition correctly: [[COLOR="DarkGreen"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251") 

As for symbolic links:

[LIST=1]
[*]Open two nautilus windows.
[*]Point the first window at /home/your-username.
[*]Point the second window at /media/your-storage-partition.
[*]Middle-click and drag a folder from the second window, into the first window, then release.
[*]From the context menu that pops up, choose "Link Here".
[/LIST]

Alternate way:
[LIST=1]
[*]Open a terminal (Applications -> Accessories -> Terminal)
[*]Type:
```
ln -s /media/your-storage-partition/somefolder /home/your-username/somefolder
```
[/LIST]

The fstab bind method was more-or-less explained in my previous post.

To edit fstab, press Alt+F2 and run```
gksu gedit /etc/fstab
```

Then just create a "bind" entry for every folder you want to bind. (Be careful not to modify any of the existing lines, you could cause your system to stop booting)

---

### Post by Oxwivi on 2010-12-02
Okay, got it! They seem easy enough. But if I dual-boot isn't the partition gonna be mounted by default? If not, I guess I know what to do. And do you think the permissions should be the same as the default settings I already have for the Download, Documents, etc folders? Or would any permission allowing me to access it will do?

---

### Post by WorMzy on 2010-12-03
You shouldn't really use the Windows system partition for your data storage partition, for the simple reason that you (or someone else) will be able to delete (accidentally or purposefully) important system files that Windows needs to operate. Ubuntu won't prevent you from doing so.

I just want to make sure that you know this.

For my data partition I mount it with "auto,uid=1000,gid=1000,umask=002", setting me as the owner and group, and giving myself full read+write+execute permissions and everyone else just read+execute.

> But if I dual-boot isn't the partition gonna be mounted by default?

Heh, no. I multi-boot (currently nine OS'), and there's rarely any cause to have any other system's partition mounted; having them all automount by default would be messy, cause slower boots, and be rather pointless. The reason fstab exists is so that you can specify which partitions you want to be mounted.

---

### Post by Oxwivi on 2010-12-03
For your first point, that is nothing to worry about, it's a personal laptop. I think I'd want to edit my files from Windows as well, so should I enter 0s?

I see what you mean

And finally, it's going x64 Ubuntu, any complications because of that? I've often seen guides have extra steps for 64-bit systems, hopefully this is isn't one of them - or is it?

---

### Post by WorMzy on 2010-12-03
Nah. Extra steps in 64-bit is basically just getting flash to behave itself. Oh, and if you want to run 32-bit applications (because there's no 64-bit equivalent or whatever) then you'll need to download the 32-bit libraries that it depends on.

> should I enter 0s?

For the last two fstab columns? Yes. Those columns are used to dump and fsck filesystems. Both of which are useless (afaik) in terms of NTFS filesystems.

EDIT: Did you mean umask value? Yes, 0 = all permissions. First number is the owner's permissions, second is the group's, and last is everyone else.

0 = read, write and execute
1 = read and write
2 = read and execute
3 = read
4 = write and execute
5 = write
6 = execute
7 = nothing

---

### Post by Oxwivi on 2010-12-03
Okay, I've got all I needed to ask about this topic. But something else still bugs me - I chose to install Windows on the whole HDD, so now I'm uncertain if it will cause problems once I install Ubuntu on it...

---

### Post by WorMzy on 2010-12-03
You can shrink the Windows partition with the Windows partitioner (XP: Start -> Programs -> Administrative Tools* -> Disk Management; probably something similar for Vista/7). You can also use the Ubuntu LiveCD, but, as it may not take fragmentation into account, it can cause data loss and sometimes even leave your Windows partition unbootable.

* You may need to [enable the administrative tools submenu]("http://www.technipages.com/xp-enable-administrative-tools-menu.html")

---

### Post by Oxwivi on 2010-12-03
Thanks for everything! I'll tag the thread as solved when everything is done without a hitch.

Cheers!

---

### Post by Oxwivi on 2010-12-05
Okay, so I got the the mounting with fstab all right. But when it came to the part about symbolic link, I arrived at a dead end. First, for example I want my download folder on Ubuntu to save merged with the download folder on WIndows; i.e. whatever I download, it'll be saved on the download folder on WIndows. With the middle-click business, I did not get what I should drag to what. So I tried to do it from the Terminal, and it looks like it got accepted. But when I'm on WIndows, the file I downloaded from Ubuntu doesn't appear.

Will fstab binding do the same thing I want? If so, how do I revert back the symbolic link? I'll try the fstab binding.

---

### Post by WorMzy on 2010-12-05
Does the file you saved from Ubuntu have "illegal" characters in it's name? i.e. \ / : * ? " < > |

If so, Windows won't be happy.

There's no way to switch symbolic links to binds, or vice versa. Symlinks are really just files which redirect your browser to the destination, whereas binds are more like doorways to another folder. This is how you create symlinks with nautilus:

[[IMG]http://img502.imageshack.us/img502/2205/linkcrz.th.jpg[/IMG]](http://img502.imageshack.us/img502/2205/linkcrz.jpg)
In this screenshot I have two nautilus windows open, one in my shared partition "/media/Terastore/Users/WorMzy", and the other in my home folder. I've middle-click-dragged the Documents folder from the shared partition's folder into my home area, then let go of the middle mouse button. Note that it asks me what I want to do with the folder I've just drag-dropped. "Link Here" is the option we want.

[[IMG]http://img63.imageshack.us/img63/2990/link2p.th.jpg[/IMG]](http://img63.imageshack.us/img63/2990/link2p.jpg)
After I choose "Link Here", it creates a file (which looks like a folder) called "Link to Documents", opening this file gives me...
[[IMG]http://img63.imageshack.us/img63/6375/link3o.th.jpg[/IMG]](http://img63.imageshack.us/img63/6375/link3o.jpg)
...the Documents folder.

Now, in the first and second screenshots, you can see a "Documents" folder in my home folder, this is in fact a bind to the same folder I've just linked:
[[IMG]http://img600.imageshack.us/img600/3928/link4.th.jpg[/IMG]](http://img600.imageshack.us/img600/3928/link4.jpg)

Of course, if you bind your shared documents folder over the top of your home folder's documents folder, make sure that you've already copied the content of the home folder's documents folder first. Once the other folder is bound there, the original documents will be inaccessible until the folder is unbound.

---

### Post by Oxwivi on 2010-12-05
Now forbidden charactes issue tehre, I downloaded Firefox's Windows installer to the Downloads folder.

From your screen shots, it looks like symbolic links is not what I'm looking for. Taking the example of the Downloads folder in my /home directory, I want all the files I save in it to go to the Downloads folder in the Wndows partition. From the screen shots it looks like the linking is a shortcut of Windows.

I am unsure as to what fstab binding does, can you explain more?

---

### Post by Mark Phelps on 2010-12-05
> **Oxwivi said:**
> ...I want all the files I save in it to go to the Downloads folder in the Wndows partition...
If you're including files you download while running Ubuntu, and if that Windows partition is your Win7 OS partition -- then NO, you do NOT want the files written there.

Writing to a Win7 OS partition from inside Ubuntu, as others have already told you, is asking for trouble -- possible data corruption in Windows, leaving the Win7 OS as unbootable.

IF you're going to write to a Windows partition from inside Ubuntu, then you need to have a separate DATA partition.  Those are not bootable, so you don't run the same risk as with Windows OS partitions.

---

### Post by WorMzy on 2010-12-05
It's not a Windows shortcut, it's a Linux symbolic link. ;)

I'm not too familiar with Windows shortcuts, but I believe they behave like files, rather than folders, so you can't use them for a lot of things. Symbolic links do not have any limitations, as far as I know.

For all intents and purposes, my "Link to Documents" and "/media/Terastore/Users/WorMzy/Documents" are one and the same. If I create a file in "/home/wormzy/Link to Documents", the file gets written to the NTFS partition, but it is available at both "/media/Terastore/Users/WorMzy/Documents/randomfile.txt" and "/home/wormzy/Link to Documents/randomfile.txt". The file is in one location, but is accessible from multiple addresses. This is the same behaviour that binding accomplishes. If symlinking isn't doing what you want, then binding will not be of any use to you.

---

### Post by Oxwivi on 2010-12-05
Can't we do symlink with an existing folder? And I'm not giving up just yet, tell me more about binding, please.

---

### Post by WorMzy on 2010-12-05
You just add an entry to your fstab file for each folder you want to bind, and where you want it bound.

I have five bound folders, Documents, Downloads, Videos, Pictures, and Music (Collection). Here's what the corresponding fstab entries look like:

```
#mount storage partition
UUID=7A5C94995C94522D                     /media/Terastore        ntfs-3g auto,uid=1000,gid=100,umask=002 0 0
#bind Music folder
/media/Terastore/Collection/              /home/wormzy/Collection none    bind                            0 0
#bind Pictures folder
/media/Terastore/Users/WorMzy/Pictures/   /home/wormzy/Pictures   none    bind                            0 0
#bind Documents folder
/media/Terastore/Users/WorMzy/Documents/  /home/wormzy/Documents  none    bind                            0 0
#bind Downloads folder
/media/Terastore/Downloads/               /home/wormzy/Downloads  none    bind                            0 0
#bind Videos folder
/media/Terastore/Videos/                  /home/wormzy/Videos     none    bind                            0 0
```

The only major difference between binding and symlinks is that you can't rename a bind point without updating your fstab file, otherwise the binding will fail.

Oh, and no, you can't create a symlink on top of an existing directory. If you use the command line and specify a directory as the "link name", it will create a symlink *inside* the folder, not on top of it.

---

### Post by Oxwivi on 2010-12-05
Well, now you know a limitation of symlink. And is binding done on top of an existing directory. I'm not getting what binding exactly does.

---

### Post by WorMzy on 2010-12-06
Yes, you must bind onto an existing directory.

After the bind, /home/wormzy/Documents behaves in the same way as "/home/wormzy/Link to Documents" does. Save a file to /home/wormzy/Documents, and it will be written to the NTFS partition, and will be accessible from both /home/wormzy/Documents, and /media/Terastore/Users/WorMzy/Documents.

---

### Post by Oxwivi on 2010-12-06
Hell yeah! This is exactly what I was looking for! My infinite thanks to you!

:guitar:

---

### Post by Oxwivi on 2010-12-06
Oh yeah, we don't need to mount the entire filesystem, do we?

---

### Post by WorMzy on 2010-12-06
Yes, you do. You have to mount the filesystem so that the folders you're binding are actually there. In my case, if /media/Terastore isn't mounted, then /media/Terastore/Users/WorMzy/Documents doesn't exist, and consequently will not be bound to /home/wormzy/Documents.

---

### Post by Oxwivi on 2010-12-06
All right, I think I'm ready do this. And again my thanks!

---

