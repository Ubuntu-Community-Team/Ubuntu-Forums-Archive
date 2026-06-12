---
title: "Help!"
date: 2006-05-09
forum: General Help
---

### Post by sinkxdie on 2006-05-09
Don't tell me this is in the wrong place, because it works for Gnome too.;) 

I used to have a Windows so most of my songs are in .wma format.
 I havn't really played that much music since I got linux, but it's not getting annoying.
 
 I've searched and looked over these forums and on google for ways to edit my taglib(or libtag), or whatever its called, to be able to display .wma files in my AmaroK library.
 Almost all of these links are un-working or are just outdated. I can only find ones for Gentoo Linux, FreeBSD, and a .rpm. Also, when I open these up it just opens up in Kate, my text editor, and when I try and save it into a script or something, it just doesn't work. I found one that was a tar.bz2 or whatever that file format is, , but it was outdated and didn't download.
 
 All help appreciated...

---

### Post by Ramses de Norre on 2006-05-09
Why not just convert them to mp3 or ogg?
audio-convert is a nice little script for that and in the repos.

---

### Post by sinkxdie on 2006-05-09
1. Theres like 200
2. Limited disk space

---

### Post by IYY on 2006-05-09
Unless they are protected with DRM,

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Najand on 2006-05-09
Xine and MPlayer can play .wma files in Linux. Also there is a wma plugin for xmms. See if you can use any of them.

---

### Post by sinkxdie on 2006-05-09
Its not protected with DRM or anything like that, I have w32 codecs installed, and  amaroK can play the .wma files, but every time I want to I have to browse to the other partition and select a file to play. 
What I want to do is like this, [http://www.cs.berkeley.edu/~ushankar/taglib-wma/#mozTocId883978](http://www.cs.berkeley.edu/~ushankar/taglib-wma/#mozTocId883978)

But I can't figure out how to..
Can anyone help me with getting my taglib patched using that site, or just another way to **view**, well, also play, .wma files in amaroK

---

### Post by 47th_Ronin on 2006-05-10
[QUOTE=sinkxdie]1. Theres like 200
2. Limited disk space[/QUOTE]

](*,) come on... do 10 at the time.. when finished you remove .wma and start the next 10
200 is nothing... I want to convert my collection to .ogg but I don't have the space and the time... (21.000 mp3's, 1900 albums)

---

### Post by sinkxdie on 2006-05-10
I'd convert them all, but I cant delete the older ones because its all on a NTFS partition.

---

### Post by nanotube on 2006-05-11
[QUOTE=sinkxdie]I'd convert them all, but I cant delete the older ones because its all on a NTFS partition.[/QUOTE]
well, you can delete them later when you boot into windows (for the last time :) ).

---

### Post by sinkxdie on 2006-05-11
Haha, that sounds easy...but the reason I can't do that is because I started using linux for one reason,
I deleted my Windows XP Media Center Edition 2005 kernel32.dll and my gdi32.dll files in my c:\windows\system32 directory when I got pissed. :D

If you can't figure what that means, I broke my installation. Oh yeah, I don't have a Windows Xp Media Center Edition 2005 disk, I have a Windows XP Home disk, which screwed up my Windows even more. And that is why you shouldn't be allowed access to system files on Windows. Too easy to murder.

---

### Post by nanotube on 2006-05-11
hehe well...
in that case, convert some, burn off to a cd, delete some, convert, burn off to a cd, etc, until you are done
and then you can just wipe your entire win partition. :)

---

### Post by sinkxdie on 2006-05-11
yeah I guess that sounds reasonable, exept use my usb card to transfer it all to a 13 gb HD i have on my "testing" computer
but also, would converting all my music to OGG be reasonable for an iPod mini?
is it smaller/bigger files for better/worse quality?

---

### Post by sinkxdie on 2006-05-11
I figured that converting my files would just take too long, so I want to get back to this topic:
[http://www.cs.berkeley.edu/~ushankar/taglib-wma/taglib-wmapatched-1.4.tar.gz](http://www.cs.berkeley.edu/~ushankar/taglib-wma/taglib-wmapatched-1.4.tar.gz)
I downloaded that, extracted it, ran complie and it complied, but then when I try and do make or make install it doesn't work

---

### Post by nanotube on 2006-05-11
make Is compiling. so... what exactly did you do, and what exact error does make give you? :)

---

