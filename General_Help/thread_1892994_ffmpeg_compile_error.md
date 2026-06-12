---
title: "ffmpeg compile error"
date: 2011-12-09
forum: General Help
---

### Post by bootstrap58 on 2011-12-09
hello.
iwant to build ffmpeg with frei0r plugin on **windows**. 

i've downloaded  frei0r 1.3 from [http://www.piksel.no/frei0r/releases/](http://www.piksel.no/frei0r/releases/)

and copied **frei0r.h file to ffmpeg/libavfilters** directory

im using this command for compile.



```

cd c:\ffmpeg
./configure --enable-frei0r 
```but that gives error

```
ERROR: frei0r.h header not found.
```what can i do. thats very important for me.

---

### Post by bootstrap58 on 2011-12-09
Bump

---

### Post by WorMzy on 2011-12-09
Have you installed **frei0r-plugins-dev**?

> cd c:\ffmpeg

The hell? o.O

---

### Post by bootstrap58 on 2011-12-09
> **WorMzy said:**
> Have you installed **frei0r-plugins-dev**?



The hell? o.O


hello. how can i install it on windows? I want to compile ffmpeg on windows

---

### Post by WorMzy on 2011-12-09
I think you may be lost, this isn't a Windows help forum. I suggest you ask on the ffmpeg forums, or a Windows help forum.

> **General Help**
All your general support questions for **Ubuntu, Kubuntu, Edubuntu, Xubuntu and Lubuntu**.

---

### Post by FakeOutdoorsman on 2011-12-10
As I mentioned in another thread, you should ask at the [Zeranoe FFmpeg Forum](http://ffmpeg.zeranoe.com/forum/) why the Zeranoe FFmpeg Build for Windows does not work with frei0r although *--enable-frei0r* is shown in the FFmpeg ./configure.

Failing that, you can ask how to get frei0r working with FFmpeg on the ffmpeg-user mailing list if you haven't already.

<troll>Another option is to use Linux to do this. Frei0r in FFmpeg works fine for me.</troll>

---

### Post by bootstrap58 on 2011-12-10
> **FakeOutdoorsman said:**
> As I mentioned in another thread, you should ask at the [Zeranoe FFmpeg Forum]("http://ffmpeg.zeranoe.com/forum/") why the Zeranoe FFmpeg Build for Windows does not work with frei0r although *--enable-frei0r* is shown in the FFmpeg ./configure.

Failing that, you can ask how to get frei0r working with FFmpeg on the ffmpeg-user mailing list if you haven't already.

<troll>Another option is to use Linux to do this. Frei0r in FFmpeg works fine for me.</troll>

i need ffmpeg.exe with frei0r plugin. can i compile ffmpeg as an EXE file in linux?

---

### Post by Elfy on 2011-12-10
This is a linux forum - please take your windows issues to a windows forum.

---

