---
title: "Moving and sharing the places folders"
date: 2011-08-09
forum: General Help
---

### Post by solouko on 2011-08-09
Hello everyone!
Current situation: two drives, Ubuntu 10.4 64bit installed and running on one drive, other drive blank and formatted for NTFS.

What I want: When I download of save anything I want it to be stored automatically on the NTFS drive with no encryption and have the 'Places' folders point to the corresponding folders on that drive.  

Why: simple, I'm planing to dual boot Ubuntu and windows 7, and the NTFS folder will be the 'My Documents' Drive, this is why it's formatted NTFS.  There will be over 100GB on files I'll need both OS's to have access too and I would like it to be automatic to save duplication.

Also, if I need to, I want to be able to take that documents drive from the Ubuntu PC and be able to recover the info with an inferior windows OS... because that's what I have lying round in an emergency.  


Any tips, links, advice, greatly appreciated.
Regards Solouko :)

---

### Post by ajgreeny on 2011-08-09
You can not have your /home folder or partition on a NTFS partition, as it does not allow the required linux permissions, so you will need that to be on a standard linux formatted partition (ext4 by default).   However, you can easily make a NTFS partition for all your data files, including things you download.

I am not sure about the NTFS folders for Documents, Music, etc etc. appearing in the places menu by default, though I can not see any major problem if you add them yourself as bookmarks, but you may need to either remove the existing ones, which do automatically point to the /home folders.

Better, perhaps, would be to make links from the existing /home folders to the same named folders in your NTFS data partition so that the files in the NTFS folders will appear to be in the /home folders.

---

### Post by solouko on 2011-08-10
Thank you, this is a great help, I'll give it a try today and edit this post with the results.
Although, being a novice user there will be a lot of googling and trial 'n error figuring out how to accomplish this. :P

---

