---
title: "Cunning plans"
date: 2010-02-05
forum: General Help
---

### Post by mrkazoodle on 2010-02-05
Hi

Idea:
Since Gnome doesn't support a 'reboot into [OS]' feature, one has to use a script. [[COLOR="Blue"]Such a script[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2077414#post2077414") would be used in both windows (probably batch file) and linux (maybe python?) to replace the GRUB menu file and by that select the OS in which you want to boot on reboot. Both OS's should run another script on startup to put the default menu file back.


Problems:
- Ext4: there are no windows drivers available (yet)
(they would have to support reading and writing)
- GRUB2: the old GRUB menu was very easy, one had to edit just one file (!or replace it!). In GRUB2 things got complicated. I think you can edit grub.cfg and that it will still work, the reason why you should not edit it is just because it gets overwritten by running update-grub2. But I'm not sure. If 
- The script I found is used to edit the Grub file, not to replace it with another one. (This is but a minor problem.)

Solutions:
- Ext4 is mountable with Ext2fsd (not with Ext2ifs because of the inode size), it has been reported to work [[COLOR="Blue"]with extent enabled[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7692118#post7692118"), but I haven't tested it yet.
Here is a [[COLOR="Blue"]tutorial to mounting Ext4[/COLOR]]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/") drives in windows (which require disabling extent)
- If editing the grub.cfg would really be a bad idea, downgrading to GRUB (legacy)
- If I couldn't mount Ext4, trying to put Grub on a separate FAT/NTFS partition (is this possible with Grub/Grub2?) or else downgrading to Ext3 (= slower).

My questions to you:
- What do you think I should do?
- What should I definitely not do?
- You have a better idea?
- Aren't there really any scripts out there which give this 'reboot into...' functionality to Ubuntu? IMHO this can't be so extremely difficult. They would only have to replace some files (under the condition that an edited grub.cfg still works).

Now let's start the discussion (well, after I had lunch :D)

---

### Post by mrkazoodle on 2010-02-05
Here's some extra documentation:

Another script (Grub legacy): [http://robotics.caltech.edu/~klk/linux.htm](http://robotics.caltech.edu/~klk/linux.htm)
A command to set the OS to boot into: [http://ubuntuforums.org/showthread.php?t=794050](http://ubuntuforums.org/showthread.php?t=794050)

```
sudo grub-set-default [NUMBER OF CHOSEN OS] && reboot
```
this is probably Grub legacy only.
In [this thread]("http://ubuntuforums.org/showthread.php?t=1195275") there will probably more on that, but I don't have time to read it right now.

---

