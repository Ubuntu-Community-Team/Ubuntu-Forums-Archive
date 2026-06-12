---
title: "Please help me grub rescue error"
date: 2011-11-28
forum: General Help
---

### Post by t3d4ks on 2011-11-28
First of all, I would like to thank you for the taking time to read my problem. I appreciate it.

Here is my situation:
I downloaded and (installed -because I'm not sure if it was completely installed) ubuntu 11.10 through wubi on my Windows 7 notebook.  Unfortunately, there was a power interruption last night. When I opened my laptop this morning, I had this grub rescue prompt.

I went through various topics for the last 6 hours hoping I could resolve this. 
To add to my demise, I don't have the win 7 cd with me right now since I'm out of town. I did downloaded ubuntu 11.10 iso though which I will transfer to external drive.

Btw, here's the result if I type "ls" on grub rescue:
grub rescue> ls
(hd0), (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
grub>set
prefix=(hd0,msdos5)
set=hd0,msdos5

Again, I greatly appreciate if someone could get me through with my problem. 

Cheers,
Ritchie

---

### Post by t3d4ks on 2011-11-28
and also if I input the command "ls (hd0,msdos3)" it gives me "error:unknown filesystem"

I'm not sure where I can find the right /boot partition.

---

### Post by Quackers on 2011-11-28
Sadly I know very little of wubi installations but it may be worthwhile looking here

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by t3d4ks on 2011-11-29
Quackers

Thanks for the link. I have already fixed it.

I downloaded Ubuntu USB and followed solution # 2.

---

