---
title: "cleaning up files on MP3"
date: 2011-08-08
forum: General Help
---

### Post by cowboy7305 on 2011-08-08
I have a small mp3 mp4  4gig 
i have deleted files from it  or so i thought
when i go to view hidden files there is a trash file in that file all mys deleted files are showing ,when i try to delete them i get permission denied
some thing to do with read right only , why is this so its not an operating system only a mp3 player

---

### Post by Basher101 on 2011-08-08
if you want to completeley remove everything, reformat it using Gparted to FAT32

---

### Post by fdrake on 2011-08-08
> **cowboy7305 said:**
> I have a small mp3 mp4  4gig 
i have deleted files from it  or so i thought
when i go to view hidden files there is a trash file in that file all mys deleted files are showing ,when i try to delete them i get permission denied
some thing to do with read right only , why is this so its not an operating system only a mp3 player

because you are not probably the owner of those files (the person/user who put those files in the mp3) . This happens even if you put those files from another computer or os.
to change ownership do:
sudo chown your_username "/media/your_player" 
or
sudo chowm your_usrname "/mnt/your_player"

depending on where your player is mounted

---

### Post by fdrake on 2011-08-08
> **Basher101 said:**
> if you want to completeley remove everything, reformat it using Gparted to FAT32

reformatting the media MAY cause the player not to work. He MAY need to reinstall the players files again.

---

