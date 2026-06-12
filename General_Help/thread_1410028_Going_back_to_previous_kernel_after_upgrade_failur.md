---
title: "Going back to previous kernel after upgrade failure (from 2.6.31-17 to 2.6.31-19)"
date: 2010-02-18
forum: General Help
---

### Post by daka90 on 2010-02-18
Hi everyone,

I upgrade to -19 kernel and as a lots of people ran through troubles...
After launching my computer and choosing ubuntu from the computer display immediatly the grub1.97~BETA4 SHELL
No booting for me too
I've read like 50 pages and figured that going back too -17 was a solution very fine for me.
 so I've looked for a detailed process (found [here]("http://www.omaregan.com/?p=583") )
 applied it but I continuously get a message like 'the magical number is invalid'.
I think the root directory is "broken"...
for root=/dev/sd** the directory simply doesn't exist 

to check my partition I did 
     Code:
     sh:grub> ls -l 
and got info on device loop0, UUID
 Device hd0, partition hd0,1, type ntfs,UUID

nothing more when I checked the mapdevice file partion are suposed to be maped in /dev/sda

but in /dev there isn't any sd** file 

...... so don't know what to do next...

And one last thing here:

     Code:
     loop=/ubuntu/disks/root.disk ro 
IF /ubuntu is supposed to be an existing directory, this is not here too....

Thanks in advance, great forum !
bye

************ --> [look here for explanation]("http://ubuntuforums.org/showthread.php?p=8846014&posted=1#post8846014")

---

