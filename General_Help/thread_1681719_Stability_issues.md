---
title: "Stability issues"
date: 2011-02-04
forum: General Help
---

### Post by samer2 on 2011-02-04
Hello,

I am a new Ubuntu user. I have actually switched from Windows 7 after being fascinated about the great services Ubuntu was offering freely to its users. Since it's only been two days, I don't think that Ubuntu is doing quite well with my Compaq Laptop. because I'm experiencing some serious freezes and crashes while playing media files (videos and audios) while performing other tasks such as downloading and/or installing new software. Like for example, the sound cuts several times until it becomes unbearable.

Are these problems normal?? if not, which is what I think, can you please guide me through solving them.


By the way, I have fully formatted my machine and have made Ubuntu install as if it was being installed for the first time on a new computer.


Thanks for helping,

---

### Post by Rocket2DMn on 2011-02-04
This is definitely not normal.  What application(s) are you using for media, and which ones are causing problems?  We usually suggest installing the *ubuntu-restricted-extras* package since it has non-open source codecs that provide the best support for audio and video codecs (e.g. mp3). You can search for it in Applications->Ubuntu Software Center or install from terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
You may need to enable the Multiverse repository first, check System->Administration->Software Sources

You can also check out the Medibuntu repository which has codecs for audio and video.  Check out [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
TBH though, I'm not sure how relevant that resource is these days.  It's worth checking out if you don't get everything you need from *ubuntu-restricted-extras*, particularly for the *libdvdcss2* and *w32codecs* or *w64codecs* packages (depending on if you're using a 32 bit of 64 bit installation of Ubuntu).

---

