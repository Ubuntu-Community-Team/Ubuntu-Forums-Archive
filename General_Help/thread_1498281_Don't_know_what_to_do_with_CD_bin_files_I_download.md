---
title: "Don't know what to do with CD bin files I downloaded"
date: 2010-05-31
forum: General Help
---

### Post by steve509 on 2010-05-31
I downloaded, through the torrent, the Pink Floyd's Live in Gdansk concert. It first downloaded as an ISO and when I unzipped I now have 5 CD folders with bin files in them. I've searched and followed many different instructions to open the bin files but nothing is working. Can someone PLEEEAAASSSEEEE!!!!! tell me how to be able to listen to the music??
Thanks so much
Steve509

---

### Post by StuartN on 2010-05-31
I am not sure that advertising your abuse of copyright on a public forum is appropriate, but wouldn't you just burn an ISO using Brasero or Gnomebaker or whatever you normally use?

---

### Post by steve509 on 2010-05-31
The download was from the Cable channel that played the concert so i didn't think it would be illegal. When I try to burn the file to a dvd all I get is that the file is too big to burn onto the dvd

---

### Post by StuartN on 2010-05-31
> **steve509 said:**
> the file is too big to burn onto the dvd

Perhaps it is a dual layer (9 GB) DVD - isn't that concert a 120 minute film? You could try mounting the ISO file. One method is:

```
sudo mkdir /media/isoimage
sudo modprobe loop
sudo mount file.iso /media/isoimage/ -t iso9660 -o loop
```

And then **sudo umount /media/isoimage** when you have finished.

---

### Post by steve509 on 2010-05-31
OK, I feel like an idiot!!! its not an ISO file, its a TPB.torrent file

---

