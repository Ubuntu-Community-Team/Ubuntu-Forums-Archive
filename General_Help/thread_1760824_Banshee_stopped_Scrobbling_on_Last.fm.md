---
title: "Banshee stopped Scrobbling on Last.fm"
date: 2011-05-17
forum: General Help
---

### Post by xxhopingtearsxx on 2011-05-17
Banshee used to scrobble on Last.fm..
Turned on computer today, listened to a song, checked out Last.fm.. it's not doing it.
Can someone help?
I'm getting sick of unnecessary bugs.

Sometimes it works (a huge delay though)
But it's so sketchy, it's very frustrating.

---

### Post by xxhopingtearsxx on 2011-05-17
Bump

---

### Post by xxhopingtearsxx on 2011-05-17
Bump.

---

### Post by xxhopingtearsxx on 2011-05-17
[size="4"]bump
[/size]
This is so frustrating.
Everything on Ubuntu so far seems to be buggy..

---

### Post by xxhopingtearsxx on 2011-05-17
Bump.

---

### Post by xxhopingtearsxx on 2011-05-17
Bump.

---

### Post by hvbakel on 2011-05-17
Last.fm has been sketchy for me in the past couple of days, maybe the problem is on their side?

---

### Post by xxhopingtearsxx on 2011-05-18
Well the thing is, this never happens on Windows or Hackintosh.

I'm currently on Windows 7 (because I'm using the program ljArchive on it) and it's scrobbling just fine.

---

### Post by hvbakel on 2011-05-18
Probably not the answer you're looking for, but you could try using rhythmbox rather than banshee. Last.fm has never really worked properly for me in banshee (plays maybe 4-5 songs in a row and then looses the connection).

---

### Post by Tornikee on 2011-10-02
I have the same problem w/ Banshee. There wasn't any problem when using Rhythmbox, although I do really prefer Banshee so wanted to check if there are any newly found solutions to Banshee/Last.fm scrobbling issue.

---

### Post by Tornikee on 2011-10-04
Nothing? : (

---

### Post by Cyb3rD0n Architectus on 2011-10-18
Hi,

I have the same problem for over two weeks now. Since I'm using Banshee 2.20, Last.fm scrobbling has been interrupted. I upgraded from 2.0 > 2.2 when using Ubuntu 11.04, but now I've upgraded to 11.10 and the problem is still there. When opening Banshee from the Terminal I get this message when connecting to my Last.fm account:

```

[Warn  15:12:51.361] Failed to handshake - System.Net.WebException: Aborted.
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0
  at Lastfm.AudioscrobblerConnection.HandshakeGetResponse (IAsyncResult ar) [0x00000] in <filename unknown>:0
[Info  15:13:05.259] Last.fm authorization result = None
```


I even completely uninstalled Banshee 2.2 from Ubuntu 11.10, rebooted and re-installed it, but it wouldn't help. :(

I hope this will help solving my problem, as I don't know how to solve it myself...

---

