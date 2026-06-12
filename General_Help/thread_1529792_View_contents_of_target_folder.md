---
title: "View contents of target folder"
date: 2010-07-12
forum: General Help
---

### Post by Steve Francis on 2010-07-12
I have a ntfs logical drive which has a folder on it called My Music, which contains a lot of my mp3 files. The location is:
/media/Data/Personal/My Music

I have a home drive with a folder on it called Music. The location is
/home/steve/Music

Is there any way that, when I open the folder called 'Music' in Nautilus, I see the contents of the ntfs folder called 'My Music'?

(Ubuntu version is 10.04)

---

### Post by geirha on 2010-07-12
Yes. Several ways to achieve it depending on preference or what you actually need it for.

1 (easiest): Make /home/steve/Music a symlink pointing to /media/Data/Personal/My Music
```
rmdir /home/steve/Music && ln -s "/media/Data/Personal/My Music" /home/steve/Music
```

2: Make the nautilus bookmark labeled "Music" point to /media/Data/Personal/My Music. Open a nautilus window, then in the left margin, delete the Music bookmark, create a new bookmark named Music that points to /media/Data/Personal/My Music

3: Use mount-binding; mount a directory on another directory.
One time use:
```
sudo mount -o bind "/media/Data/Personal/My Music" /home/steve/Music
```
To make it permanent, add a line in /etc/fstab:
```
# Somewhere after the line(s) that mounts /media/Data and /home (if any)
/media/Data/Personal/My\040Music /home/steve/Music none bind 0 0
```

---

### Post by Mr. Gnome on 2010-07-12
Creating a symbolic link to the target folder should work exactly like you wanted.

```
ln -s [TARGET] [LINK]
```

---

### Post by Steve Francis on 2010-07-12
Thanks for your help, guys. I'll experiment with your suggestions.

---

### Post by Steve Francis on 2010-07-14
In the end, I used Mr. Gnome's suggestion:

```
ln -s "/media/DATA/Personal/My Music" /home/steve/Music
```

Note to self: For some reason it didn't work if DATA was in lower case.

---

