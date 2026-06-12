---
title: "Syncing Music with iPod"
date: 2012-05-16
forum: General Help
---

### Post by timg37 on 2012-05-16
So I'm trying to put some music on the iPod touch my dad gave me. Rhythmbox recognizes the iPod when I plug it, but when I drag the music files I want to it, nothing happens, they don't show up in my "Music" on the iPod or when I click on the iPod in Rhythmbox. I don't even see where to sync with the iPod on Banshee, there is no "Devices" tab where the iPod should show up and there are no options anywhere to sync music. GTKPod say's "Import Repository Errors. Errors created during repository import" when I start it up and crashes whenever I try to add my music library to it. Any suggestions or other software I should try?

Using:
Ipod Touch 2g 32GB MB533LL
Ubuntu 12.04

---

### Post by Enigmapond on 2012-05-16
Try Guayadeque. Works great with external devices and IMHO is the best audio player available.

```
sudo add-apt-repository ppa:anonbeat/guayadeque && sudo apt-get update && sudo apt-get install guayadeque-svn
```

---

