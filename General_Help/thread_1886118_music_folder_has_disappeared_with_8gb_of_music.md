---
title: "music folder has disappeared with 8gb of music"
date: 2011-11-24
forum: General Help
---

### Post by elliotn on 2011-11-24
help needed again, music folder has disappeared with 8gb of music, I checked in home but no music folder, documents is there as well as videos and downloads, help I need the space

---

### Post by sudodus on 2011-11-24
Try to repair your file system! If that does not give you the music back, try ***photorec*** and in the meantime, do not write to your disk. The file data is probably still there, so don't overwrite it!****

---

### Post by elliotn on 2011-11-24
oh yeah to add I didn't delete the folder. the 8gb also disappear

---

### Post by sudodus on 2011-11-24
Is it a partition or a directory within the root partition?

---

### Post by elliotn on 2011-11-24
its the default Music folder in /home/elliotn

---

### Post by Vaphell on 2011-11-24
maybe you drag and dropped your music folder somewhere by accident?
```
find ~ -iname '*mp3'
```
does it return anything?

---

### Post by elliotn on 2011-11-25
> **Vaphell said:**
> maybe you drag and dropped your music folder somewhere by accident?
```
find ~ -iname '*mp3'
```
does it return anything?

the code just showed me few mp3's that I stored in my documents folder in home

---

### Post by sudodus on 2011-11-25
> **elliotn said:**
> oh yeah to add I didn't delete the folder. the 8gb also disappear
Could it be in your waste-paper basket or trashcan? That someone has deleted your music folder by mistake? Then it would have disappeared (from it's original place) but is actually moved to another place found by the file browser and/or the waste-paper basket widget.

I think it might be like this since the disk space has also disappeared.

---

### Post by elliotn on 2011-11-25
> **sudodus said:**
> Could it be in your waste-paper basket or trashcan? That someone has deleted your music folder by mistake? Then it would have disappeared (from it's original place) but is actually moved to another place found by the file browser and/or the waste-paper basket widget.

I think it might be like this since the disk space has also disappeared.

the command on the above reply should have listed the mp3's that are in Music, even if it has been moved. I just can't locate it grrrr

---

### Post by sudodus on 2011-11-25
> **elliotn said:**
> the command on the above reply should have listed the mp3's that are in Music, even if it has been moved. I just can't locate it grrrr
No, not if moved outside of your home folder. But maybe this command would find it
```
sudo find / -iname '*mp3'
```

---

