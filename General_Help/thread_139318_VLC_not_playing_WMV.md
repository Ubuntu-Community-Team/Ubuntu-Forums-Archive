---
title: "VLC not playing WMV"
date: 2006-03-03
forum: General Help
---

### Post by ryan76 on 2006-03-03
I'm on AMD64 with a 32-bit chroot. I have installed VLC in the chroot and the w32codecs, but .wmv files still aren't playing. There is sound but no video.

The output of the terminal is this:

```
ryan@ubuntu:~$ dchroot -d
Executing shell in 'breezy' chroot.
ryan@ubuntu:~$ vlc
VLC media player 0.8.4-svn20040920 Janus
[00000302] main decoder error: no suitable decoder module for fourcc `WMV3'.
VLC probably does not support this sound or video format.
```

Can anyone help please? I'm so close...

---

### Post by Mez on 2006-03-03
You want the w32codecs package, which can be found in the plf repo

[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

---

### Post by ryan76 on 2006-03-04
I have installed that already, thanks

---

### Post by Toxicity999 on 2006-03-04
From what I know you need to compile it with that support... theres a guide around.
Read this [Topic]("http://ubuntuforums.org/showthread.php?t=61608") incase you have any issues with it and follow the first posts link to a tutorial. I haven't tried it but seemingly it's good. Might want to search the forums for Compiling VLC for anyting else you may want.

(Also, I just ran to this from memory. Is this even what you were looking for? I've never been after it but I assume it's the same thing.)

---

### Post by ryan76 on 2006-03-04
Thanks, I'll try that. :)

---

