---
title: "fsck error - Couldn't fix parent - A Solution"
date: 2009-09-08
forum: General Help
---

### Post by ahalin on 2009-09-08
I got the following error (abbreviated to the relevant bits) after running manual fsck checks of various kinds because my Ubuntu and Mepis wouldn't start, "disk check forced", and all that (there are plenty of other posts about how to do a manual fsck, so not shown here):

[I]e2fsck -f -y -v /dev/sda2  	

Pass 3: Checking directory connectivity

'..' in /.Trash-1000/files/Loony Tunes- Los Benjamins/M-/M-]M-. R & H M-/M-]M-. (245807) is <The NULL inode> (0), should be /.Trash-1000/files/Loony Tunes- Los Benjamins (49362).

Fix? yes

Couldn't fix parent of inode 245807: Couldn't find parent directory entry.

MyDocuments: ********** WARNING: Filesystem still has errors **********[/I]

All the errors were the same, ie, "orphans", in the .Trash. I tried all sorts of fsck and e2fsck checks while dismounted, live cds, etc. 

There were some apparently successful fixes at [http://bitc.bme.emory.edu/~lzhou/blogs/?p=70](http://bitc.bme.emory.edu/~lzhou/blogs/?p=70) for restoring ownership and finding Mum and Dad (the parent directory entry of offending files) but it's pretty complicated stuff. 

None of the help on the www referred to something that was in the .Trash but I got to thinking that if the orphans ***were*** in the bin (trash) I could just delete them. So, using Parted Magic as my live CD just because it has the tools and is quick, using a terminal as root (in Parted Magic this is automatic, in other distros you would have to use *sudo* before the commands shown below):

*mount /dev/sda2* (You could also do this with a right mouse click n "Mount" in the file manager graphical user interface)

Then navigate to the .Trash via the file manager (enough of the command line thanks, I could not cd to .Trash, perhaps because it is a hidden file) and manually delete everything in it. I actually copied them to somewhere else ***just*** in case. Then  

*umount /dev/sda2* [Unmounting the drive that you want to check is very important!!!  Insert your drive name after "dev/" eg dev/hda4  .You could also do this with a right mouse click n "Unmount" in the file manager graphical user interface]

[/I]e2fsck -y -f -v /dev/sda2[/I]

and then 

*e2fsck -n -f -v /dev/sda2*

Voila, no errors!! I rebooted and all was well. 

I am feeling quite chuffed that I worked it out pretty much by myself and didn't have to reinstall anything. Trust me, I was about to! 

Just a note, because this was "My Documents" or "Home" drive, I used another operating system to back it up before I started fsck-ing.

Anyway, I hope this helps someone else. 

John

---

### Post by ahalin on 2009-09-08
That should say:

*e2fsck -y -f -v /dev/sda2*

without the [/i] at either end. Sorry!

---

