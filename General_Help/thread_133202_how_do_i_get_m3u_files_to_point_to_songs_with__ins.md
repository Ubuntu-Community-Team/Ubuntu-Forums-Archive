---
title: "how do i get m3u files to point to songs with / instead of \?"
date: 2006-02-19
forum: General Help
---

### Post by aeiah on 2006-02-19
is there any way to get beep music player (or linux in general) to change the path within m3u files from \ to / ? ill elaborate..

i have 33GB of music on my 300GB sata drive in an NTFS partition (where windows resides). the mp3 files are in directories like: music/audio/album/song.mp3 and the playlists are: music/playlist.m3u

these playlists were generated in windows, some many years ago, and all of them use the format audio\album\song.mp3, which is no good in a none-windows environment :( 

i know totem manages to figure out the problem for its self and i have no troubles playing my m3u files within totem, but i find it awkward and cumbersome for audio and ideally, would like to use beep. what can i say, ive used winamp since windows 95

---

### Post by engla on 2006-02-19
I don't know anything about m3u files, but this is a small try at a solution.

These files are text files basically, right? Try making a copy of a playlist file, and opening that copy with gedit. In gedit, type ctrl+R and enter Find "\" and replace with "/"; run this replace on the whole file and save and try again.

It should work..

---

### Post by aeiah on 2006-02-19
[QUOTE=engla]I don't know anything about m3u files, but this is a small try at a solution.

These files are text files basically, right? Try making a copy of a playlist file, and opening that copy with gedit. In gedit, type ctrl+R and enter Find "\" and replace with "/"; run this replace on the whole file and save and try again.

It should work..[/QUOTE]


thanks for the solution but i dont think it'll be really practical im afriad.

1: these are on my NTFS partition so there's no write access
2: the .m3u files have relative paths. to change \ to / within the .m3u's i would need to copy these playlists to my FAT or /home partition, and thus need to add absolute paths as well as changing the \ to /
3: there's 33GB of music and a playlist for every album. thats quite a few playlists, so batch conversion would be necessary

---

### Post by piedamaro on 2006-03-01
do not use absolute paths. In this way if you move your mp3 folders playlists still work.

---

### Post by jrrhodes on 2006-03-01
you can just make a copy of the play list one for windows one for linux, that way you can have both lists one with \ and one with / and like the other person said just use your favorite text editor to change the \ to /

---

