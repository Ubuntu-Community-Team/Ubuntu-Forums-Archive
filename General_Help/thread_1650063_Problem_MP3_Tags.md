---
title: "Problem MP3 Tags"
date: 2010-12-21
forum: General Help
---

### Post by jhmaccuish on 2010-12-21
Hello,

I have been editing MP3 tags with Easytag and it has worked for nearly all files but I have some files that when I open them with Easytag,gtkpod Manager, or MusicBrainz Picard, they display the new tags. But when I open these files with Rhythmbox player and when I look at the file properties I see the original pre-editing tags. I know I can change the artist, album, etc. in Rhythmbox player but that just seems to be a local change and I was more concerned by the audio properties of the file showing the old value because I don't want to have to go back and edit the tags again.

Any suggestions would be great.

Jamie.

---

### Post by veggen on 2010-12-21
I don't use Rhythmbox so I have no clear solution, but... Could it be related to ID3v1 vs ID3v2 issue or ID3 vs APE? Maybe you have different values in one than the other and for some reason Rhythmbox prefers the old ones. Check if both ID3 tags (i.e. v1 & v2) have the same data.
Also, it might just need a sort of refresh in Rhythmbox. Many media-library type programs cache this sort of data and won't refresh the file before you play it or execute a manual refresh.

---

### Post by jhmaccuish on 2010-12-29
Hi,

Sorry for the late reply, I don't use the forum very often and I though that if I created a thread any answers would automatically get sent to my e-mail account but it didn't. I will subscribe to this thread to be sure. Anyway, I'm pretty sure it isn't a question of cached data as I've emptied the rhythmbox player library and recreated it, made copies of the files and anything else I could think of and none of it has solved the problem. In the various programs that I've use the preferences all seem to say that both ID3v1 and ID3v2 tags will be updated but I can't find a way to check the value of both side by side. 

Many thanks,

Jamie.

---

