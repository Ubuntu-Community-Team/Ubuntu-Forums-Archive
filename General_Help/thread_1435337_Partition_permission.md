---
title: "Partition permission"
date: 2010-03-21
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2010-03-21
So... frustratingly I do this ```
Killmandline:$ ls -la /media/store
total 36
drwxr-xr-x 6 sin  sin   4096 2010-03-21 12:26 .
drwxr-xr-x 6 root root  4096 2010-03-21 10:48 ..
drwx------ 2 sin  sin  16384 2010-03-15 10:42 lost+found
drwxr-xr-x 3 sin  sin   4096 2010-03-21 12:26 Mine
drwx------ 4 sin  sin   4096 2010-03-16 08:23 .Trash-0
drwx------ 4 sin  sin   4096 2010-03-21 12:26 .Trash-1000
Killmandline:$ 
```

Then ```
Killmandline:$ ls -la /media/store/Mine/Nexuiz
total 27760
drwxr-x---  10 sin sin    4096 2009-12-10 04:00 .
drwxr-xr-x 111 sin sin    4096 2010-03-21 12:47 ..
drwxr-x---   2 sin sin    4096 2009-12-13 06:10 data
drwxr-x---   4 sin sin    4096 2009-10-01 02:08 Docs
drwxr-x---   4 sin sin    4096 2009-10-14 00:21 extra
-rwxrwxrw-   1 sin sin   18009 2009-10-01 01:53 gpl.txt
drwxr-x---   2 sin sin    4096 2009-10-14 00:21 havoc
-rwxrwxrw-   1 sin sin  266911 2009-10-01 02:34 libcurl-4.dll
-rwxrwxrw-   1 sin sin  114688 2009-10-01 02:34 libjpeg.dll
-rwxrwxrw-   1 sin sin  339968 2009-10-01 02:34 libmodplug-0.dll
-rwxrwxrw-   1 sin sin  222244 2009-10-01 02:34 libpng12.dll
-rwxrwxrw-   1 sin sin  720543 2009-10-01 02:34 libtheora.dll
drwxr-x---   3 sin sin    4096 2009-10-01 02:34 Nexuiz.app
-rwxrwxrw-   1 sin sin 2009088 2009-10-01 01:52 nexuiz-dedicated.exe
-rwxrwxrw-   1 sin sin 2087936 2009-10-01 01:52 nexuiz.exe
-rwxrwxrw-   1 sin sin    7500 2009-12-10 04:00 nexuiziconnf2.png
-rwxrwxrw-   1 sin sin 1961480 2009-10-01 01:38 nexuiz-linux-686-dedicated
-rwxrwxrw-   1 sin sin 2199088 2009-10-01 01:38 nexuiz-linux-686-glx
-rwxrwxrw-   1 sin sin 2191728 2009-10-01 01:38 nexuiz-linux-686-sdl
-rwxrwxrw-   1 sin sin    2104 2009-10-01 01:53 nexuiz-linux-glx.sh
-rwxrwxrw-   1 sin sin    2104 2009-10-01 01:53 nexuiz-linux-sdl.sh
-rwxrwxrw-   1 sin sin 2105480 2009-10-01 01:51 nexuiz-linux-x86_64-dedicated
-rwxrwxrw-   1 sin sin 2357664 2009-10-01 01:51 nexuiz-linux-x86_64-glx
-rwxrwxrw-   1 sin sin 2350368 2009-10-01 01:51 nexuiz-linux-x86_64-sdl
-rwxrwxrw-   1 sin sin 3939228 2009-10-01 01:35 nexuiz-osx-dedicated
drwxr-x---   3 sin sin    4096 2009-10-01 02:34 Nexuiz-SDL.app
-rwxrwxrw-   1 sin sin 2065920 2009-10-01 01:52 nexuiz-sdl.exe
-rwxrwxrw-   1 sin sin  441977 2009-10-01 02:34 ogg.dll
-rwxrwxrw-   1 sin sin   11323 2009-10-01 01:53 readme.html
-rwxrwxrw-   1 sin sin  321536 2009-10-01 02:34 SDL.dll
drwxr-x---   3 sin sin    4096 2009-10-01 01:59 server
drwxr-x---   2 sin sin    4096 2009-10-01 02:07 sources
-rwxrwxrw-   1 sin sin  568692 2009-10-01 02:34 vorbis.dll
-rwxrwxrw-   1 sin sin 1532974 2009-10-01 02:34 vorbisenc.dll
-rwxrwxrw-   1 sin sin  434851 2009-10-01 02:34 vorbisfile.dll
-rwxrwxrw-   1 sin sin   69120 2009-10-01 02:34 zlib1.dll
Killmandline:$ 
```

So all seems well to ```
Killmandline:$ /media/store/Mine/Nexuiz/nexuiz-linux-x86_64-glx
bash: /media/store/Mine/Nexuiz/nexuiz-linux-x86_64-glx: Permission denied
Killmandline:$ 

```

So... now I'm confused. /dev/sda6 is mounted at /media/store and it'
s just an ext4 backup partition. I can run the program if I move the whole folder to my home dir but I would rather keep it on the larger partition. Thanks in advance.

---

### Post by Sin@Sin-Sacrifice on 2010-03-21
Don't know if it's relative but now I can't export PATH= anymore either. It shows in echo $PATH but command line doesn't see the command. This install is being weird.

---

### Post by Sin@Sin-Sacrifice on 2010-03-21
I fixed by setting fstab to defaults... literally.```
UUID=34e343b7-ec4d-4b0a-a605-1c345f1d0a7f  /media/ext  ext4         defaults,noatime,errors=remount-ro 0 1
``` And there we have it.

---

