---
title: "Squeezebox Server won't add music"
date: 2010-05-24
forum: General Help
---

### Post by midna on 2010-05-24
I'm having some trouble getting squeezebox server to scan my music directory. Squeezebox server is installed and running ok, but it refuses to add my music directory as the folder for the "Music Folder". If I try to add it manually I get the following message:

"Invalid value "/media/raid/Music/" for audiodir"

My music is all on /media/raid/Music/ which is part of a 3 drive mdadm array. XBMC can see and play all music fine. Samba shares everything correctly. I assumed that for some reason the permissions were not right, but I don't know if that is truly the case. I added the "squeezeboxserver" user to the "users" group, but got no where.

Please help! Thanks!

```
cd /media/raid/
ls -la

drwxrwxr-x  4 media users  4096 2010-02-03 18:38 Music

cd Music/
ls -la

drwxrwxr-x  4 media users 4096 2010-02-03 18:38 .
drwxrwxrw- 13 media users 4096 2010-05-24 00:34 ..
drwxrwx--- 41 media users 4096 2010-05-23 19:43 flac
drwxrwx---  3 media users 4096 2010-02-01 14:09 mp3

cat /etc/fstab

/dev/md5        /media/raid     auto    errors=remount-ro       0       0
```

---

### Post by midna on 2010-05-24
bump...

---

### Post by fimbar on 2010-09-13
Hi,
 
Are you still struggling on this? I've just followed this guide to [**install squeezebox server**]("http://havetheknowhow.com/Install-the-software/Install-Squeezebox-server.html") and had similar issues getting it to see my music.
 
However, this is because I was manually specifying the music folder location into the web interface ([http://IPaddressOfyourServer](http://IPaddressOfyourServer)).
 
Instead, if you go to Settings -> Music Folder and then click the Browse button against the Music Folder and then try and navigate to the desired location you'll soon see whether squeezebox server can actually see the files or not. If you can drill down into your music then squeezebox server can see it. If you can't then it can't either.
 
The permissions on your main folders look fine (although personally I'd "chmod a+r" on them). However, you've not mentioned the permissions on the folders within them. Are they also owned by the users group? What permissions do they have?
 
You mentioned samba. Is your music stored on a different machine to squeezebox server?

---

### Post by elitenoobboy on 2010-11-15
Is there anyway to run squeezebox as a certain user, instead of adding read permissions for everyone else?

---

