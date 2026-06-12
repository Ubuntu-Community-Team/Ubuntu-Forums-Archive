---
title: "The folder contents could not be displayed (Invalid argument)"
date: 2009-12-19
forum: General Help
---

### Post by quiteconfused on 2009-12-19
Ubuntu 9.10 (Karmic) Nautilus - The folder contents could not be displayed (Invalid argument)

Nautilus reports the following error when I attempt to view the contents of a folder:  The folder contents could not be be displayed (Invalid argument).  In this case, I am unable to view or access the contents of the folder.

The problem *seems* to be localized to the folders that contain a larger number of files.

Specifically, I am accessing a FreeNAS share with multiple subfolders (at various levels) each containing mainly .jpg (photo) files.  I can access most all of the sub-folders and files just fine.  I get the error when I try accessing the two folders that contain a larger number of files.  These folders contain 1889 files (179 MB) and 9765 files (9.08 GB) respectively.

All of the folders on this share were placed on the FreeNAS server at the same time via an XP machine.  I remain able to access these folders via XP without issue, but not via Ubuntu.  The other folders appearing at the same level in the hierarchy are accessible via Ubuntu and have the same permissions.

I am navigating to these folders using Nautilus (i.e., Gnome menu <Places><Network><Server><Share><folder>) using an up-to-date install of Karmic.

I would really like to have easy access to these files from my Ubuntu machine, but am stumped as to how to solve.  Any help is appreciated.

---

### Post by dcstar on 2009-12-19
> **quiteconfused said:**
> Ubuntu 9.10 (Karmic) Nautilus - The folder contents could not be displayed (Invalid argument)

Nautilus reports the following error when I attempt to view the contents of a folder:  The folder contents could not be be displayed (Invalid argument).  In this case, I am unable to view or access the contents of the folder.

The problem *seems* to be localized to the folders that contain a larger number of files.

Specifically, I am accessing a FreeNAS share with multiple subfolders (at various levels) each containing mainly .jpg (photo) files.  I can access most all of the sub-folders and files just fine.  I get the error when I try accessing the two folders that contain a larger number of files.  These folders contain 1889 files (179 MB) and 9765 files (9.08 GB) respectively.

All of the folders on this share were placed on the FreeNAS server at the same time via an XP machine.  I remain able to access these folders via XP without issue, but not via Ubuntu.  The other folders appearing at the same level in the hierarchy are accessible via Ubuntu and have the same permissions.

I am navigating to these folders using Nautilus (i.e., Gnome menu <Places><Network><Server><Share><folder>) using an up-to-date install of Karmic.

I would really like to have easy access to these files from my Ubuntu machine, but am stumped as to how to solve.  Any help is appreciated.

Are you 100% sure that these folders do not contain any filenames that are illegal under Linux?

---

### Post by quiteconfused on 2009-12-20
> **dcstar said:**
> Are you 100% sure that these folders do not contain any filenames that are illegal under Linux?

I took a look from XP explore at one of the folders I that I cannot view or access (with option to view hidden files is shown).  Files in the folder are:
  Picture 009.jpg ... Picture 1898.jpg
No other files are listed.

So (unless I'm missing something) invalid file name does not appear to be the issue.

Other ideas?

---

### Post by fjm03 on 2009-12-20
[I]Other ideas?

[/I]You bet. It's an issue with 9.10. Been asking for help for weeks with no results.  Here's what I do know:

1) It's not a file size or illegal name issue. 
2) It's not a kernel issue. 9.04 runs the same kernel (-17)
3) It could be a partition issue. Ext 3 v Ext4. 9.04 is 3, 9.10 is 4
4) It's not a Samba issue. Same dependencies on both distros.
5) It's most probably simply code within 9.10. it's by design and no one wants to fess up.

I've gone back to 9.04 where samba transfers work and VMware Server is stable.

---

### Post by quiteconfused on 2009-12-20
> **fjm03 said:**
> 
3) It could be a partition issue. Ext 3 v Ext4. 9.04 is 3, 9.10 is 4


Its probably not a partition issue.  I upgraded from 9.04 which was installed with the default partition type.

Disappointing ...

---

### Post by rwperkinsjr on 2009-12-30
This is a major problem. I have been looking for a fix for about a week now. Getting ready to scrap it all. If the network, trash, mounter and other components aren't working then why would I want to use this system.

Everything appeared to be working just right until recent updates. I also built and installed GTK2. Could this have caused my errors?

I know I am geting tired of this though. Every time I update Ubuntu i get new errors. Man I didn't want to format and reinstall this whole system again. :(

---

### Post by rmdrake on 2010-02-04
I too am having problems connecting to FreeNAS samba shares with 9.10. I can connect fine with windows, but not via Nautilus with:
```
smb://freenas/share
```

Furthermore, attempts to connect via the Nautilus convieniece method seem to temporarily seize up the freenas box.

I can connect to the freenas manually with: *(Example)
```
mount -t smbfs -o username=<username> //freenas/share /mnt/share
```

In order to do this you may need to:
```
sudo apt-get install smbfs
```

---

### Post by Bullwinkle_Moose on 2012-04-29
This problem still exists in Ubuntu 11.04 (Natty) :mad:

---

### Post by Bullwinkle_Moose on 2012-04-29
This issue is also discussed here (but with no resolution, unfortunately):

[http://askubuntu.com/questions/127360/why-cant-i-access-a-directory-on-another-device-if-it-has-more-than-around-500](http://askubuntu.com/questions/127360/why-cant-i-access-a-directory-on-another-device-if-it-has-more-than-around-500)

---

