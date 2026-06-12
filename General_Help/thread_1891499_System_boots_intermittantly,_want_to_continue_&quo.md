---
title: "System boots intermittantly, want to continue &quot;Transmission&quot; on separate system"
date: 2011-12-05
forum: General Help
---

### Post by unckybob on 2011-12-05
I dropped my laptop and it starts sometimes, sometimes not. I have using "Transmission" I have downloaded some really large files to an external hard drive. Some of these files are over 50Gs. I can still start the system up sometimes, so I can still get some information about the downloads from it.

I have a new system now and I would like to continue the downloads on the new system. Rather than start the downloads all over again, I would like to use part of the files I have already downloaded. 

Can someone please tell me how to do this?

---

### Post by papibe on 2011-12-05
I've done it using transmission-daemon, which it shouldn't be that different.

First copy all the data on the directory transmission downloads the date (usually ~/Downloads).
Then you need to get important data from the directory ~/.config/transmission
The torrents subdirectory contain the torrents already loaded. You need that so you don't load them again.
The most important part is in the resume directory. Here you'll find the status of what has been already downloaded and what is yet missing (in blocks). This would make the verify data process very fast!

Once you have copied everything, torrent should start as they were interrupted. As a double security measure, I would paused them all, and then one by one I would 'verify local data'.

Hope it helps.
Regards.

---

### Post by unckybob on 2011-12-24
I transfered the files to the "Download" folder. Then I managed to find the original torrent. Then used "verify files" and it downloaded using what had already been downloaded. Not what you recommended, but it works. Thanks all the same.

---

