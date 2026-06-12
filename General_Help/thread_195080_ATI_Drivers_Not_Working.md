---
title: "ATI Drivers Not Working"
date: 2006-06-12
forum: General Help
---

### Post by rowanparker on 2006-06-12
Hello,
I attempted to install the ATI drivers using [this]("http://ubuntuforums.org/showthread.php?t=75378") tutorial. The installation went fine but when i rebooted i still could not play games.
```
rowan@hal:~$ fglrxinfo
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
(etc, etc)
```
That is the output of fglrxinfo and it goes on for another 50 odd lines.

```
rowan@hal:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)
```
That is the output of lspci | grep ATI.

How can I get it working or how can I play my games (Neverball mainly)?

Thanks, Rowan.

---

### Post by halfvolle melk on 2006-06-13
Hi,
check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=185033](http://www.ubuntuforums.org/showthread.php?t=185033)

It says to replace the currect /usr/liblibGL.so.1.2 with [this one](http://www.ground-impact.com/libGL.so.1.2).
ie.
```
sudo cp /whereever/youputit/libGL.so.1.2 /usr/lib/libGL.so.1.2
```
That should fix it.

---

### Post by nephesh on 2006-06-13
Personally I would suggest this thread.

[http://ubuntuforums.org/showthread.php?t=143283&highlight=ati+driver](http://ubuntuforums.org/showthread.php?t=143283&highlight=ati+driver)

---

### Post by rowanparker on 2006-06-14
Works great!

Thanks, Rowan.

---

### Post by rowanparker on 2006-07-18
Edit: Moved to a [new thread]("http://ubuntuforums.org/showthread.php?p=1283249").

---

