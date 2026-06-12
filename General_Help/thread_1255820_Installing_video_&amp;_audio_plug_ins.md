---
title: "Installing video &amp; audio plug ins"
date: 2009-09-01
forum: General Help
---

### Post by SISU1375 on 2009-09-01
I was trying to install video  & audio plug ins to play some some songs.   I went into Add/Remove & ticked the options, but when the administrative password came up, my account password did not work.  How do I do this?

---

### Post by sblunix on 2009-09-01
Your account password should work if you are the only user on your linux, are you sure you used the right password?

either way try typing ```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
sudo aptitude install nonfreecodecs
``` and it will install all the media codecs but prompt for your pass prompt for your pass, and see if you can get the right pass working... :\

---

### Post by mthalis on 2009-09-01
Read this it describe how to play video,mp3...
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

---

### Post by Villiam on 2009-09-01
You can try installing vlc player so you will be able to play and install audio and video plugins. Read this for more:

[http://en.kioskea.net/forum/affich 21675 vlc for ubuntu 8 04]("http://en.kioskea.net/forum/affich-21675-vlc-for-ubuntu-8-04")

---

### Post by SISU1375 on 2009-09-03
Got it all!  Thanks!

---

