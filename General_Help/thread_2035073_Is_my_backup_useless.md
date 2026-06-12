---
title: "Is my backup useless?"
date: 2012-07-29
forum: General Help
---

### Post by jonnyboysmithy on 2012-07-29
I made a backup using:
```
sudo dd bs=15M if=/dev/sda5 conv=sync,noerror | gzip -9 > /home/myusername/.System-Root-Partition-Image.img.gz

```

And now I need my backup and I can't figure out how to restore it.
I figured I would need to do the reverse of what I did before. So from a liveusb I tried:
```
sudo dd if=/media/e7e88e65-92e8-481e-bdf6-a52d1367dfa6/myusername/.System-Root-Partition-Image.img.gz of=/dev/sda5
```
It didn't work.
(the image is on in my home folder. I have my homefolder backed externally) 

What do I do now?
Please help ;)

---

### Post by spjackson on 2012-07-29
You compressed the backup with gzip. You need to decompress it with gzip -d .

---

### Post by Kirk Schnable on 2012-07-29
> **spjackson said:**
> You compressed the backup with gzip. You need to decompress it with gzip -d .

I second that!  Should work great after you decompress the backup.

Kirk

---

### Post by AginoZinuepup on 2012-07-29
> I made a backup using:   Code:  sudo dd bs=15M if=/dev/sda5 conv=sync,noerror | gzip -9 > /home/myusername/.System-Root-Partition-Image.img.gz And now I need my backup and I can't figure out how to restore it. I figured I would need to do the reverse of what I did before. So from a liveusb I tried:   Code:  sudo dd if=/media/e7e88e65-92e8-481e-bdf6-a52d1367dfa6/myusername/.System-Root-Partition-Image.img.gz of=/dev/sda5 It didn't work. (the image is on in my home folder. I have my homefolder backed externally)   What do I do now? Please help  couldnt have said it better myself

---

### Post by jonnyboysmithy on 2012-07-29
The graphical utility gives an error "An error occurred while extracting files"
EDIT: I had tried the graphical utility earlier, and because it came back with an error I thought the file was corrupt.
I tried it the command line way: ubuntu@ubuntu:~$ sudo gzip -d /media/e7e88e65-92e8-481e-bdf6-a52d1367dfa6/myusername/.System-Root-Partition-Image.img.gz 
No errors, seems like it worked!:popcorn:
Now I'll run ```
sudo dd if=/media/e7e88e65-92e8-481e-bdf6-a52d1367dfa6/myusername/.System-Root-Partition-Image.img of=/dev/sda5
```I'll see how it goes.. seems to be working so far :P..... we'll see...

---

### Post by idoitprone on 2012-07-29
> **jonnyboysmithy said:**
> I made a backup using:
```
sudo dd bs=15M if=/dev/sda5 conv=sync,noerror | gzip -9 > /home/myusername/.System-Root-Partition-Image.img.gz

```And now I need my backup and I can't figure out how to restore it.
I figured I would need to do the reverse of what I did before. So from a liveusb I tried:
```
sudo dd if=/media/e7e88e65-92e8-481e-bdf6-a52d1367dfa6/myusername/.System-Root-Partition-Image.img.gz of=/dev/sda5
```It didn't work.
(the image is on in my home folder. I have my homefolder backed externally) 

What do I do now?
Please help ;)

I dont think you should use dd to back up your disk. DD command will copy unused bytes which in return increase your back file. I think clonzilla is a better option

---

### Post by jonnyboysmithy on 2012-07-30
I used rsync to pre-task execute a script that makes an system image in my /home and then clone my home folder to my external. So it was plug  in and click start. Really easy.
Maybe I can use rsync instead of dd? 
It seems you have to boot of a live system to use clonezilla  ....I don't like having to reboot :biggrin:.

I was quiet happy with the ddrescue. The backup file is only 5GB (the script I use zeros the empty space). I had trouble with extracting it earlier(I think it was because I ran out of disk space :-\"). It extracts to 21GB. 

SOLVED
Its all working as is should now:popcorn: Bring out that popcorn!!

---

