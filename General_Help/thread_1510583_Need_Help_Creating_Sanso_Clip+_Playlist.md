---
title: "Need Help Creating Sanso Clip+ Playlist"
date: 2010-06-15
forum: General Help
---

### Post by Manaan on 2010-06-15
I just bought a Sansa Clip+ mp3 player, and have uploaded all my music to it. Here's the problem: I have created a massive xspf playlist with all my favorite songs and it doesn't show up. After some research I discovered that it takes m3u playlists. I created one with VLC and uploaded it instead, but still nothing. I openned the m3u playlist up with gedit and replaced the /home/user/Music/ with /media/SANSA/MUSIC/ but when I open it with my media player it is recognized but it acts as if it were an empty playlist with nothing in it. So, I tried changing it from /media/SANSA/MUSIC/ to just /MUSIC/ since it's technically the root of the mp3 player. That gave me the same problem. I was thinking of moving all the music in my playlist into the same directory and then editing all their ID3 tags so that they all play at once, but I can't figure out how to do that, either.

Short version: I'm trying to create an m3u playlist on an mp3 player that organizes everything through ID3 tags and when I try the playlist is always shown as blank.

EDIT: I just found out that I can actually sort them by folder and in fact play all of the music in a specific folder. So the problem now becomes getting all that music into one folder.

ANOTHER EDIT: I guess I could have figured this out by myself... after some creative greping and piping I was able to convert an m3u to a direct list of the files I want. Now all I have to do is figure out how to cp them all into one dir.

FINAL EDIT: I got it working, finally, I saved the playlist as m3u, and then issued "cat playlist.m3u | grep file://" then replaced file:// with nothing and then replaced all the ascii codes with the correct characters finally issuing "xargs cp -t /target/dir < file/list.txt".

---

