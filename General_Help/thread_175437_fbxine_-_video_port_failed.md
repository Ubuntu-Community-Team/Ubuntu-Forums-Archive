---
title: "fbxine - video port failed"
date: 2006-05-13
forum: General Help
---

### Post by Biffy on 2006-05-13
When i was using Suse i usually would play videos in the fb-console. When trying to do this in Ubuntu, i get the error message "Video port failed" . I can play the same video with mplayer.

```
fbxine -V vidixfb video.avi
Video port failed
```

It does not matter wich video driver i choose. I've been trying as normal user and as root, no difference.

```
larsson@ubuntu:/media/hd2 $ fbxine --help
Usage: fbxine [options] <MRL> ...

  -v, --version                  Display version.
      --verbose [=level]         Set verbosity level. Default is 1.
  -V, --video-driver <drv>       Select video driver:
```

I have a Radeon 9600XT graphics card.

---

### Post by Biffy on 2006-05-13
I saw that there is another xine fb application called aaxine. Tried with that one and it does not work either, but it gives me some error messages:

```
error occured during PCI scan: Operation not permitted
```

and

```
libdha: Can't open /dev/dhahelper
```

Hope this helps.

This is when trying the vidixfb driver. The only driver that actually works with aaxine is the ASCI one.

---

### Post by Biffy on 2006-05-15
No one using fbxine/aaxine here? Need help!

---

### Post by Biffy on 2006-05-24
Somone must know why fbxine wont work in Ubuntu..

---

