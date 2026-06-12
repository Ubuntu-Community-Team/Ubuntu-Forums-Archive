---
title: "&quot;Root&quot; keeps taking over files......."
date: 2009-09-04
forum: General Help
---

### Post by Thanh-BKK on 2009-09-04
Hello.

Ubuntu 9.04 Jaunty here with a strange (in my opinion) issue.

Every now and then some files or folders are suddenly owned by root and no longer accessible by myself as a normal user. What causes this and, more important, how can it be prevented..? 

This happens specially after using Nautilus to copy/paste items from /home to a different volume for backup purpose, many items located within /home/some_other_folders are then suddenly "owned" by root when before they were owned by myself.

This is very annoying because not only does it cause the dreaded "User's $HOME/.dmrc file is being ignored" problem but also prevents virtual machines from being started (located in /home/virtual) and of course prevents files from being copied or opened. 

Is there a way to stop this from happening..? 

Kind regards.....

Thanh

---

### Post by kiridude on 2009-09-04
maybe because you are opening nautilus as root and therefore any changes you make are then owned by root.

---

### Post by Thanh-BKK on 2009-09-04
Hi.

Nope i do not open Nautilus as root, and i don't make any changes either - i just copy files from /home to /media/Backup (for example). 

Kind regards.....

Thanh

---

### Post by mcduck on 2009-09-04
Couple of things come to mind. First, if you run any graphical apps as root, *never* do that with "sudo, always use "gksudo". "sudo" doesn't load rot's environment correctly for GUI applications, causing you to sun the program with root permissions but using your normal user's configuration files.

Same applies to opening root terminal session with "sudo su" or "sudo -s". you should use "sudo -i" instead.

Then comes the aspect of the file systems.. Are both source and target directories on some Linux filesystem? For example if your backup directory is on a NFTS drive it won't be able to maintain file ownerships and permissions and instead uses those defined at mount time for the whole drive (which would usually result in root as owner).

If you need to make backups to non-linux filesysems create a .tar archive of your files and backup that, the archive will maintain the ownerships & permissions.

---

### Post by Thanh-BKK on 2009-09-04
Hi.

Aha! I think that's it... the target volume (/media/Backup) is indeed a NTFS volume. 

The other possibilities don't apply as i never used either "sudo su" or "sudo -s".

However creating tar files is not an option - as i do backup my entire /home partition which is like 40 GB, i don't have that much spare space to put such a tar file. I don't need specific permissions for the files that sit in the NTFS volume - those are only to be used in case my system HDD dies again :)  

So basically when i copy/paste files to the NTFS volume then the original files (in /home) get the same right/permissions etc as the whole /dev/sda, yes? Hmm so i guess i will need to stick to manually resetting the permissions after each backup..... well i don't backup that partition too often anyway as there is no data there, only configurations and settings and they don't change all too often, only my .mozilla folder is very important as my e-mail and my bookmarks are there. 

I would make the /media/Backup also ext3 however i have enough annoyance with "routine disc check" already, which of course always comes just then when i have absolutely no time for it. 

Best regards.....

Thanh

---

### Post by mcduck on 2009-09-04
> **Thanh-BKK said:**
> Hi.

Aha! I think that's it... the target volume (/media/Backup) is indeed a NTFS volume. 

The other possibilities don't apply as i never used either "sudo su" or "sudo -s".

However creating tar files is not an option - as i do backup my entire /home partition which is like 40 GB, i don't have that much spare space to put such a tar file. I don't need specific permissions for the files that sit in the NTFS volume - those are only to be used in case my system HDD dies again :)  

So basically when i copy/paste files to the NTFS volume then the original files (in /home) get the same right/permissions etc as the whole /dev/sda, yes? Hmm so i guess i will need to stick to manually resetting the permissions after each backup..... well i don't backup that partition too often anyway as there is no data there, only configurations and settings and they don't change all too often, only my .mozilla folder is very important as my e-mail and my bookmarks are there. 

I would make the /media/Backup also ext3 however i have enough annoyance with "routine disc check" already, which of course always comes just then when i have absolutely no time for it. 

Best regards.....

Thanh

You should be able to create the .tar archive directly in the target location (and of course you can compress the archive into .tar.gz at the same time to save even more space). Although I'm not sure if there's some graphical way to do this. But the tar command run from a terminal will definitely allow you to create the archive directly in the target directory so you won't need any more disk space to do that than you need to just copy the files there.

What comes to the fsck, the frequency is fully configurable and checking can even be completely disabled through /etc/fstab if you want to.

---

