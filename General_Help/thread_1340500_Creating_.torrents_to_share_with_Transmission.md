---
title: "Creating .torrents to share with Transmission"
date: 2009-11-28
forum: General Help
---

### Post by KayakJim on 2009-11-28
I have a number of .iso images of several Linux distributions that I have downloaded and would like to share them via BitTorrent using the built-in Transmission client.

It does not appear possible within the Transmission GUI to simply select a file and say to seed, which seems extremely strange to me.

I have spent the past hour trying to figure it out but I am apparently missing something and need some help.

According to the few useful search results, to create a new torrent I have to run:
```
transmission-cli -n [source file] -a [tracker] 
```
However I am not sure what to put for the tracker or if the above is even correct.

Any help or guidance will be appreciated.

---

### Post by KayakJim on 2009-11-29
Is there another BitTorrent client that I should be using instead of Transmission that will allow me to add files to share easier?

---

### Post by wangsuda on 2009-12-04
BUMP! Help please. How do you create a torrents file? I, too, have material to share but I have no idea on how to create a torrents file.

---

### Post by bodhi.zazen on 2009-12-04
See if this helps : [http://torrentfreak.com/how-to-create-a-torrent/](http://torrentfreak.com/how-to-create-a-torrent/)

If it is any consolation, utorrent runs in wine (last time I looked).

---

### Post by wangsuda on 2009-12-04
> **bodhi.zazen said:**
> See if this helps : [http://torrentfreak.com/how-to-create-a-torrent/](http://torrentfreak.com/how-to-create-a-torrent/)

If it is any consolation, utorrent runs in wine (last time I looked).Thanks for the help. Further investigation shows that the standard torrents client supplied with Karmic (Transmission Bittorrents Client) can make torrents. The only problem is that it reports corrupt files.

I just can't win for losing.

---

### Post by abhilashm86 on 2009-12-04
> **KayakJim said:**
> Is there another BitTorrent client that I should be using instead of Transmission that will allow me to add files to share easier?

u can try deluge with more options, its GUI, [check this.........]("http://deluge-torrent.org/")

---

### Post by wangsuda on 2009-12-05
> **abhilashm86 said:**
> u can try deluge with more options, its GUI, [check this.........]("http://deluge-torrent.org/")I installed deluge. Am experimenting now. Thanks for the tip!

---

### Post by bodhi.zazen on 2009-12-05
I fired up Transmission and it appears it will make torrents.

Torrent -> New

Add your file
Add the tracker you wish to use ...

=)

---

### Post by wangsuda on 2009-12-06
Thanks for all your help. I had success with Deluge and ran a successful test.

I haven't had the same luck with the Karmic supplied torrent program. But at least I have something that works.

Again, thanks to the community,

---

