---
title: "Connecting to windows share from Ubuntu - permission problem"
date: 2011-07-17
forum: General Help
---

### Post by exup1000 on 2011-07-17
Hi
I have a couple of window boxes on my small work group.
I can easily connect to these shares from my Ubuntu machine and run backups etc.
Trouble is for the first time I have tried to copy files to the windows share and I am not able to.

The shares root folder and the second child folder are semi read only. By semi I mean I can delete, rename copy any file or folder, but not create from scratch a file or folder or paste.
But all the child file and folders level 3 and on wards I have full access.

I thought it was a windows permission problem, but I did a test from another windows machine and can do everything ok.

I am connecting as the administrator of the windows box using its credentials, when I am on the machine I have full modify rights to all files and folders.

This has got me perplexed? Not sure what to try next.
The only visual thing I can see is a padlock on the folder when browsing with nautilus. But when I go to check permissions its unable to determine security.

Is there a command line entry that can show effect permissions across an SMB share. 

cheers

---

