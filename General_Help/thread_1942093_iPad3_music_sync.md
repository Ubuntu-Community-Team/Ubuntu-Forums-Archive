---
title: "iPad3 music sync"
date: 2012-03-16
forum: General Help
---

### Post by wocsnia on 2012-03-16
All,

I have bought myself a shiny new iPad 3 today, I wish to use ubuntu 11.10 to sync it etc...

libimobiledevice seems to identify it correctly and I am able to browse the files, however, sync in banshee does not seem to work.

Banshee is unable to see the music on the iPad (there are two albums downloaded from itunes). Then when it tries to sync, it fails.

Any ideas?

---

### Post by wocsnia on 2012-03-19
Anyone else had problems/attempted this?

---

### Post by wocsnia on 2012-03-22
I found the solution.

It seems banshee or maybe libimobiledevice doesnt like filenames with non-standard characters.

My iPad was named "Alex's iPad". I renamed it (using itunes on a VM) to "alexipad". This caused banshee to be able to understand it fully, upload tunes etc... I expect it was the ' which it didnt like... Although, I guess it could have been the space.

Now all ubuntu needs is to be able to upload photographs, and I will be iTunes free!!!

---

### Post by cprofitt on 2012-03-22
Even though you solved this yourself you can mark the thread solved. This will help others by letting them know the solution was found.

---

### Post by wocsnia on 2012-03-22
> **cprofitt said:**
> Even though you solved this yourself you can mark the thread solved. This will help others by letting them know the solution was found.

Good point, I will do this in future. Thanks.

---

### Post by megabuffen on 2012-04-07
I've tried doing this, but the problem remains. Banshee indicates a successful sync, but the songs do not show up on the device.

---

