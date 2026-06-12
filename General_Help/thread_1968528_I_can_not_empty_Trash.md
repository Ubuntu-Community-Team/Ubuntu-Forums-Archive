---
title: "I can not empty Trash"
date: 2012-04-29
forum: General Help
---

### Post by gurrunaki on 2012-04-29
Hi, I&#7743; running ubuntu 11.10 I tried delete trash folder because are inside some audio files and some videos too taken much place and I don need them anymore, I found this command
**rm****-rf**[B]~/.local/share/Trash/

[/B]but nothing happen when use that, neither when I try do manually, any idea?

Thanks in advance

---

### Post by celem on 2012-04-29
Log out and back in again.

---

### Post by wojox on 2012-04-29
You may need spaces in that command:
```
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
```

---

### Post by gurrunaki on 2012-04-29
Thanks for your fast reply, I did what both of you said, log out and try the command and gave me the next error

---

### Post by gurrunaki on 2012-04-29
Is working, I don know how but now Trash is empty. I logged out again and appear empty :p

Thanks a lot!!!

---

