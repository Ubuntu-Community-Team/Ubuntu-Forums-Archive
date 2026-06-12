---
title: "downoad rm files to computer"
date: 2009-09-22
forum: General Help
---

### Post by sponsoredwalk on 2009-09-22
I'm having problems trying to save rm files from the Berkley website  - [http://webcast.berkeley.edu/course_details.php?seriesid=1906978487](http://webcast.berkeley.edu/course_details.php?seriesid=1906978487). 
I click the link and it asks me to play or save the rm file so if I click download it saves a file maybe 70kb in size. I can watch them with vlc fine it's just that i need most of them for offline use, is there a program on ubuntu or a way to edit the link, idk?

---

### Post by jocko on 2009-09-22
Those .rm files are just links to the actual streams. I opened one in gedit and got an rtsp:// address. I don't know if that helps you, as I think the rtsp address is not a link to the real file but more of a command that tells the remote server to stream the file for you...

---

### Post by sponsoredwalk on 2009-09-22
Thanks for the reply. Eh, a .rm file is strange enough to me, let alone an rtsp link, the best I've got so far is using real player to stream them, but it doesn't solve my problem of saving them for offline purposes and, as a result, is causing me to restructure the next 3 weeks to accommodate it. I really hope there is a way to bypass this problem using some linux program or smart workaround!!!

---

### Post by jocko on 2009-09-22
> **sponsoredwalk said:**
> Thanks for the reply. Eh, a .rm file is strange enough to me, let alone an rtsp link, the best I've got so far is using real player to stream them, but it doesn't solve my problem of saving them for offline purposes and, as a result, is causing me to restructure the next 3 weeks to accommodate it. I really hope there is a way to bypass this problem using some linux program or smart workaround!!!
Other than asking the people responsible for those files to give you access to them, I don't think you can do anything else than watching the streams...

---

### Post by CatKiller on 2009-09-22
> **sponsoredwalk said:**
>  I click the link and it asks me to play or save the rm file so if I click download it saves a file maybe 70kb in size.

Those are essentially playlist files; text files that contain the location of the stream. You can use MPlayer to read the playlist and then save the resulting stream. It's been a while since I've done this, so I may have got it slightly wrong, and there may be an easier way still, but something like this should work.

```
mplayer -playlist *LocationOfRMFile.rm* -dumpstream -dumpfile *NameYouWantToCallTheFile*
``` You can get a bit more sophisticated and convert the format as part of this command too if you want. MPlayer is capable of many things.

---

