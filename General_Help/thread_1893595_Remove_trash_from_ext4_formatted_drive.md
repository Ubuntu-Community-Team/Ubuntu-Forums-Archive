---
title: "Remove trash from ext4 formatted drive"
date: 2011-12-10
forum: General Help
---

### Post by gennatolls on 2011-12-10
I have a second HDD that I use to store my movies, pictures, and backups so I don't fill up my boot drive. Problem is when I delete something by right clicking and selecting move to trash it goes to .Trash-1000/files or .Trash-1000/info and the trash is never cleaned when I unmount the drive. For now I just use terminal to :
rm * /media/MyHDD/.Trash-1000/files which isn't too inconvenient. Am I missing something here, I thought it should be cleaned upon unmounting it like my drives do in Mac. Thanks for input.

---

### Post by fragos on 2011-12-10
Every drive partition and has it'd own trash file for each user. Even on a single user system you still have two users, you and root. The trash icon on your desktop only reflects trash for the logged in user for the disk partition that holds their home folder. Emptying trash is always a manual process and is only for one trash container. Trash is safety measure encase you mistakenly delete something it can easily be restored by the user. To deal with I've in Nautilus enabled include delete command for both myself and for nautilus as a root user. Deleting things from my home folder I use the trash function. For files on other partitions or when operating as root/admin I use the Delete option I enabled with the operational proviso that I double check myself when using the delete function since any file deleted that way isn't easily restored. It is my habit to empty the trash bin when I shutdown for the evening. I find this procedure workable for me.

---

