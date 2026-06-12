---
title: "Unmounting /media"
date: 2010-07-26
forum: General Help
---

### Post by Joseph Schwenker on 2010-07-26
I have been struggling to find a way to play a game under Wine without using the CD, so looked if it was possible in Wine.  I came across this commmand:

```
sudo mount /home/joseph/BIONICLE.iso -o loop /media/cdrom0/
```

which I tried.  It didn't work, and gave me an error about how there was no "cdrom0".  I assumed that it was created whenever something is mounted.  Out of desperation, I removed cdrom0 from the command, and then things got funky.  Doing so replaced all the contents of /media (there were no files, only useless floppy folders, since I have no floppy drive) with the contents of the ISO file.  I tried using sudo to delete the files, but it said that it was a read-only filesystem.  I tried changing the permissions using sudo chmod +w /media, but it didn't work, and complained about being read-only.  I am unable to mount anything now!  Can someone help, both with deleting /media, and possibly with running Wine games without the CD?

---

### Post by Joseph Schwenker on 2010-07-26
I solved the problem by running 

```
sudo umount /media
```

---

