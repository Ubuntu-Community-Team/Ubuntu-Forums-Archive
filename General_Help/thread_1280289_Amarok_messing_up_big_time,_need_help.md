---
title: "Amarok messing up big time, need help"
date: 2009-10-01
forum: General Help
---

### Post by Vunutus on 2009-10-01
NOTE: I appear to have fixed this, and other, problem upon updating the newer version of Amarok found in the backports repository. Apparently the version that ships with Jaunty is a seriously bugged out piece of software

Amarok is easily the best media player I've ever used but all of the sudden it's messing up on me pretty badly in several different ways, primarily with my music library. I first noticed the oddity this morning when I tried to put some new music on my MP3 player. Amarok was refusing to see it. I've used it with Amarok before so I know that isn't the problem.

This evening when I get home I discover it has a nifty media file organizing tool that I desperately need. I run it once to organize my files into alphabetical folders. It runs a while then bam, all my music is tagged and sorted into appropriate folders. I thought that was cool, so I check out what other options it has. I find the option to have it rename all music files, so I set it to rename to "Artist - Title.whatever" and let it loose. It runs a while again, but crashes towards the end. I re-start Amarok and things appear to be fine. All my library is renamed, but with one strange quirk, everything was classified as the "Various Artists" artist instead of their correct artists. I figure that was related to the crash, so I run the media sorter one last time. This time, it fixes some of the files and puts them in the correct folders, but still some other random artists are stuck off in Various Artists. I think "alright, it's just a matter of file organization and I can still play my music so who cares what folders they are in?", but then realize that no, Amarok can no longer correctly play music.

It only shows a number of random artists in the local collection. There is no reasoning to what artists it lists. Sometimes the artists can be expanded to show the correct albums, sometime they are empty, and other times still it shows albums from the wrong artist (no, amarok, Iron Maiden doesn't have a Mozart album). It also re-scans every once in a while and changes what artists it decides to see.

I've tried everything I could think of to reset this. I made a backup of my music folder before I started letting it loose on my files, so I tried deleting what it had organized and restoring the backup, but that doesn't help. I also tried doing apt-get purge amarok, apt-get autoremove, and apt-get autoclean to completely get rid of amarok then re-installing it, but that doesn't change anything.

I'm currently without any music. Can someone please help me fix this stupid thing?

---

