---
title: "Encoding independent file manager"
date: 2012-09-24
forum: General Help
---

### Post by eskimo on 2012-09-24
Hello,
i'm using linux since years, but now i don't want to waste time with the same problems...i've got a encoding issue, but not the usual visualization problem.
I'm tying to copy files from my old home partition, since i have to install a fresh distro. The old one is compromised so i'm using a live distribution to save my data.
While i'm copying multimedia files, the ones that normally have strange characters (i'm italian), i receive an error because file manager i'm using says it found a not recognized char.
How can i copy old files without have to remove manually all strange chars?? (normally accent char...) nautilus in live ubuntu distro seems to be suddenly not independente from encoding as usual, when it was capable...
how can i do??
thanks...
Paolo

---

### Post by shreepads on 2012-09-24
How about using command line

```

$ cp /source/path/* /destination/path

```

---

### Post by Vaphell on 2012-09-24
somewhat strange. I think that encoding related errors come from filesystem. That could be a problem if your system and live session used incompatible encodings. That should not happen though, as i think utf8 is default. Usually that problem occurs when people transfer files between windows region specific encodings and utf8.
you can try using convmv tool, translating filenames between encodings, though i think you need to explicitly supply them (requires you to know them)

```
convmv -f <encoding_from> -t <encoding_to> <files>
```
usually encoding_to is utf8

I think you should be able to install it during live session.
Another option would be to leave old home partition in place and reuse it as either /home or some system independent /data and do the cleanup work after reinstallation.

---

### Post by eskimo on 2012-09-24
Thanks...

@shreepads: i hoped a shell could be an help...unfortunely i tried to copy by hands but no way.

I'll try to convert between encodings. My original filesystem is UTF_8 encoded, and seems that my liveubuntu start with iso8859-15.
I like your last solution: leave all files there...but i'll change partition scheme and i risk to loose my data...
P.

---

### Post by diesch on 2012-09-24
> **eskimo said:**
> 
I'll try to convert between encodings. My original filesystem is UTF_8 encoded, and seems that my liveubuntu start with iso8859-15.


Linux file systems don't know anything about file name encoding. They just use bytes and let the software care about encoding and such. Hence it is possible that you have file names with different encodings.

The live CD uses UTF-8 as default encoding, just like an installed system. The files with a different file name encoding may be ones you copied from Windows on the command line or downloaded from somewhere.

---

### Post by eskimo on 2012-09-24
Yes, diesch, thanks for your precision. For sure, they're downloaded so came from another system.
I think convmv could be a good solution. 
Which encoding do you think i have to use for my future installations? Keep UTF8 but remember to convert all downloaded files?
thanks

---

