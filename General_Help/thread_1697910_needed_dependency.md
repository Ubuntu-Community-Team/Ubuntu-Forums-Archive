---
title: "needed dependency"
date: 2011-03-01
forum: General Help
---

### Post by somerefriedbeans on 2011-03-01
I am needing libavutil.so.50 in order to run a blender build from graphicall.org

After googling for over an hour, I am lost as to what I should do. Can anyone help, please?

Thanks in advance.

---

### Post by seawolf167 on 2011-03-01
Does the package

```
sudo apt-get install libavutil-dev
```

solve your dependency issue?

---

### Post by somerefriedbeans on 2011-03-01
Sorry, I forgot to mention that I'm on Ubuntu 9.10 and the libavutil that is in the repositories is libavutil.so.49

---

### Post by seawolf167 on 2011-03-01
You can get libavutil50 from [here]("http://packages.debian.org/sid/libavutil50"), [here]("http://fr2.rpmfind.net/linux/rpm2html/search.php?query=libavutil.so.50"), or see if the second from bottom post [here]("http://linux.justinhartman.com/Talk:FFmpeg,_FFmpeg-PHP,_Lame,_Libogg,_Libvorbis,_FLVtool2,_Mplayer,_Mencoder,_AMR_Installation#ffmpeg:_error_while_loading_shared_libraries:_libavutil.so.50") helps you at all.

---

