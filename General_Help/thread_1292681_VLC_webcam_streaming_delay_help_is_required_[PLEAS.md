---
title: "VLC webcam streaming delay help is required [PLEASSE]"
date: 2009-10-16
forum: General Help
---

### Post by moss12 on 2009-10-16
I am having some delay here when I stream with VLC my setup as follows my wevcam is labtec
vlc version 0.8.6 i tried the latest version has so many bugs in it which didn't work for my purpose
video device name: labtec webcam
Audio: none
cache: 100
play locally
rtp: 239.255.100.100
encapsulation: mpeg-ts
transcoding: wmv1, 64, 0.5
ttl: 12

seems like no one knows by the searching i done anyone out there with a solution

thanks :-)

---

### Post by Baelus on 2009-10-16
The transcoding is probably the cause of the delay.

I use this for better quality as there is no compression AFAIK.

```
vlc -I dummy v4l:///dev/video0 --sout #standard{access=http,mux=asf,dst=10.0.0.6:1234}"
```

The "-I dummy" is to give a window without playback controls. Just looks a bit neater.

---

### Post by moss12 on 2009-10-17
thanks for the reply Baelus
but I have no choice but to use multicasting for the project 
multicast address iam using 239.255.100.100

---

