---
title: "Audio Duration Zero"
date: 2010-05-07
forum: General Help
---

### Post by simptechmike on 2010-05-07
I recently did a fresh install of 10.04 and am experiencing a really weird issue. I right click on an audio file (in my case an MP3) and pull up the properties. I select the Audio tab and look at the duration for the file. All of my file (which play just fine) are showing a zero duration. Is this a known bug and is there a fix for this somewhere?

I should note that these are all valid MP3 files, with duration time previously showing under a 9.10 install.

---

### Post by jbrown96 on 2010-05-07
You probably need to install lame to read mp3s. Better yet install ubuntu-restricted-extras to get all the codecs you need. ```
sudo apt-get install lame
``` or ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by simptechmike on 2010-05-07
> **jbrown96 said:**
> You probably need to install lame to read mp3s. Better yet install ubuntu-restricted-extras to get all the codecs you need. ```
sudo apt-get install lame
```

The restricted extras I had installed. Installed lame and that was the fix. Thanks.

Edit. I though this fixed it but I rechecked and no go.

---

### Post by simptechmike on 2010-05-07
Ok. I am updating this thread as it seems to be a much bigger issue than simply audio files. I have tested both MP3 and Ogg audio files as well as avi video files. They all come out as 0 seconds for duration. So, I'm assuming this is a Nautilus problem. I have Nautilus 2.30.1, which came with 10.04. I see nothing anywhere say this is a bug in this version, but believe something is up. Anyone else having this issue??

More Updates:

Just ripped a few CDs to MP3s, which all play just fine yet Nautilus shows them all having a length of 0 seconds. I'm convinced this is a Nautilus issue. Hopefully Nautilus is updated.

---

