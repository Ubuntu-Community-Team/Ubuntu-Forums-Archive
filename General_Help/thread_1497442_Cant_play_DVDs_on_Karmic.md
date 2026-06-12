---
title: "Cant play DVDs on Karmic"
date: 2010-05-30
forum: General Help
---

### Post by alxpenguin on 2010-05-30
I just upgraded to Karmic, I had not previously tried to play dvds but i cant seem to get it to work. I downloaded VLC to see if thta would fix it but to no avail. Any ideas?? I also downloaded a restricted date allowance package but nothing works. It doenst say it cant play it, it just wont start at all. Thanks

---

### Post by todak on 2010-05-30
You probably need to install libdvdcss2 from the Medibuntu repository. See [here]("https://help.ubuntu.com/community/Medibuntu") to enable the repository and install the file needed to watch DVDs.

---

### Post by Swagman on 2010-05-30
Or he can click the blue help button on his top menu bar and look in **Music, Video and Photos** / "Playing DVD's"

On Karmic he would usually just need to copy & paste this into a shell

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by alxpenguin on 2010-05-30
Still not working...

---

### Post by Swagman on 2010-05-30
Have you activated the hardware driver for your graphics card ?

---

### Post by alxpenguin on 2010-05-30
Yeah I did activate the card drivers

---

### Post by alxpenguin on 2010-05-30
I did what you suggested and still all that happens is I get asked if I wanna open with movie player, I say yes, it opens without playing and automatically closes again...

---

### Post by Swagman on 2010-05-30
> **alxpenguin said:**
> Yeah I did activate the card drivers

And rebooted ?

If so then you'd better try installing medibuntu repos as stated a couple of posts up.

---

### Post by alxpenguin on 2010-05-30
The graphics cars I did a few days ago. I did the medibuntu stuff also....nothing...any other ideas??

---

### Post by Swagman on 2010-05-30
just for the query (it shouldn't matter either way)

nVidia or Ati ?

oh.. silly as it sounds... Is that really a dvd drive you have in that machine or a cdrw ?

---

### Post by alxpenguin on 2010-05-30
Nvidia and yes its a dvd drive though I can understand why you ask lol

---

### Post by alxpenguin on 2010-05-30
This is what it get when I try to open and this is what I get on the terminal when I did the download of the libv package. I also did the medibuntu and nothing works...its a brand new dvd disc it should work....

---

### Post by alxpenguin on 2010-05-30
Ok I tried a different idsc and it worked! Why does my pc hate the criterion collection version of fear and loathing in las vegas? could it be a region thing???

---

### Post by alxpenguin on 2010-05-30
Indeed it was a region issue!! I installed the region change program and now its working just fine! thanks for all the help guys!!

---

