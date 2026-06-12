---
title: "Ubuntu messed up my external harddrive?"
date: 2006-06-08
forum: General Help
---

### Post by Eric_T on 2006-06-08
Hello

Yesterday I mounted my Maxtor OneTouch harddrive(FAT32 filesystem) in Ubuntu, and everything seemed to work fine. But then I disconnected it, and now instead of folders there are about 1000 files around 22kB in it, with weird "Wingdings" filenames...
What's even weirder is that two of the original folders are still there, and work just as before...?? The result is the same in Windows.
Does anyone know what the problem is? And if there's any way to fix it? There  are about 100GB of music and stuff there that I REALLY don't want to loose!! Any help is greatly appreciated.

---

### Post by ifokkema on 2006-06-08
[QUOTE=Eric_T]Hello

Yesterday I mounted my Maxtor OneTouch harddrive(FAT32 filesystem) in Ubuntu, and everything seemed to work fine. But then I disconnected it, and now instead of folders there are about 1000 files around 22kB in it, with weird "Wingdings" filenames...
What's even weirder is that two of the original folders are still there, and work just as before...?? The result is the same in Windows.
Does anyone know what the problem is? And if there's any way to fix it? There  are about 100GB of music and stuff there that I REALLY don't want to loose!! Any help is greatly appreciated.[/QUOTE]

Hi,

I have been using an external FAT32 drive for some time now... without any problems. Have you ran a file check on that disk?

---

### Post by Eric_T on 2006-06-09
Ok, I ran a fsck, and first got this:
```
/\031<\000\000\032<\000\000.\033<\000
  Bad file name.
1) Drop file
2) Rename file
3) Auto-rename
4) Keep it


```

I didn't quite know what to do, so I choose Keep it. Then I got this:
```
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT


```

I chose 1. Then I got a lot of these messages:

```
/\031<\000\000\032<\000\000.\033<\000
  Bad file name.
1) Drop file
2) Rename file
3) Auto-rename
4) Keep it

```

I'm afraid to break everything, so I don't quite know what to choose... Is it a good idea to run fsck -a, to let Linux try and fix everything for me?

---

### Post by ifokkema on 2006-06-09
[QUOTE=Eric_T]Ok, I ran a fsck, and first got this:
```
/\031<\000\000\032<\000\000.\033<\000
  Bad file name.
1) Drop file
2) Rename file
3) Auto-rename
4) Keep it


```

I didn't quite know what to do, so I choose Keep it. Then I got this:
```
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT


```

I chose 1. Then I got a lot of these messages:

```
/\031<\000\000\032<\000\000.\033<\000
  Bad file name.
1) Drop file
2) Rename file
3) Auto-rename
4) Keep it

```

I'm afraid to break everything, so I don't quite know what to choose... Is it a good idea to run fsck -a, to let Linux try and fix everything for me?[/QUOTE]

I wouldn't go with the -a flag, since I don't know which option Linux will choose. I would say 'Auto-rename' file, so that the errors are fixed, but you don't loose the file. It may take you some time to go through it.

But in the end, this does not 'solve' your problem, i.e. the cause of the corruption. Maybe the drive was not properly unmounted some time?

---

### Post by Eric_T on 2006-06-10
Yeah, I think I just disconnected it without unmounting... it was really stupid of me, but that's what I'm used to do in Windows. And I didn't write anything to the drive when I was using it, either, so I thought it wouldn't matter. Anything I can do about the corruption? As I said, nothing has been written to the drive, I just want back what was already there...

---

### Post by kvonb on 2006-06-10
Can you still access the files you need on the drive?  If so I would recommend copying them to another drive (IF you can find the room!) before doing anything.

Do you have a DVD or CD writer?  If so search the net for "Hirens" and download the ISO image, burn to CD and boot from it.  It has several partition backup utils, get some blank DVDs or CDs and burn the entire thing as a backup before doing ANYTHING!

Just a thought: I'm wondering if those strange files are thumbnails that Linux was creating when it was hot-unplugged.  You might want to try displaying them to find out, then just deleting them once you know that for sure then turning previews off in Nautilus (file manager), goto PLACES -> HOME FOLDER which lainches Nautilus, then on the menu choose EDIT -> PREFERENCES -> PREVIEW and play with the settings.  If this is the problem it might prevent it happening again.


HOWEVER.......back up first!!!!

---

### Post by Eric_T on 2006-06-10
That's the problem, I only have access to two of the original folders... But I'd rather have that than to loose everything.. So yeah, I should take a backup first. I guess I have to buy another external hard drive...there's too much stuff there to bother burning it all on cds/dvds.
But I would very much like to have all the other folders back as well!
Thanks for the help so far, both ifokkema and kvonb.

I had no luck messing with the preview settings, btw...

---

### Post by ifokkema on 2006-06-10
[QUOTE=Eric_T]Yeah, I think I just disconnected it without unmounting... it was really stupid of me, but that's what I'm used to do in Windows.[/QUOTE]
Also in Windows, it's bad to just unplug it. There's a greenish icon in your taskbar (I think it's called Unplug hardware) that you should use to unmount the drive first.

[QUOTE=Eric_T]And I didn't write anything to the drive when I was using it, either, so I thought it wouldn't matter.[/QUOTE]
kvonb's suggestion that these files are thumbnails is possible. You can try and have Linux figure out that files these are by using the 'file' command.
```
file <filename>
```
To see what kind of file this is. And you can try:
```
ls -1 |head -n 10|xargs file
```
to find out the file types of the first 10 files in your current directory. You can change the '10' in the command to a higher number to check more files.

[QUOTE=Eric_T]Anything I can do about the corruption? As I said, nothing has been written to the drive, I just want back what was already there...[/QUOTE]
Not sure what kind of information you had on that drive, but files are rarely just lost. Maybe after running the fsck completely and have it rename all these weird files, you can try and find your original files between these strange files.

---

### Post by kvonb on 2006-06-10
The reason I stress a full PARTITION backup is because you will eventually find the correct way to retrieve the files which unfortunately destroys some in the process.  If you have a full partition backup you can then experiment on the drive and simply restore the original (messed up) files if you need to.  I have lost several drives worth of files over the years and I now perform a full partition backup first, believe me it's worth the extra messing around!  I'm no expert, I can only suggest the steps I would try from experience.  If the files are really valuable to you, I would seriously look at Steve Gibsons "SpinRite", I use it for bad sector revival and recovery quite often and believe me it is worth it's weight in gold!  And I have nothing to do with him or his product, I just know that it works for me.  Best of luck to you.

Regards,

Kev :)

---

### Post by Eric_T on 2006-06-11
Thanks. I'll take kvonb's advice, and buy a new harddrive to backup everything before I try anything else. I need another drive anyways, cause I don't trust this one for backup anymore! Fortunately it wasn't something really, really important on the drive, all the pictures and stuff are backed up somewhere else as well.

Again, thanks for the help! I'll let you know in this thread how things went.

---

