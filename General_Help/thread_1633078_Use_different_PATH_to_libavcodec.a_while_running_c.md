---
title: "Use different PATH to libavcodec.a while running compile"
date: 2010-11-28
forum: General Help
---

### Post by excetara2 on 2010-11-28
I'm running the alsa upgrade script and I have ffmpeg installed so it finds the /usr/local/lib/libavcodec.a first when I want it to use the /usr/lib/libavcodec.so instead because otherwise make errors occur.

Can I point it to use the PATH to /usr/lib/libavcodec.a or should I just uninstall ffmpeg temporarily.

---

### Post by andrew.46 on 2010-11-28
Hi excetara2,

Perhaps try adding in a '*export PKG_CONFIG_PATH=/usr/lib/pkgconfig*' variable?

Andrew

---

### Post by excetara2 on 2010-11-28
Add this into the script file or before running the script. I assume it tells it to look for packages in the /usr/lib first??

Thanks

---

### Post by andrew.46 on 2010-11-29
Hi excetara2,

Hmmm..... I think you are referring to the alsa upgrade script [available on these forums]("http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001")? I am not so sure if this approach will work with that particular script but it might be worth a try to alter the script as follows:
```

PACKAGE=1.0.23

[B][COLOR="Red"]# Make the script look for libav* in /usr/lib first:
PKG_CONFIG_PATH=/usr/lib/pkgconfig
export PKG_CONFIG_PATH[/COLOR][/B]

setpack () {
DRIVER=alsa-driver-1.0.23
```

But looks like soundcheck is pretty active in the thread devoted to his script and he may be able to offer better advice that fits the script a little better if this does not work...

Andrew

---

### Post by excetara2 on 2010-11-29
Went down a different route to get it working on the alsa script and so far so good. If I have to do it again, I'll post if that works.

Cheers for the help because that's good to know either way when compiling.

---

### Post by excetara2 on 2010-12-01
Hey, gave it a go and that worked fine so cheers on that.

---

