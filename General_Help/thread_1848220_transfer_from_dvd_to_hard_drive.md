---
title: "transfer from dvd to hard drive"
date: 2011-09-22
forum: General Help
---

### Post by brotell on 2011-09-22
Hi all a question for you all I would like to transfer some movies from my dvd's to an external hard drive I dont want to shrink them in most cases this has already been done. Tried to straight copy them but it still wants to try and shrink them.

Any help or suggestions would be gratefully accepted


Terry

---

### Post by ajgreeny on 2011-09-22
If you use brasero for copying the disk, you will get the option to save the image of the original DVD as an .iso file (or maybe .img, I can't remember)  which will be an exact copy of the original and will play on VLC, or I presume, most other media players.  The image file will be available to burn to DVD, if you wish, but there is no need to do so.

I am not sure how the encryption of the disk or the later need for libdvdcss2 affects this, but I think it works OK, so give it a try.

---

### Post by Olivia Wagner on 2011-09-22
This is a good thing which I came to know. I was also doing it through the shrinking process. Sometimes I used to copy the content of DVD to the computer and then copy it back to the hard disk. But it used to take a lot of time. Now it could be faster.

---

### Post by coldraven on 2011-09-22
Check that your external drive is not formatted to FAT32.
If it is FAT32 you cannot save any file over 4GB, you would need to re-format it to NTFS or  EXT2 for example.

---

### Post by searchfgold6789 on 2011-09-22
+1 for ripping from Brasero.
Please make sure that this is legal, I'm begging you.
You will need libdvdcss in order to play the DVD's:
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list
sudo apt-get --quiet update 
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring
sudo apt-get --quiet update
sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu libdvdcss
```

---

### Post by perspectoff on 2011-09-22
Ok, so your company gave you an old A/V training DVD that you want to archive on your computer, (since I know you aren't trying to copy commercial movies illegally, right?)

You may only want to do this one time, or you may have many occasions to do this. If the latter, you will quickly tire of saving DVDs that are in their original format (.vobs) and will want something of equal quality but of much smaller size.

That's when you will want to start converting all your videos to H.264 / X264 format for video, and .mp3 or AC3 (or AAC) for audio. You would then save them in a Mastroska open source container. The best program to do this is Handbrake. (I personally don't use AAC because that is a proprietary Apple format and I don't have a single DVD player that accepts it. I tend to retain the AC3 audio format, or sometimes convert to mp3 with libmp3lame.)

Handbrake. Find it, install it, use it. 

I happen to have a very old DVD player that will not accept Mastroska, so I end up converting (using mencoder or ffmpeg) to an .AVI container with XVID video (XVID/DivX is nowhere near the quality of H.264/X264 but was the standard for a very long time and is even accepted by my very old DVD players). In reality, I'm just lazy, though, since a new DVD player which can play Mastroska with H.264/X264 is probably only $40 at Walmart these days.

You can get a very, very high quality 2 hour video into a 700 Mb to 1.4 Gb file this way, and therefore store several such video files on a single standard DVD (for archival purposes).

We store all our company's videos this way, now, and have gone completely away from the old .vob formats that is/was in use for "standard" commercial DVDs. I certainly don't bother with .ISOs, which is what we did maybe 10 or 15 years ago.

Of course, we don't use CSS encryption, so we don't need the libdvdcss2 package from Medibuntu  (as one would need even to watch commercial DVDs on the computer). You'll definitely want libdvdcss2 installed, though, as mentioned.

While we put a lot of training videos on DVD (for new employees), we actually store them all on one hard drive, as you are suggesting to do. The hard drive can be set up as a WebDAV server with Apache2 so that the videos can then be accessed by employees (who have a password) online through the Internet, as well, obviating the need for DVDs entirely. WebDAV is pretty universal, these days, so any OS and (most) browsers allow WebDAV connections. (VLC as a multimedia player is also available for all OS, as well.)

---

