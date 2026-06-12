---
title: "make links between ext4 and fat32"
date: 2012-03-12
forum: General Help
---

### Post by NewUserFF on 2012-03-12
it is used in android phone. Because my ROM is big enough(around 8G), and my SDCard has been full with various files, so i want to link a big file stored in ROM to SDCard so as to save the treasure space of SDCard( the big file cannot be identified by a software except it is in /sdcard patition ) first i take an test to validate the method: try to link a file /data/test.mp3 to /sdcard/test_fat32.mp3, then in the terminal (#su), i tried to make a symbolic link like this :

```
ln -s /data/test.mp3 /sdcard/test_fat32.mp3
```

but failed:

**_ln: /sdcard/test_fat32.mp3: Operation not permitted_**

Googling for a while, and i found that i cannot create symbolic links with fat32, i dont want to format the SDCard to ext4, because i want to make such an app to share with my friends. you surely cannot demand everyone of the format, what's more, maybe many apps cannot identify ext4 files. does anyone have a good idea to realize it? or some other ways to access inner files and fake the app that it is a file in /sdcard? any help appreciated!

---

### Post by HavarN on 2012-03-12
Have you rooted your phone?
I believe you will need root access to create a symbolic link in a system folder.

However, do you want to create a symbolic link on the sd-card? Then you need to format it using another filesystem. I don't think fat32 supports symbolic links. However to use an sdcard which is formatted with another filesystem, you will need a rooted android phone.

If you want to create the symlink in the /data folder, you should instead do:```
ln -s /sdcard/test_fat32.mp3 /data/test.mp3
```

---

### Post by NewUserFF on 2012-03-12
> **HavarN said:**
> Have you rooted your phone?
I believe you will need root access to create a symbolic link in a system folder.

However, do you want to create a symbolic link on the sd-card? Then you need to format it using another filesystem. I don't think fat32 supports symbolic links. However to use an sdcard which is formatted with another filesystem, you will need a rooted android phone.

If you want to create the symlink in the /data folder, you should instead do:```
ln -s /sdcard/test_fat32.mp3 /data/test.mp3
```

Thanks, i have rooted my phone. i know that i cannot create a symbolic link on fat32 system, so i am looking for some ways to realize the link. IOW let the apps access the ROM files according to the simple /sdcard mount, just as what i referred to above. do you have some other good ideas?

---

