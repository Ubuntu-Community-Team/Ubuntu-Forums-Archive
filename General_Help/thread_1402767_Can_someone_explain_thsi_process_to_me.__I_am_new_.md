---
title: "Can someone explain thsi process to me.  I am new to ubuntu"
date: 2010-02-09
forum: General Help
---

### Post by Waveridr85 on 2010-02-09
Create a directory in for example your  [COLOR=#0d3799][home]("http://linx.chitika.net/track?target=http%3A//rc.us-east.srv.overture.com/d/sr/%3Fxargs%3D20AGWAnRb1USNTJsQHGeSmxIuynS51dez9A70tR3T3Xdyl9434Xv2oWS7gifTOItZEQCxETFLCTjuvnVD5_i1JaIEnKXbUUWXXPN0pQOP6zy8RsS5PL_3HI5CKkpHwdk9gJfGq-cNTQDOQxar97lUIP1QCuE3EZx-k116TTovzSIe08QUMgLaiZINVUxhDf2EdwhIaA4iJRca-ikeSHfnGU3HeD5LyExZQy0-5_SSwOqfZ.000000024ca26891%26op%3D5187c78&xargs=XxAO3IPsd%2Bb/ZEyvTQPMUfw4k83oKFMfYjNzt3gQfQiUI0%2BE2ZOdIdoVItpMc8do1SUAk8TR9qhIkc7CLBiMtMId8g//3UJNaO1ik6C4LjMI6PxQ38ix8MAoqkRZp0dNYAQGCmbrO8HPH2M3uEleTykFE9l3KyMVHXuV29VJdGXNsTO7s1cRescs8v8Iv0VWiOF7GIJ7pydccvk%2BmObgFH%2BfqUGAD%2Br/DvDLcEyrE9dxK34Rby187lO0911ZPjHoj5PisFmA3oPYNyR7EaUFgw6ePwVz/cjX87lbI4Bk5xl7jzIgzS5O7a4G5gcJIDB/&keyword=home")[/COLOR] directory to keep all the files
cd ~/

mkdir rt2870

cd rt2870

---

### Post by Waveridr85 on 2010-02-09
This is after I get build-essential via terminal

---

### Post by patchwork on 2010-02-09
These instructions do the following:

1. cd ~/   ##change to home directory, eg  /home/<username>

2.  mkdir rt2870     ## create a directory within the user's home directory called rt2870

3.  cd rt2870      ## change to newly created directory,  /home/<username>/rt2870

---

### Post by Waveridr85 on 2010-02-09
> **patchwork said:**
> These instructions do the following:

1. cd ~/   ##change to home directory, eg  /home/<username>

2.  mkdir rt2870     ## create a directory within the user's home directory called rt2870

3.  cd rt2870      ## change to newly created directory,  /home/<username>/rt2870

Where and when do I enter this?

---

### Post by Vaphell on 2010-02-09
these are commands you put in terminal

---

### Post by 3rdalbum on 2010-02-09
Linux contains drivers for lots of hardware, including the rt2870 **(so don't try installing a driver for it!)**. However, as you've discovered, it doesn't "just work" properly in Ubuntu 9.10.

This is the solution:

Hit Alt-F2 and type the following:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

This opens a text configuration file. Add the following to the bottom of it:

```
blacklist rt2800usb
```

Save changes, shut down completely and start up again.

---

