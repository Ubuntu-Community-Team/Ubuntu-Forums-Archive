---
title: "Trying to make iso of DVD"
date: 2009-10-12
forum: General Help
---

### Post by infinitelink on 2009-10-12
: ( 

Nothing works.

Dd if=[directory] of=[directory]/[filename] doesn't work, but gives, 
> 
dd: reading `/dev/cdrom': Input/output error
2016+0 records in
2016+0 records out
1032192 bytes (1.0 MB) copied, 3.64745 s, 283 kB/s


it does, however, produce a file, but attempting just to use VLC to play that output file (just to try) gives, 

> VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.

And no other player (not mplayer or any other, none, period) works, either.

I cannot copy the DVD's directory contents, either. : (

What's going on, anyone? I can play the DVD fine itself (i.e. the decryption stuff is all installed), so...?

---

### Post by lukjad on 2009-10-12
I don't know for sure, but I don't think you can use VLC on an ISO file until you mount the ISO file. Double Click the file first, and browse the ISO. Are there any files there?

---

### Post by raygj on 2009-10-13
VLC does indeed open & play DVD.iso's.just rightclick on your "dvd.iso" file and select open with VLC.
Also to copy you "dvd disc" to "dvd.iso" just install "Brasero" and use it to copy dvd to your folder as a "brasero.iso" file.
Another option is ,instead of installing brasero, to open/browse your DVD disc with Nautalus.then select all files(on dvd disc) and copy to a folder (eg for example into a folder named "/home/username/movie").
then  if you open nautilus and go to "/home/username" and rightclick on "movie"folder icon and select open with VLC then VLC will open and play the folder "movie" as if it was a DVD disc in your DVD drive.

---

