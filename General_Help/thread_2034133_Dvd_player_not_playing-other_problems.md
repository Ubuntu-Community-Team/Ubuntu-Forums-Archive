---
title: "Dvd player not playing-other problems"
date: 2012-07-27
forum: General Help
---

### Post by davidzaq11 on 2012-07-27
I have been having problems with my dvd player.  I put in a disk and movie player opens but it wont play the dvd.  If I use vlc the dvd will play but the colors are inverted.  I have movies that are saved to my computer. When I try to play them, the play back is choppy and freezes for several seconds at a time. I updated from version 10.04. Everything worked perfect in that one.
Well, now I have been trying to find a video player that will work and play the videos with no color problems and plays smoothly, but every time I try install something I gety the message below.

Does anyone know how to fix this problem?   
Thank you.


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D258A9281AF466B2

---

### Post by matt_symes on 2012-07-28
Hi

You can fix the second issue by opening a terminal and copying and pasting the commands below.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D258A9281AF466B2
```

Enter your password. It will not be echoed to the screen.

```
sudo apt-get update
```

Kind regards

---

