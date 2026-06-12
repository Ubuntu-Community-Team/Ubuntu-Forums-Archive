---
title: "mounted drive no longer repsonding correctly"
date: 2010-09-27
forum: General Help
---

### Post by rebeltaz on 2010-09-27
I have a secondary harddrive that is auto mounted through fstab at startup in the /mnt/media_drive folder. I have not had any problems out of it until today. 

I was trying to get the computer to act as a PS3 media server. I installed pms-linux, couldn't get it working, removed that, installed ushare, didn't like that, uninstalled that and reinstalled pms-linux. Now the PS3 sees the folder, but nothing else does. 

When I ls -l the /mnt/media_drive folder, I get this:

```

derek@shop:~$ ls /mnt/media_drive -l
ls: cannot access /mnt/media_drive/audio books: Permission denied
ls: cannot access /mnt/media_drive/playlists: Permission denied
ls: cannot access /mnt/media_drive/Christmas: Permission denied
ls: cannot access /mnt/media_drive/DVD_temp: Permission denied
ls: cannot access /mnt/media_drive/OTR: Permission denied
ls: cannot access /mnt/media_drive/dont_play: Permission denied
ls: cannot access /mnt/media_drive/shop_data.bak: Permission denied
ls: cannot access /mnt/media_drive/MP3s: Permission denied
ls: cannot access /mnt/media_drive/photography: Permission denied
ls: cannot access /mnt/media_drive/music.videos: Permission denied
ls: cannot access /mnt/media_drive/CDs: Permission denied
ls: cannot access /mnt/media_drive/delete: Permission denied
ls: cannot access /mnt/media_drive/lost+found: Permission denied
ls: cannot access /mnt/media_drive/temp: Permission denied
ls: cannot access /mnt/media_drive/Halloween: Permission denied
ls: cannot access /mnt/media_drive/test discs: Permission denied
ls: cannot access /mnt/media_drive/videos: Permission denied
ls: cannot access /mnt/media_drive/~cd-r.tmp: Permission denied
ls: cannot access /mnt/media_drive/TV theme songs: Permission denied
ls: cannot access /mnt/media_drive/Classical: Permission denied
ls: cannot access /mnt/media_drive/comedy: Permission denied
ls: cannot access /mnt/media_drive/sbnews.tmp: Permission denied
total 0
d????????? ? ? ? ?                ? audio books
d????????? ? ? ? ?                ? ~cd-r.tmp
d????????? ? ? ? ?                ? CDs
d????????? ? ? ? ?                ? Christmas
d????????? ? ? ? ?                ? Classical
d????????? ? ? ? ?                ? comedy
d????????? ? ? ? ?                ? delete
d????????? ? ? ? ?                ? dont_play
d????????? ? ? ? ?                ? DVD_temp
d????????? ? ? ? ?                ? Halloween
d????????? ? ? ? ?                ? lost+found
d????????? ? ? ? ?                ? MP3s
d????????? ? ? ? ?                ? music.videos
d????????? ? ? ? ?                ? OTR
d????????? ? ? ? ?                ? photography
d????????? ? ? ? ?                ? playlists
d????????? ? ? ? ?                ? sbnews.tmp
d????????? ? ? ? ?                ? shop_data.bak
d????????? ? ? ? ?                ? temp
d????????? ? ? ? ?                ? test discs
d????????? ? ? ? ?                ? TV theme songs
d????????? ? ? ? ?                ? videos

```

I have to sudo ls -l the directory to see the permissions and to get rid of the 'Permission Denied' errors. Additionally, I used to be able to mount the folder on a networked laptop. Now when I try to do that, I get a 'mount error(12): Cannot allocate memory' error. 

I tried running e2fsck and uninstalling pms-linux but I still have the same problem. I hope someone can help me out here and tell me what I did wrong! Thanks...

[edit] 
Oh, and when I do a sudo ls -l on that directory, it shows me as being the owner, not root.

---

### Post by rebeltaz on 2010-09-27
I figured it out in case anyone else needs it:

permissions were set to to rw-rw-rw- on the /mnt/media_drive folder. For some reason, that folder needs execute permissions set to be able to access it correctly. I'm not sure how the permissions got changed, but ... there you have it.

---

### Post by amauk on 2010-09-27
just a side note
Any folder you wish a user to access needs to be executable

Navigating into a folder = "executing" the folder

---

### Post by rebeltaz on 2010-09-27
> **amauk said:**
> just a side note
Any folder you wish a user to access needs to be executable

Navigating into a folder = "executing" the folder

OK... I can see that - Thanks...

---

