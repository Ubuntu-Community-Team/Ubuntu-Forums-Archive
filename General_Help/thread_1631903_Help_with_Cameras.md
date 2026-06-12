---
title: "Help with Cameras"
date: 2010-11-27
forum: General Help
---

### Post by dpwilson on 2010-11-27
I have been searching the forums and all over the internet.  

I am running ubuntu 10.10 and have problems getting pictures from my camera using any photo program (f-spot, picasa, etc).  When I plug in the camera, it shows up in "Places" and under "Computer", it even brings up f-spot or whatever I have set to open under media handling in the nautilus preferences, however, when f-spot or picasa open, the camera is listed, but there are no pictures detected.  I can click import in f-spot and it will import the pictures, but when I click on one of them to enlarge it, f-spot crashes and the pictures are no longer there when I reopen it and are not actually saved on the computer in the pictures folder as specified.

I can open the camera in nautilus and drag them to a folder.

If I remove the card from the camera and use a card reader I can import the photos using fspot, picasa or any other photo program.  

I hope thats not too much info and is not too confusing.  The camera(s) show up in lsusb.  I say cameras because it is not limited to one make/model.

```
wilson@wilson:~$ lsusb
Bus 002 Device 002: ID 03f0:4d11 Hewlett-Packard PSC 1400
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 04b0:0314 Nikon Corp. 
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Any help is certainly appreciated.

---

### Post by dpwilson on 2010-11-28
Update: I installed gthumb and gphoto2 and it is working, that is, will import pictures directly from the camera.  Still not working with any other programs I have tried.

Would like to figure this out and get it working with f-spot.  

Any advice?

---

