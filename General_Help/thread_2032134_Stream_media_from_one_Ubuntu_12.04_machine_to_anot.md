---
title: "Stream media from one Ubuntu 12.04 machine to another?"
date: 2012-07-23
forum: General Help
---

### Post by Matt Pellegrini on 2012-07-23
I have two ubuntu 12.04 machines, one a desktop, the other my laptop. My desktop has a tone of video files on /dev/sda6 and I want to stream these on my Laptop.

There are two ways I considered.

1) Mounting the drive /dev/sda6 on my laptop
<code>
mount //192.168.0.77:/dev/sda6   /mnt/Videos doesn't work

or

2) Browsing to the file in nautlius and double click it

I can't seem to browse to the pc in nautilus, it's not there under network, just a folder that says windows network.


I thought this would be simple as they are both Ubuntu machines?

Thanks in advance for any help.

Please note, I would like a solution to either approach above and not a different solution. I've managed to ssh -X and have the server do the actual playing of the file, but this is not really what I'd want. I want the file to be streamed not the X-server data.

Thanks

Matt

---

### Post by papibe on 2012-07-23
I would use the ssh extensions on Nautilus:
```
File -> Connect to a server 
```
Use ssh, user and password and that's it. Once you make it work, save it in your bookmarks so it'd get one click away.

Regards.

---

