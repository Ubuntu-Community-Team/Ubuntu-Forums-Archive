---
title: "Unable to open music files"
date: 2009-08-15
forum: General Help
---

### Post by unknown user on 2009-08-15
I have downloaded a music file and I am unable to open it as I get there error message stating that audio/x-asf is not installed.

How can I install this and get the music file to open?

Cheers,

---

### Post by East82 on 2009-08-15
Try this:

[http://www.linuxidentity.com/us/down/articles/Ubuntu_810_codecs_US.pdf](http://www.linuxidentity.com/us/down/articles/Ubuntu_810_codecs_US.pdf)

---

### Post by sblunix on 2009-08-15
Or you could add the Medibuntu Repository To your sources using this command in terminal: ```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
``` Then clicking this link to play most audio formats: [non-free-codecs]("apt:non-free-codecs")

---

### Post by unknown user on 2009-08-15
Thanks but nope no good still the same.
It has the same error message.
Why is it so hard to get ubuntu to work?

---

### Post by credobyte on 2009-08-15
w32codecs ( or w64codecs ) from Mediabuntu should fix this issue.

---

### Post by unknown user on 2009-08-15
Sorry how do I get this w32 or w64 as not know?

---

### Post by credobyte on 2009-08-15
> **unknown user said:**
> Sorry how do I get this w32 or w64 as not know?

If you have enabled Mediabuntu repository ( read previous posts in this thread ):
```
sudo apt-get install w32codecs
```

---

### Post by unknown user on 2009-08-15
Installed both links fro sblunix
and then run sudo apt-get install w32codecs
but still getting the error message:

The playback of this movie requires a audio/x-asf-unknown decoder plugin which is not installed.

---

