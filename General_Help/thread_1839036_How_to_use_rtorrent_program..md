---
title: "How to use rtorrent program."
date: 2011-09-04
forum: General Help
---

### Post by yushisune511 on 2011-09-04
1.How to download .torrent with curl program.
2.I make a list and ctl^s for start download but it said "miss key","can not resolve host"

How can I do for the problems.

---

### Post by papibe on 2011-09-04
I think this rtorrent [User Guide]("http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide") is pretty good.

I would use wget to get the torrent file. For example to get the Ubuntu Desktop torrent:
```
$ wget http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent
```
Hope it helps,
Regards.

---

### Post by yushisune511 on 2011-09-08
> **papibe said:**
> I think this rtorrent [User Guide]("http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide") is pretty good.

I would use wget to get the torrent file. For example to get the Ubuntu Desktop torrent:
```
$ wget http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent
```Hope it helps,
Regards.

I cann't found the way to do about 'Failure reason "missing key"'.
Can you give basic config in .rtorrent.rc for me?

---

### Post by yushisune511 on 2011-09-08
[View: main]
*  Erotibot.iso
*              0.0 / 4225.6 MB Rate:   0.0 /   0.0 KB Uploaded:     0.0 MB [ 0%] --d --:-- [   R: 0.00]
* Tracker: [Failure reason "missing key"]

---

### Post by andrew.46 on 2011-09-08
If rtorrent is giving you grief perhaps start with a more straightforward bittorrent client such as Transmission?

---

### Post by haqking on 2011-09-08
> **andrew.46 said:**
> If rtorrent is giving you grief perhaps start with a more straightforward bittorrent client such as Transmission?

+1

indeed so many good ones out there.

qbittorrent works great as does deluge as does transmission etc.

the list goes on with great torrent clients

---

### Post by nothingspecial on 2011-09-09
If you have to do it from the console try transmission-cli

the -u flag limits upload speed

the -d flag limits download speed

The capital letter will set no limit, so if you want unlimited download but an upload limit of 100kbs for example.

```
transmission-cli -D -u 100 http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent
```

There are other options such as -er for requiring encryption etc, check the man page. It's great for grabbing a one off torrent rather than seeding multiple files and stuff.

---

