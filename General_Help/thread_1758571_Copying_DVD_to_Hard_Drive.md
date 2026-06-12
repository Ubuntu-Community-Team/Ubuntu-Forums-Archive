---
title: "Copying DVD to Hard Drive"
date: 2011-05-14
forum: General Help
---

### Post by aoniumo on 2011-05-14
I would like to copy/back-up dvds to my hard drive.  I do not want an ISO image.  I want want AnyDVD does in Windows.  With AnyDVD, I could copy/rip the DVD onto my hard drive. The format would be that it's inside a folder with the DVD title and within that folder are the Video TS and Audio TS folders.  The DVDs I have on my hard drive that were ripped with AnyDVD play perfectly in mplayer.  I just have to open the folder location in mplayer and they would play with all the menu options available just like a regular DVD.

I tried Acid Ripper.  Since it failed several times before ending, I deleted the program.

I tried k9copy.  How do you play the iso it creates?  VLC doesn't work!  Extract the iso and I cannot play the files in the Video TS folder once extracted.  I ripped 30Rock and the folder without creating an ISO and it only had less than 1GB in it even though it said it copied successfully! I also cannot play the contents.  So, K9copy is deleted.

I tried Acid Ripper.  Also didn't work.  Acid Ripper is deleted as a program.

Any help would be appreciated.

---

### Post by flipper T on 2011-05-14
k9copy rips to videots / .vob

its in Ubuntu software centre

use the assistant

---

### Post by TeoBigusGeekus on 2011-05-14
1)Create a folder with the movie's name.
2)Select AUDIO_TS and VIDEO_TS folders from the dvd.
3)Right click them>Copy.
4)Paste them into the folder.
5)?????
6)Profit.

---

### Post by aoniumo on 2011-05-14
> **TeoBigusGeekus said:**
> 1)Create a folder with the movie's name.
2)Select AUDIO_TS and VIDEO_TS folders from the dvd.
3)Right click them>Copy.
4)Paste them into the folder.
5)?????
6)Profit.


I tried that but half way through it, I get a read error.

---

### Post by TeoBigusGeekus on 2011-05-14
Try with a different dvd.
It won't make a difference if you use a different app/way to do it.
If the dvd and/or the driver are faulty, you won't be able to copy it to your hd.

---

### Post by Ichido on 2011-05-15
I use Brasero to Copy DVDs.
I Burn them to DVD+R and it works great!

---

### Post by andrew.46 on 2011-05-16
To copy the DVD structure to your hard drive you could install vobcopy, libdvdread and libdvdcss and simply run:

```
vobcopy --mirror
```

Andrew

---

### Post by doublewitt on 2011-07-31
> **andrew.46 said:**
> To copy the DVD structure to your hard drive you could install vobcopy, libdvdread and libdvdcss and simply run:

```
vobcopy --mirror
```

Andrew

OK - I did this and now there is no sound...
no sound plays for youtube, dvd's etc...

what can I do to fix this?
thanks for any tips...

---

