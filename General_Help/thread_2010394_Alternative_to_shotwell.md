---
title: "Alternative to shotwell"
date: 2012-06-25
forum: General Help
---

### Post by Mazate on 2012-06-25
Hi there... does anyone know of another good application that I can use to manage my photos other than shotwell?  It seems to freeze my computer so I need to find something else.

---

### Post by philinux on 2012-06-25
> **Mazate said:**
> Hi there... does anyone know of another good application that I can use to manage my photos other than shotwell?  It seems to freeze my computer so I need to find something else.

I just use the file browser to create folders by event and date. I then use gthumb and gimp for any editing. If any image software wants to import anything then its not for me. By that I mean I have no use for albums etc. I do my own organising.

---

### Post by davidvandoren on 2012-06-25
you can use
Digikam  or
F-spot 
Or 
Gwenview but it needs some dependencies from the KDE desktop. 

It's in the repository

---

### Post by |{urse on 2012-06-25
There's always picasa :/ F-spot also.

---

### Post by ajgreeny on 2012-06-25
> **philinux said:**
> I just use the file browser to create folders by event and date. I then use gthumb and gimp for any editing. If any image software wants to import anything then its not for me. By that I mean I have no use for albums etc. I do my own organising.
I totally agree! And it takes only a small amount of resources.

Previous versions of gthumb were pretty limited, but more recently it has become an extremely good application provided that you manage your photo folders manually before trying to use gthumb.

Its photo editing is also much better than it used to be; not as all embracing as gimp, but nevertheless quite enough for most simple photo edits, eg brightness/contrast, colour enhancement, etc etc.

---

### Post by David Andersson on 2012-06-25
I think **F-spot** is quite good at managing tags. It is easy to organize tags, to add tags to images, and to search images for individual tags or combinations of tags. The tags themselves can be organized hierarcially. You can also add a text comment to each image.

F-Spot (like other photo organizers) saves info about images, including tags, in its own database, stored in hidden files in your home directory. F-spot can export images and it seems more capable than Shotwell in that regard.

If you go to F-spot's settings and tell it to save tags inside images (in exif- and jpeg-headers in the jpeg files) then you can export images just by copying them from F-spot's photo directory. (You can let it only save tags in its database, if you, for example, want to offload incremental backups.)

You can configure F-spot to use your normal ~/Photo directory or you can let it use, for example, a hidden directory, like ~/.my-fpsot-album.

There are some cons also. I have not found an easy way to search for *file names*. It requires *mono*. If you would like to manage scanned photos too (that does not have exif-data with correct time and date in them, as camera photos have) I have not find an easy way to set time and date on those photos.

I have briefly tried **Shotwell** and **gThumb**. I find those lack flexibility in tag management. Shotwell's export didn't copy out the images but exported scaled and re-encoded jpegs.

(Disclaimer: I have not tested the lasted versions of these programs. They may be better or worse.)

---

### Post by eric-yorba on 2012-06-26
> **Mazate said:**
> Hi there... does anyone know of another good application that I can use to manage my photos other than shotwell?  It seems to freeze my computer so I need to find something else.
Sounds like a bug, we can look into it and see if we can find a solution.  What version of Shotwell are you running?  What were you doing when it froze?

---

### Post by eric-yorba on 2012-06-26
Also, when you say your computer froze, do you mean Shotwell or the entire OS?

---

### Post by Mazate on 2012-06-26
> **eric-yorba said:**
> Sounds like a bug, we can look into it and see if we can find a solution.  What version of Shotwell are you running?  What were you doing when it froze?


Importing pictures.

---

### Post by davidvandoren on 2012-06-26
Did you import the pictures to your hard drive or were they already there?
If they were already there, did you choose to copy them to your pictures directory or just map the pictures into the application?

---

### Post by Mazate on 2012-06-26
> **davidvandoren said:**
> Did you import the pictures to your hard drive or were they already there?
If they were already there, did you choose to copy them to your pictures directory or just map the pictures into the application?


They were already there, and I chose to map the pictures.

---

### Post by davidvandoren on 2012-06-26
> **Mazate said:**
> They were already there, and I chose to map the pictures.

I had the same problem where shotwell froze or crashed whenever importing large directories or managing huge directories full of pictures.

I now have a 2TB external HD and it's a slow one which was cheaper because of that. 
It imported/mapped the whole picture collection without any problem from the external drive.
I wish someone could figure this out because I think it's a bug.

---

### Post by eric-yorba on 2012-06-26
> **Mazate said:**
> They were already there, and I chose to map the pictures.
Interesting... what version of Shotwell is this?  You can check in help->about.

---

### Post by otto67 on 2013-05-20
I can confirm this bug since couple of years. Shotwell always freezes while importing large image folders. And it makes it unusable for me

---

### Post by dave0109 on 2013-05-20
What do you mean by large?  After returning from a recent trip, I imported nearly 2000 photos without any problems.  This was on version 0.13.1, though I have just recently gone to 0.14.1 by adding their PPA.

---

### Post by Linuxisfast on 2013-05-21
Shotwell works beautifully as does digikam, I have latest from the PPA. The freezing issue looks to be like gvfs related.

---

### Post by nutsyben on 2014-01-06
Disagree with this last statement, for many years shotwell freezes during import and randomly for large pictures (> 8-10mb). I did not experience such problems on other softwares but must admit that shotwell remains handy.

---

