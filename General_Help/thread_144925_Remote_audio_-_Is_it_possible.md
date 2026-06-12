---
title: "Remote audio - Is it possible?"
date: 2006-03-15
forum: General Help
---

### Post by ]Nbx*cmD[ on 2006-03-15
Hi all,

I would want to be able to listen to my local computer music from any computer without having to download each song each time.
From now on, what i've been doing is use scp to get the files and then play them, but that's a huge waste of time... so does anybody know if there is a way to play mp3 remotely? I've heard something about audio over ssh but it sounds very strange to me...
Thx! :-({|=

---

### Post by lamego on 2006-03-15
Well you just to select one of several files based sharing services like samba, ftp, NFS to share your files .
All of them would allow you to "access" your files without much work (well, FTP would need to get the entire file before playing).
Any other Ubuntu desktop system should be able to access to the files with one of those services.

---

### Post by petervk on 2006-03-15
Once you upgrade to dapper, you can share music through rhythmbox. 

It will automatically discover shared music (from itunes/rhythmbox/banshee) and put an icon in the side bar.

Other then that, trying to setup samba or NFS is probably your best bet.

---

### Post by jannol on 2006-03-15
I like to mention vlc, vlc has a built in http remote that easily can be enabled.

Then it is possible to stream music from vlc and there is also settings for user and pass for accessing the stream.

I used this to simply listen to my music everywhere and controlling the player from a browser, I think there is methods for securing the http remote page but I didn't bother when I used it.

---

### Post by ]Nbx*cmD[ on 2006-03-15
Thanks all, i think the samba solution may be the best, but to access my computer i have to pass through my "local server", so i'll have to share the local shared folder shared by the server which may result in a complete chaos lol
I'll post my achievements when i find out a solution, thx ;)

---

### Post by ]Nbx*cmD[ on 2006-03-18
Working!
Done with samba, thanks all =D>

---

