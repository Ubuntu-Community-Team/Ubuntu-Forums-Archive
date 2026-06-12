---
title: "Linux and ntfs drives"
date: 2012-01-03
forum: General Help
---

### Post by Vipercatt on 2012-01-03
I have a media pc which has several drives formatted using ntfs and I have just built a server using useros which is Ubuntu based . I want to take the drives out of the media pc which have my movies only on them and use them in the server box. Will u untuntu allow me to use these drives as they are or do they have to formatted Linux style to use them for file sharing ?

---

### Post by Canime on 2012-01-03
You can file share by setting up an FTP server from your computer. I've had mixed success with this sort of thing.

---

### Post by Lars Noodén on 2012-01-03
Ubuntu can read NTFS, but be warned that it is a garbage file system and you will not get the performance that you would with a decent file system.  Further, you will have to periodically manually defrag those partitions to eek out a little better performance.  If possible, update them to EXT3 or EXT4.

---

### Post by lukeiamyourfather on 2012-01-03
> **Lars Noodén said:**
> Ubuntu can read NTFS, but be warned that it is a garbage file system and you will not get the performance that you would with a decent file system.  Further, you will have to periodically manually defrag those partitions to eek out a little better performance.  If possible, update them to EXT3 or EXT4.

Agreed. It would be worth your time to use a filesystem native to Linux. Using non-Linux filesystems should be for temporary situations only in my opinion.

---

### Post by Vipercatt on 2012-01-03
> **lukeiamyourfather said:**
> Agreed. It would be worth your time to use a filesystem native to Linux. Using non-Linux filesystems should be for temporary situations only in my opinion.

Ok in that case can I format a drive in linux then copy the media files across from the ntfs system or do i have to re-encode 9 tb of movies ?

---

### Post by Lars Noodén on 2012-01-03
The data is ok, it's just the underlying file system in which they reside which is the problem.  Copying works fine, so would tar or rsync.

---

### Post by lukeiamyourfather on 2012-01-03
> **Lars Noodén said:**
> The data is ok, it's just the underlying file system in which they reside which is the problem.  Copying works fine, so would tar or rsync.

If you use rsync it'll keep the modified dates and other metadata. Below is an example command for rsync.

```

rsync -a /mnt/source/directory/ /mnt/destination/

```

---

