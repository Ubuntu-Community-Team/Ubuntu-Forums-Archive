---
title: "seed torrents on Deluge not working?"
date: 2010-01-16
forum: General Help
---

### Post by Arminius on 2010-01-16
my torrents upload fine when they are peers, but as soon as they finish and become seed's they stop working.

they haven't uploaded a single time since becoming seeds.

---

### Post by JBAlaska on 2010-01-16
1-Do you have your port forwarded properly to allow incoming connections?
2-Are you on comcast or another ISP that may be "Traffic Shaping" P2P Traffic?

---

### Post by Arminius on 2010-01-16
incoming and outgoing ports is set to random

well I'm with the same ISP I was with when I was using transmission, and the seed files worked fine then.

---

### Post by Arminius on 2010-01-23
under incoming connections in the preferences I have ports 6881 to 6891, but when click on test active port it comes up with !

not very helpful in how to fix that.
and at the very bottom bar of deluge it reads no incoming connections.

this must be at the heart of what's wrong.
any ideas?

---

### Post by falconindy on 2010-01-23
Make sure your seed limits aren't being reached. You can find them under the 'Queue' section of the preferences.

---

### Post by Arminius on 2010-01-23
nah seed queue is fine

---

### Post by falconindy on 2010-01-23
May be expected behavior then. The following is taken from a torrent site I won't mention by name:
> **I upload when I'm downloading, but when I complete the download, I stop uploading!!**

This is normal behaviour for BitTorrent. When you are leeching, you are given some priority in connecting to any other leechers, and so will often upload data to them. However, once you finish your download, you become just another seeder and no longer have priority in connecting to leechers.

---

