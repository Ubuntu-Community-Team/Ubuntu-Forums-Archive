---
title: "Help with rsync"
date: 2010-10-02
forum: General Help
---

### Post by elosier on 2010-10-02
I've been using rsync since December of last year thinking it was correctly backuping my files to an external hard drive.

Recently, one of my hard drive on my raid 0 array completely crashed and I had to send for a replacement.  So I took my external hard drive with the backups and started copying the files on another computer...only to realize that there's not been any backups for the past 7+ months.

Now, I realize that those files are lost forever, but I'd would really like to know where I screwed up so that I don't make the same mistakes again when I reinstall everything.

Here's the rsync command I was using : 
```
rsync -auv --delete --log-file=/home/tzeentch/Desktop/$(date +%Y%m%d)_rsync.log /home /media/Iomega\ HDD/home/
```

The result of the command was also sent to my email address so that I could see what was being backed up.

Here's a sample output from the last mail I received before the hard disk crash : 
```
...
home/photos/30D/2010/2010_09_05/IMG_4258.JPG
home/photos/30D/2010/2010_09_05/IMG_4260.JPG
home/photos/30D/2010/2010_09_05/IMG_4263.JPG
home/photos/30D/2010/2010_09_05/IMG_4266.JPG
home/photos/30D/2010/2010_09_05/IMG_4267.JPG
home/photos/30D/2010/2010_09_05/IMG_4268.JPG
home/photos/30D/2010/2010_09_05/IMG_4282.JPG
home/photos/30D/2010/2010_09_05/IMG_4283.JPG
home/photos/30D/2010/2010_09_05/IMG_4288.JPG
home/photos/30D/2010/2010_09_05/IMG_4289.JPG
home/photos/30D/2010/2010_09_05/IMG_4300.JPG
...
```

And yet, on the external hard drive, the last dated directory is 2010_02_06.

Anybody has any idea where I went wrong?  And most important, how can I prevent this from happening in the future?  Any better solutions than rsync?

---

### Post by elosier on 2010-10-03
Also, in case other people had bad experience with those : the external hard drive is a Iomega eGo 1TB.

---

### Post by ragtag on 2010-10-03
When accessing files on a remote machine, rsync opens a shell to that machine which means that any spaces you have in your path need to be escaped twice, or the whole path put in quotation marks.

I'm not sure if that's the problem here, since you're only copying files locally, but it might be a good idea to just avoid having spaces in your paths at all. Other than that, I can't see anything wrong with the command.

You might want to compare the file size and number of files once done, and mail that to yourself as well, so you can catch any errors you're not seeing in the logs.

---

### Post by elosier on 2010-10-04
Ah, that's a good idea, comparing the files sizes. I'll try that.  Although I'm thinking about checking for foolproof backup techniques.

---

