---
title: "Where to begin...?"
date: 2010-11-14
forum: General Help
---

### Post by Delfofthebla on 2010-11-14
If this topic belongs in another forum feel free to move it, I wasn't really sure where to ask the question.

To start off I'd like to say that I dual boot Windows 7 and Ubuntu. I just recently reinstalled ubuntu and haven't used it since version 7 or 8. I also run windows and ubuntu on completely different drives.

I do a lot of torrenting. My torrent folder is somewhere around 150-200gigs, and takes up quite a lot of space. One of the main problems I'm having with ubuntu stems from this. I want to be able to torrent from my ubuntu drive, and have it save everything onto my windows drive. I want to seed my torrents from the windows drive--while I am on ubuntu. I'm pretty sure that's possible, but doing it without conflicting with the windows drive is proving to be a problem.

I use uTorrent to do all my torrenting. Files are downloaded into my User/Torrents/Downloading/ folder, and then moved to User/Torrents/TORRENT_LABEL/ folder upon completion. They are organized based on the label I give them, and this is important.

uTorrent doesn't work on Ubuntu, at least not yet. The server version doesn't work with labels, and I just couldn't seem to get anything working very well.

So, my question is this. Is there a way that I can store all of my torrents in an organized manner on my windows drive while seeding and maintaining that organization when I am on Ubuntu?

---

### Post by ivarn on 2010-11-14
So what you say is, you can't access your windows partition from ubuntu?
Ok install NTFS-Config from synaptic and there you'll see the NTFS partition used by Windows. Mount it. Now it will ask for permission to read/write to and from the partition, click yes. When this is done, reboot and you'll be able to browse your windows files from ubuntu. Now go to the torrent program and when you save a file, browse in to your windows partition and save the file wherever you want.
The new location will be saved so you don't have to do this again unless you delete the target folder where you save your files.

---

### Post by Delfofthebla on 2010-11-14
> **ivarn said:**
> So what you say is, you can't access your windows partition from ubuntu?
Ok install NTFS-Config from synaptic and there you'll see the NTFS partition used by Windows. Mount it. Now it will ask for permission to read/write to and from the partition, click yes. When this is done, reboot and you'll be able to browse your windows files from ubuntu. Now go to the torrent program and when you save a file, browse in to your windows partition and save the file wherever you want.
The new location will be saved so you don't have to do this again unless you delete the target folder where you save your files.

Sorry, the problem is kind of hard to explain. I can access my windows partition just fine. I'm basically looking for torrent software that can mimic what uTorrent does in windows. (Moving completed torrents to specified folders based on their labels or categories)

---

### Post by armware on 2010-11-14
ktorrent has been a wonderful replacement for utorrent for myself (it will do the 'move completed torrents' and other niceties), though deluge has some neat stuff going for it, too.

lets not overlook that you can run utorrent via wine.

---

### Post by Delfofthebla on 2010-11-14
> **armware said:**
> ktorrent has been a wonderful replacement for utorrent for myself (it will do the 'move completed torrents' and other niceties), though deluge has some neat stuff going for it, too.

lets not overlook that you can run utorrent via wine.

I'll check out ktorrent later, thanks. As for wine + uTorrent, that was a no go for me. Unless you have a method of "linking" a folder in wine to a separate hard drive, I have to find a replacement for uTorrent. I wasn't able to have it find anything other than the C drive.

---

### Post by hakermania on 2010-11-14
utorrent runs perfectly with wine. Btw I use transmission

---

### Post by Delfofthebla on 2010-11-16
Sorry for the late reply, been a little busy.

After I made links to the original torrent folders, uTorrent seemed to be working just fine within wine. However, it was unbearably laggy for some reason, and I questioned whether or not the seeding would be effected by it. So I gave ktorrent a try, and it's working great.

I was able to set up categories and specific download folders for each one, and have those folders be "links" to my windows drive, effectively solving the problem.

Thanks. :)

---

