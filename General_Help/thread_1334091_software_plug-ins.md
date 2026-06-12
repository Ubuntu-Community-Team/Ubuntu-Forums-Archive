---
title: "software plug-ins"
date: 2009-11-22
forum: General Help
---

### Post by catinhat on 2009-11-22
I just downloaded Kino on it's requirements page it requires these plug-ins     *   libglade2
    * gtk 2.6 (and related dependencies)
    * libxml2
    * libdv
    * libsamplerate
    * libasound
    * libXv
    * libpthread
    * ffmpeg, libavformat, and libavcodec
    * libraw1394
    * libiec61883
    * libavc1394
    * ffmpeg2theora
    * sox
    * vorbis-tools
    * lame
    * mjpegtools
    * dvdauthor
    * 'Q' dvdauthor
    * growisofs
    * mencoder
and I was wondering how many of these already in ubuntu9.10

---

### Post by camaron1 on 2009-11-22
Why don't you use Synaptic? all dependencies will be taken care of

---

### Post by catinhat on 2009-11-22
I have dial-up so I had to download through Windows.

---

### Post by camaron1 on 2009-11-22
> **catinhat said:**
> I have dial-up so I had to download through Windows.
I see, 

Kino is in the repositories, when i tell synaptic to install doesn't ask for any other dependencie, which means all it needs is already installed. Now, having a look at your list many of them are codecs or media libraries that **don't** come pre-installed in ubuntu, you'll need to install them too. I think this is what you are asking?

Is it a deb package or the source package you got hold of?

---

### Post by catinhat on 2009-11-22
source package but I just found a deb package I plan to download

---

### Post by SPr on 2009-11-22
Slightly OT but try setting up the modem for Ubuntu [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by catinhat on 2009-11-22
I guess it wasn't a deb package I found

---

### Post by camaron1 on 2009-11-22
Unless you find a deb package somewhere I don't think you can install that with any use, i'm afraid

---

### Post by 3rdalbum on 2009-11-22
If you want to compile something from source, then you need the "-dev" packages for each dependency.

So you need:

libglade2-dev
libxml2-dev
libdv-dev
libsamplerate-dev

etc.

---

