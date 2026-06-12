---
title: "Cannot retrieve files with ubunto 12.04 desktop"
date: 2012-05-24
forum: General Help
---

### Post by popsrozie on 2012-05-24
I'm an absolute ubuntu newbie with limited computer skills. I want to use ubuntu but am having difficulties. My first project is to try to retrieve files from an unbootable hard drive running Windows XP using a ubuntu live CD. 

I've downloaded ubuntu 12.04 desktop and burned the image to a CD correctly (I think). I loaded it into the pc and selected "Try ubuntu without installing" - and that's where the problem starts.

The online instructions read "select Places/Computer - this should show you your hard drive"  But no such menu exists as far as I can see. 

I need to know whether there is some way of getting ubuntu to recognise the other drives on the pc, and how to open a new terminal in order to write the commands, etc.

I've looked for a guide for this but without success. All help gratefully received.

---

### Post by Mark Phelps on 2012-05-24
If the Windows filesystem on the drive is damaged, Linux will NOT mount the partitions on the drive.

You didn't tell us what version of Ubuntu the instructions are designed for -- but it's clearly NOT version 12.04.

In the current version, you click the "home" icon at the top-left of the navigation bar on the left.  That will display a list of partitions that Ubuntu can see.  You click one of the partition icons in that list to mount that partition.

If you see no partition icons in the list, that's most likely due to the problem I indicated at the top of this post.

---

### Post by popsrozie on 2012-05-24
Thanks for that. I'll try what you suggest. The instructions come from here;

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)


with a link to the ubunto download page. Maybe I missed something!

---

### Post by popsrozie on 2012-05-24
The bar on the left of my screen includes top left 'Dash Home', below it;'Install', and below that; 'Home Folder'.

Nothing I click on seems interested in showing me the hard drive or anything other than what is on the CD.

Maybe the hard drive is completely shot but I would have thought there was some way to recognise its existence even if it could not be mounted.

Seems like I'll have to try a non-ubuntu rescue package.

Thanks again anyway.

---

