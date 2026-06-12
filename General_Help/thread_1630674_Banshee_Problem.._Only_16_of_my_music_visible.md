---
title: "Banshee Problem.. Only 1/6 of my music visible??"
date: 2010-11-25
forum: General Help
---

### Post by Matt Brooks on 2010-11-25
I just installed Banshee v1.80 on Ubuntu 10.10 and was looking to import my music from my external HD. I pluged the HD in and copied all of the music in it to my music folder, (**ALL 2,604 SONGS**).

I then went into banshee and set the folder for my music library to be /home/matt/Music, where i put **THE 2,604 SONGS**.

Banshee started to scan the songs, all the way up through **THE 2,604th**. After it was finished i navigated to all music in the banshee side pane and there was **only 394**. 

After some research i found that this was because only 394 of the songs actually had .mp3 or a similar extension at the end of the file name.

I've spent the past hour trying to figure out how to either append the appropriate extension to all the files, or how to get banshee to see the files without any extension, to no avail.

Thats why I'm posting here - Any ideas? Thank you.

---

### Post by tuppe666 on 2010-12-03
Wow. I am at a loss as to why you don't have the right extensions to your files. You could do some fancy bash thing, but I suspect a tag editor will probably be your best bet at this point. I tried Mp3 Diags which did not recognise files without extensions, I had a try with Puddletag which did recognise the files although did not correct the extension. Maybe Easttag!?

---

### Post by concentricpuddle on 2010-12-04
There is one way of getting your extensions back using puddletag, but it's a slight bit of work.

In Edit->Preferences->Columns add __filetype to a column (I think it's there by default, but I'm tired and can't be bothered to check). In Tag Panel Preferences add __ext. 

Now you can sort your files by filetype. Select all files of the same type then add the extension using the Tag Panel. Should take no longer than a few minutes. ;-)

---

