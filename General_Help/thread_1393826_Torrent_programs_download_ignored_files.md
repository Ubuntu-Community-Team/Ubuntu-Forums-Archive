---
title: "Torrent programs download ignored files"
date: 2010-01-29
forum: General Help
---

### Post by Klump on 2010-01-29
Hi, I couldn't find an answer myself. So, the problem is that every single bittorrent program I tried downloads files I checked to ignore so I know this is not a program related issue. For example, there are 2 pictures in a torrent, I select only one but in the end I have both downloaded. Ideas?

Any help is appreciated.

---

### Post by tom.swartz07 on 2010-01-29
> **Klump said:**
> Hi, I couldn't find an answer myself. So, the problem is that every single bittorrent program I tried downloads files I checked to ignore so I know this is not a program related issue. For example, there are 2 pictures in a torrent, I select only one but in the end I have both downloaded. Ideas?

Any help is appreciated.

when you download the torrent, it still downloads all of the files so you could seed to other users. When you remove the torrent, it should *theoretically* delete the files you have checked not to download.

---

### Post by Klump on 2010-01-29
Well, that is where the weirdest thing is happening. I noticed that not all the files included are downloaded. It seems like they're downloaded randomly alongside the selected ones. And the files are still there after the torrent file is removed.

---

### Post by Vaphell on 2010-01-29
i think that the unwanted files are created because they are partially present in the torrent chunks containing stuff you want. Because their part is downloaded they need to be put somewhere (and are created) but i think they are not complete - any chunk containing only unwanted data will not be downloaded.

---

### Post by ron999 on 2010-01-29
Which program are you using to download torrents?

I agree with this from Vaphell
> any chunk containing only unwanted data will not be downloaded.

---

### Post by Klump on 2010-01-29
I have tried Transmission, Deluge and qBitTorrent so far. All with same result.

> **Vaphell said:**
> i think that the unwanted files are created because they are partially present in the torrent chunks containing stuff you want. Because their part is downloaded they need to be put somewhere (and are created) but i think they are not complete - any chunk containing only unwanted data will not be downloaded.

Ah, that's similar to something I had in mind but I didn't think it might be true. What would be the use of the parts selection feature then?

---

### Post by Vaphell on 2010-01-29
torrents are like .rar's split to parts - either you download whole chunk or you don't. You can't have half of the chunk because it would be useless for everyone else. Half of the chunk = corrupted chunk from the torrent protocol perspective as the chunks are downloaded as a whole and tested with checksums to see if the data is valid.

if your torrent contains thousand of 5kB files next to the stuff you want the chances are you will get most of them as a by-product, but if you download a torrent with two 700meg avis and need only one of these, you'll save approximately 700mb of download - chunks are in hundeds of kB-few MBs range, so it means that unwanted 700meg file is built of few hundred chunks at least. if you unmark big file, those chunks will never be downloaded.

Because of how things work it doesn't make sense to unmark anything small, but when you DL let's say whole season of tv series (350MB for each ep) to get half of the episodes it makes huge difference. Other ep files may be created but will never be filled with valid data. Essentially it saves time, your download is smaller and given that it's nice to seed to 1+ ratio your upload time is shorter (important given the DL/UL speed ratio of the average internet connection being in the 10:1 ballpark)

---

### Post by Klump on 2010-01-29
I see. I believe I'll just have to live with it :) 

Thank you all for the replies.

---

### Post by lovinglinux on 2010-01-29
> **tom.swartz07 said:**
> when you download the torrent, it still downloads all of the files so you could seed to other users. When you remove the torrent, it should *theoretically* delete the files you have checked not to download.

No, that's not how it works.

> **Vaphell said:**
> i think that the unwanted files are created because they are partially present in the torrent chunks containing stuff you want. Because their part is downloaded they need to be put somewhere (and are created) but i think they are not complete - any chunk containing only unwanted data will not be downloaded.

Yes, that's how it works.

> **Klump said:**
> I have tried Transmission, Deluge and qBitTorrent so far. All with same result.

Ah, that's similar to something I had in mind but I didn't think it might be true. What would be the use of the parts selection feature then?

That's normal behavior. There are two things happening. First, the client might be using full allocation, instead of compact allocation. What that means is that the client reserves the space to download the entire file in advance to avoid fragmentation on the disk and loss of performance, so no matter how completed the download is in your torrent client, it looks like completed on your file browser (nautilus, dolphin...). But if you try to open it, it will be incomplete (videos, music) or it won't open at all (other types of files). As far as I remember,  Deluge compact allocation doesn't work on Linux and perhaps other clients have the same behavior.

The second thing happening, was already described above. Files transfered via BitTorrent are sliced into small pieces of the exact same size. You get on piece after the other, until you finally fulfill the entire file. Imagine that the torrent file is like a pizza, that you eat one slice after the other, until the pizza is completely transfered from the table to your stomach. 

When you download a torrent which contains more than one content file inside, like a music compilation for example, it behaves like a pizza of half-cheese and half-pepperoni...some cheese always get over the pepperoni, no matter how perfect you slice it. So let's say to be satisfied you need to eat all the cheese from the pizza, but you don't want the pepperoni. Unfortunately, at some point you will eventually take a bite on a pepperoni slice to get the cheese from it's border. You might even throw the pepperoni slice on the garbage can, but you need to take it from the table to get that last small amount of cheese on it's border. Nevertheless, you don't need the other pepperoni slices and you won't get them, unless the pepperoni part of the pizza is so small that fits on a single slice (torrent piece).

> **Klump said:**
> I see. I believe I'll just have to live with it :) 

Thank you all for the replies.

Yes. Avoid large torrents with multiple files.

See the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by Klump on 2010-01-30
Cheers for the guide, helped me to better understand what is what :)

---

