---
title: "music cd not browsable?!"
date: 2006-02-11
forum: General Help
---

### Post by edistar on 2006-02-11
Hey!
I wondered if one cannot see the .cda files on a musiccd!
I inserted the cd and sound juicer started to play :) Unfortunately my sound doesn't work yet, but that is not the problem of this thread ;)
I wanted to make an iso of that cd and did "dd if=/dev/cdrom of=cd.iso"...
It didn't work.... so I wanted to check the cdrom and did "cd /cdrom". That told me there was nothing on the cd :-k 
Of course there is something on it and it is mounted as sound juicer can play it!
What do I do to open the drive and make an iso?

Thanks,
Edistar

---

### Post by kaamos on 2006-02-11
nevermind, didn't work. pretty good question..

---

### Post by lha on 2006-02-11
You have to unmount cd before you can dd it to a file.
```
sudo umount /dev/hdc
``` if your cd-rom drive is secondary master. Then try that dd again.

---

### Post by edistar on 2006-02-11
Hey!
Thanks for the replies,
I tried to umount and it said that the cd wasn't even mounted! But then why can sound-juicer play it?!
It tells my on the desktop that it's a music cd... 
But if I do cd /cdrom I don't get anything....

Please help!

Btw., I can ripp the cd without problems with sound-juicer.... :)

---

### Post by xmastree on 2006-02-11
> I wanted to make an iso of that cd
See this thread:
[http://www.ubuntuforums.org/showthread.php?t=98116](http://www.ubuntuforums.org/showthread.php?t=98116)
There's info there about making an ISO from an audio CD.

---

