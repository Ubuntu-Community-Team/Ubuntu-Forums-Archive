---
title: "I can't watch DVD's on Ubuntu"
date: 2011-01-16
forum: General Help
---

### Post by MysteryPig on 2011-01-16
When I put a DVD in my computer, I can watch it on Windows XP, but not on Ubuntu. When I use "movie player", I get the error "Could not read from resource".

What do I need to do to get this working?

Any help is appreciated.

---

### Post by linuxman94 on 2011-01-16
Have you install the restricted-extras package?  If your not sure open synaptic (System -> Administration -> Synaptic Package Manager) and search for ubuntu-restricted-extras and mark it for install by clicking the white box next to its name.  If it is already installed it will be a green box and you don't need to install it.

---

### Post by Primefalcon on 2011-01-16
here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

what you'll want to do short story is to add the repository and then add either the w32codecs (if you are 32 bit) or w64 codecs (if you are 64 bit) and then for full dvd playback install sudo apt-get install libdvdcss2

---

### Post by MysteryPig on 2011-01-16
> Have you install the restricted-extras package?  If your not sure open  synaptic (System -> Administration -> Synaptic Package Manager)  and search for ubuntu-restricted-extras and mark it for install by  clicking the white box next to its name.  If it is already installed it  will be a green box and you don't need to install it. 	

Yes, there is a green box beside ubuntu-restricted-extras.

---

### Post by MysteryPig on 2011-01-16
> Have you install the restricted-extras package?  If your not sure open  synaptic (System -> Administration -> Synaptic Package Manager)  and search for ubuntu-restricted-extras and mark it for install by  clicking the white box next to its name.  If it is already installed it  will be a green box and you don't need to install it.     Yes, there is a green box beside ubuntu-restricted-extras.

---

### Post by MysteryPig on 2011-01-16
> Have you install the restricted-extras package?  If your not sure open  synaptic (System -> Administration -> Synaptic Package Manager)  and search for ubuntu-restricted-extras and mark it for install by  clicking the white box next to its name.  If it is already installed it  will be a green box and you don't need to install it. 	

Yes, there is a green box beside ubuntu-restricted-extras.

---

### Post by Primefalcon on 2011-01-16
here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

what you'll want to do short story is to add the repository and then add either the w32codecs (if you are 32 bit) or w64 codecs (if you are 64 bit) and then for full dvd playback install sudo apt-get install libdvdcss2

---

### Post by MysteryPig on 2011-01-16
I apologize for the 3 identical posts. It did not appear to have sent.

Primefalcon: Thank you very much. It appears to work, however the movie appears to be shaking. What would cause this?

---

### Post by MysteryPig on 2011-01-16
I apologize for the 3 identical posts. It did not appear to have sent.

Primefalcon: Thank you very much. It appears to work, however the movie appears to be shaking. What would cause this?

---

### Post by Primefalcon on 2011-01-16
my duel post was from that as well.... these forums have been rather problematic last few days

---

### Post by Primefalcon on 2011-01-16
what I use to watch dvd's actually is vlc

```
sudo apt-get install vlc
```

---

### Post by jcolyn on 2011-01-16
> **MysteryPig said:**
> 

Primefalcon: Thank you very much. It appears to work, however the movie appears to be shaking. What would cause this?

Install vlc and use it to watch the DVD's..

---

### Post by MysteryPig on 2011-01-16
Works Terrifically,

Thank you all.

---

