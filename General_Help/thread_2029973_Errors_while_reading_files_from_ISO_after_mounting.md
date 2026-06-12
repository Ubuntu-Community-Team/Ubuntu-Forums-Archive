---
title: "Errors while reading files from ISO after mounting it with archive mounter"
date: 2012-07-20
forum: General Help
---

### Post by April Lavender on 2012-07-20
OK, I searched about it on the forum but can't seem to find anyone talking about this exact problem. Maybe someone did and I missed it (in which case, I'm sorry).

I have some ISO images that I want to mount using double click. There's an application for that on Ubuntu 12.04 called "archive mounter". I don't know if it is for this specific purpose but it does mount ISOs. The problem is, when I open ISO files using "archive mounter", all the files show on the left pane in nautilus but when I open video files from there using VLC or UMplayer, they give read errors. 
The exact error from VLC is this:

File reading failed:
VLC could not read the file (Operation not supported).

Is this a bug in archive mounter or am I doing something wrong here?

---

### Post by dino99 on 2012-07-20
iso is a compressed install format, not a video one  :confused:

---

### Post by sudodus on 2012-07-20
- What kind of files is it? What extension?

- Can you extract a file to the desktop using drag and drop?

- What happens when you try to run it with a video player after extraction?

---

### Post by April Lavender on 2012-07-20
The ISO file is, obviously, in .iso format. The file that I'm trying to open from the ISO image is .avi file. I can copy it to desktop and then open it and it opens fine this way. The problem occurs only when I'm trying to open it directly from where it gets mounted by opening ISO image using "archive mounter".

Thanks for the replies.

---

### Post by sudodus on 2012-07-20
> **April Lavender said:**
> The ISO file is, obviously, in .iso format. The file that I'm trying to open from the ISO image is .avi file. I can copy it to desktop and then open it and it opens fine this way. The problem occurs only when I'm trying to open it directly from where it gets mounted by opening ISO image using "archive mounter".

Thanks for the replies.
Well, the archive program is probably ***file-roller***, and I don't think it mounts the iso file, it only opens it (and reads the content). That is why you need to extract the file to run it in a video player.

You can also mount the iso-file as a loop device for example like this 
```
sudo mount -o loop file.iso /mnt
```
and then you might succeed to run the avi file without extracting it:

```
cd /mnt
```
```
ls
```
lists videofile.avi
```
vlc videofile.avi
```

*Edit:* Or simply browse to /mnt with your file browser and double-click ...

---

### Post by April Lavender on 2012-07-20
I know about the command line method. I just wanted to mount the ISO just by double clicking. And it does work except when I want to play multimedia files directly
. 
I'm not using file-roller. It is "Archive Mounter", that is, a program that actually mounts archives without extracting anything. 

And everything works fine except for when I try to open a video or audio file.

---

### Post by sudodus on 2012-07-20
OK, just to be sure, please click on ***Help -- About*** to find out which program it is.

Anyway, I know that many files can be opened directly by double-clicking, but there might be some logic to stop running video and at the same time decoding it (because it might be too slow to play well). Remember that the archiver (e.g. file-roller) is also used for zipped files.

---

### Post by April Lavender on 2012-07-20
I can't seem to take snap of my screen while right clicking. Otherwise I would show you. Its "archive mounter". Not "archiver" or "archive manager". The program doesn't seem to appear in dash or any other place. I can only see it in open-with context menu or in the open-with dialogue box. 
As it doesn't seem to have any GUI window, I can't check the Help->about thing.

---

### Post by sudodus on 2012-07-20
You are right, it is not 'file-roller', but some other tool, that I have not used. But if it were really mounting the iso file, then you should be able to manage the files just like in any file system on a HDD, CD, flash drive and run it with a video program.

Maybe someone else reading this thread can explain that tool and what it can do.

---

### Post by sudodus on 2012-07-20
So I got curious and tried it in Ubuntu 10.04 LTS (which is still my main working environment, while testing Lubuntu 12.04)

It ***is*** possible to right-click on an iso file in the file browser Nautilus and select mount, which opens a new Nautilus window with the files inside the iso file.

It is 'mounted' like this:

[COLOR="RoyalBlue"]_archive://file%253A%252F%252F%252Fhome%252Fsudodus%252FCD%252Ffile.iso/_[/COLOR]

It is not shown by df, so it is no regular mount, and I ***can*** play video files by double-clicking the file icons ;-)

Are you running 'vanilla' Ubuntu 12.04?

*Edit:* test in Lubuntu 12.04
The 'archive mounter' does not work at all, but the 'archive manager' alias 'file-roller' works, and I can play video without extracting the video clips, just by double-clicking on the file icons :KS

So maybe you can try with the 'archive manager' alias 'file-roller'. If no go, I guess there might be some logic, that finds that it would be too slow :confused:

---

### Post by April Lavender on 2012-07-20
I have a Training DVD with video files ranging from 700MB to 1 GB so File Roller aka Archive Manager does work pretty slow :(

With archive mounter, the files open fine sometimes but either stop if I move around the seek bar or just stop without any reason during the playback.

My OS is Ubuntu 12.04 by the way.

---

### Post by sudodus on 2012-07-20
It seems to be problems because the system cannot manage to decode the iso archive and at the same time run the video.

DVDs are slow compared to hard disks. If you have space enough on your hard disk, the most convenient solution is to extract/copy all the video files to your hard disk to have them ready to play.

Otherwise I guess you have to extract each file and play it (and delete it to preserve disk space).

-o-

Another alternative is to get a lighter desktop environment, which needs less computer power. That way you might be able to decode and play your video files on the fly.

I'm happy with Lubuntu (and the ultra-light desktop environment LXDE).

---

