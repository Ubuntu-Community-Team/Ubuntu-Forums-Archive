---
title: "Problem playing m3u and pls files residing in NTFS"
date: 2006-04-21
forum: General Help
---

### Post by vxj9219 on 2006-04-21
I tried to play a playlist file (**m3u**) on my windows partition (NTFS read only access) using totem. Everything worked fine, but suddenly some songs refused to play. Totem showed the following error:

[I]Totem could not play 'file:///media/windows/Music/Elvis Presley\The Top Ten Hits Disc 2\18 Good Luck Charm.mp3'.
The specified movie could not be found.[/I]

**(Is the '\' a problem?)**

But when I navigate to the directory and click on the above song directly, it plays fine. So I went back to windows and created a new playlist and saved it as **.pls** file. **This time none of the songs played on totem**. Same error message as above. At least m3u worked for some songs.

Real player and xmms are even worse. 

**Realplayer gives this message (for BOTH playlists and individual mp3 files)**
*Cannot open the audio device. Another application may be using it.*

In xmms, when I open the playlist, the playlist keeps scrolling non-stop at great speed. Note again, I dont have this problem while clicking on an individual mp3 file, only with pls/m3u.

BTW, I have not tried playing a playlist file directly on Ubuntu partition.

Is there a solution?](*,)

---

### Post by Stealth on 2006-04-21
The thing is that an .m3u file is pretty much a list of the songs and the directory there in. It could very well be a slash problem to get it working that way, but what you should do is try making the playlist **in** Ubuntu, that way, the directories and stuff are all relative to Ubuntu, and it can find the files. Instead of trying to read a playlist that has its menu structure in "Windows form"

---

