---
title: "Help setting up Grsync"
date: 2012-04-03
forum: General Help
---

### Post by SuperFreak on 2012-04-03
I have been able to backup my music library with grsync but subsequent backups are taking a long time (music files about 0.5 TB 6hrs+ with only a few changes to directory since I last backed it up- maybe 1 gb of changes). I want to be able to backup any files that have changed (ie new or different tags) as well as add new music but I don't want to recopy the entire directory which I suspect it is doing

settings I am using are (see images)

I am backing up from NTFS to my external HD

---

### Post by papibe on 2012-04-04
Hi SuperFreak.

What filesystem the external HD has? If it's an ext3/4 fs, you may need to adjust the --modify-window option.

Could you show us the actual rsync command you are generating?

Regards.

---

### Post by SuperFreak on 2012-04-04
I believe all my external Hard Drives are NTFS. Here is the Command used :

*** Launching RSYNC command:
rsync -r -t -v --progress --size-only --modify-window=1 -c -s --exclude CELTIC/ --exclude CLASSICAL/ --exclude COMEDY/ --exclude COUNTRY-BLUEGRASS/ --exclude CUE Files/ --exclude JAZZ/ --exclude Playlists/ --exclude R & B/ --exclude RELIGIOUS/ --exclude Renee/ --exclude SOUNDTRACKS/ --exclude SPECIAL/ --exclude REGGAE/ /media/Music/Flac /media/FLAC Rock

sending incremental file list

---

### Post by papibe on 2012-04-04
Interesting. I've never done recurrent NTFS to NTFS rsyncing, so I just have educated guesses for you:

The option --modify-window is used to relax the time comparing process, it is very helpful for syncing when ext3/4 and NTFS are mixed (because a known [problem]("ftp://ppp.samba.org/pub/unpacked/rsyncweb/daylight-savings.html") of DST and UTC).

I would test either increasing the value, or removing the option.

Another useful option would be the --update (or -u) that avoid transferring files that are newer on the destination.

Just some ideas. Tell us how it goes.
Regards.

---

### Post by SuperFreak on 2012-04-05
Thanks

I will try your suggestions
It may be simply that USB 2.0 is too slow. I am about to build a PC with USB 3.0

edit: I changed the 2 settings you mentioned and I will see next back up how it goes(a month from now)

---

