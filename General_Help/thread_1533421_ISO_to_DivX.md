---
title: "ISO to DivX"
date: 2010-07-17
forum: General Help
---

### Post by Lyerae on 2010-07-17
Well, I've got a couple DVDs in .iso format, and I'd like to convert them to DivX, but I can't see to get anything to load the .iso.

I've also tried mounting it and loading it, and it doesn't work.

Can anyone tell me what I'm doing wrong?

---

### Post by Spr0k3t on 2010-07-18
First off, create a directory in /media/iso, then mount the file you want.  Here's the quick code you need to do it from a terminal.

```
sudo mkdir /media/iso
sudo mount filename.iso /media/iso/ -t iso9660 -o loop
```

To unmount, just type 'sudo umount /media/iso' at the terminal and you're done.

---

### Post by techunit on 2010-07-18
Well assuming these are already decrypted or not encrypted... you can extract them to a folder and use handbrake to convert them into h.264 ... DivX isn't an opensource driver so it is limited for an opensource operating system... [here is a video on using handbrake]("http://ubuntuvideotutorials.wordpress.com/2010/07/13/trancode-video-in-ubuntu-with-handbrake/")...

---

### Post by jocko on 2010-07-18
> **techunit said:**
> ... DivX isn't an opensource driver so it is limited for an opensource operating system...
Not true. DivX may be closed source, but there is nothing preventing you to use it in an open source os. Why would there be?
As far as I can see, DivX support is included in ffmpeg, so any dvd rip software using ffmpeg should be able to make DivX files.

One program that will do it is is dvd::rip. It's in the repos (the package is named dvdrip).

---

### Post by techunit on 2010-07-18
> **jocko said:**
> Not true. DivX may be closed source, but there is nothing preventing you to use it in an open source os. Why would there be?
As far as I can see, DivX support is included in ffmpeg, so any dvd rip software using ffmpeg should be able to make DivX files.

One program that will do it is is dvd::rip. It's in the repos (the package is named dvdrip).

I should have made myself clearer it is not easy to integrate encoders for closed source software... decoders are given away for free in most cases. what is important is that it is hard to do... h.264 isn't open source either but it is more open... You are right it is part of ffmpeg so you could use it...

 Handbrake is by far the fastest in my opinion but honestly if you don't have a mulicore computer your not going to be able to convert the ISO files to video in a timely manner.

---

