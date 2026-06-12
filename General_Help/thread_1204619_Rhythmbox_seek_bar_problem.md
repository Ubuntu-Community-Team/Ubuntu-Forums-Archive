---
title: "Rhythmbox seek bar problem"
date: 2009-07-05
forum: General Help
---

### Post by m00se3724 on 2009-07-05
The seek bar in rhythmbox only moves for certain (and very few) songs, and it's not only for certain file types, it seems completely random. Anybody else run into this problem?

---

### Post by jf1 on 2009-07-10
I had the same problem and  found out more about this problem, and also a solution.
it seems it has something to do with the library folder and the "watch library for new files" setting.


 After I installed my new Jaunty I had rhythmbox open and let it watch ~/Music for new files  then I copied all files from my backup in ~/Music, it recognized all, but the time for all MP3s was unkown - also the seekbar unmoveable for these songs.

This applied for every new MP3 file in ~/Music, also when removing some mp3 files from the folder and the library and moving it back.
 but i noticed that when I imported Mp3s manually, i.e. with drag and drop from desktop,
the playtime was detected correctly.
 now I created a new Folder ~/Music2  set rhythmbox library to this path and also the watch option.
then removed all files from the library (right-click -> remove) and moved the actual files to ~/Music2 - and BINGO. now the playtime of the files is detected correctly ..
 

weird bug.


Hope this helps you too.

---

### Post by tylerious on 2010-06-29
I hate to bring up an old thread, but the problem still exists in Lucid as of June 2010, and I have an easier solution.

The problem, as jf1 correctly states, is when Rhythmbox watches a folder for music, but is unable to play the files because the correct codecs are not yet installed. 

Instead of having to actually move the physical files, here's all you need to do:

1) In Rhythmbox's preferences, unselect "Watch my library for new files."
2) "Remove" all your music from Rhythmbox.
3) Install the appropriate codecs (gstreamer-plugins-bad and/or gstreamer-plugins-ugly).
4) In Rhythmbox's preferences, select "Watch my library for new files."

With the correct codecs installed now, Rhythmbox should detect the playtime correctly and add back all your music.

---

### Post by rodrigor on 2011-02-28
The fix worked for me on ubuntu natty 11.04 (beta).
The seek bar was ok, then i installed the restricted codecs and it stopped working. I did that you suggested and it's working again.

Thanks!

---

