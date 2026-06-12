---
title: "Expanding home and root folder"
date: 2010-12-09
forum: General Help
---

### Post by pranavk_uict on 2010-12-09
I have a bit of situation. First thing I should tell is I installed Ubuntu just to try it out and now I am in love with it.
I have attached a screenshot from the disk utility. The problem is I want to increase my home and root partitions but without loosing any data or customizations that I made in Ubuntu. I seriously dont wanna mess up my windows drive because there is lots of important data (my work basically) and softwares.
I tried using gparted live cd to see what I can do to resize my home drive and found out that I cant resize my home folder because its at the end (as you can see in the screenshot). Also I got an waring message when I tried to move my root drive to left (so that I can resize my home folder then. 
Please, explain to me in great detail (I dont know much about this partitioning stuff) that how is it possible for me to do this?

---

### Post by zvacet on 2010-12-09
All I know is that Windows 7 have utility for resizing partition.Because I don´t use Win I can not tell you more then try to resize partition from Windows.After that you will be able to move your root to the left and make space for home.

---

### Post by joehoward on 2010-12-09
Hello pranavk_uict,

Windows 7 (and vista, for that matter) does have a repartitioning tool which I find more user-friendly than Gparted.
Before you repartition, it is always a good idea to defragment your HDD.  Click Start, then search "Disk Defragmenter".  It'll show up under Programs.
This is next step is **very **important: ALWAYS backup your stuff before you do anything with your hard disk.  I have repartitioned my disk many times and never had a problem, but there is always a chance something terrible could happen.

Now that you have prepped your disk, it's time to start the partitioning.
Right-click on the "Computer" icon on your desktop and click "Manage".  You will need administrative rights.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177961&stc=1&d=1291937997[/IMG]
Once the Window shows up, click "Disk Management" under the "Storage" tree in the left panel.  A list will show up with all your disks.  you will see a few more partitions in your window because I don't have Ubuntu on this machine.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177960&stc=1&d=1291937997[/IMG]
Right-click the block (or text) with C: on it, then press "shrink volume".  After your machine queries space available for shrink, dialogue box will ask you how much you want it to be shrunk.  enter the new value.  Remember that it is measured in MB.  Click the "shrink" button to commit changes.
After it is all done, the disk management should refresh and you will see a black bar labeled "unallocated".  If you can see that, everything went well.  Now, you need that boot disk you mentioned in your post - from now on, we will need Gparted's ability to work with linux partitions.

from here on, you can use the instructions on this page: [http://www.simplehelp.net/2008/11/04/how-to-resize-linux-partitions-using-gparted/]("http://www.simplehelp.net/2008/11/04/how-to-resize-linux-partitions-using-gparted/").
I don't have screenshots of Gparted, but this page does a good job explaining the next steps.  It goes through the entire process of shrinking other partitions using Gparted, but you only need to worry about resizing/moving your partition onto the unallocated section you made earlier (look at number 13 on the directions).

I hope this helps!  Good luck!

---

