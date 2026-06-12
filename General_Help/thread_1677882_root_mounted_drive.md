---
title: "root mounted drive"
date: 2011-01-29
forum: General Help
---

### Post by brad3260 on 2011-01-29
Hello, instead of boring with why I did what I did, I'll get to the problem. I installed pysdm and it seems to have permanently mounted a drive under the root user. The following terminal should explain. I need to unmount the OS so I can have OS_ be named OS. Can someone help me please? 

brad@brad-laptop:~$ ls -l /media
total 20
drwx------ 1 brad brad 4096 2011-01-28 10:33 FreeAgent Drive
drwxr-xr-x 2 root root 4096 2011-01-28 23:22 OS
drwx------ 1 brad brad 8192 2011-01-28 16:34 OS_
drwxr-xr-x 2 root root 4096 2011-01-28 23:54 sdc1
brad@brad-laptop:~$ sudo umount -l /media/OS
umount: /media/OS: not mounted
brad@brad-laptop:~$ ls -l /media/OS
total 0
brad@brad-laptop:~$ ls -l /media/OS_
total 12824797

---

### Post by tredegar on 2011-01-29
> brad@brad-laptop:~$ ls -l /media/OS
total 0
So nothing is mounted at **/media/OS** so you can safely remove that mountpoint```
sudo rmdir /media/OS
```

---

### Post by brad3260 on 2011-01-29
Well that was embarrassingly easy, thank you! Now can you help with the reason I installed pysdm? I'm dual booting with vista and want to share profiles between the two in Firefox and Thunderbird. The profiles are on the vista partition and I have everything working but when I first get in Ubuntu, Firefox or Thunderbird can't access the profiles until I go Places->OS. Once I do this everything works and the OS drive is shown on my desktop. It's like Ubuntu sees that partition don't mount it until it needs to be accessed? Any idea on that?

---

### Post by tredegar on 2011-01-29
> It's like Ubuntu sees that partition don't mount it until it needs to be accessed? Any idea on that?
I don't use windows, but if you want the drive to be mounted, either clicky-clicky it when you login or put an entry for it in **/etc/fstab** so it will be mounted wherever you like at boot (so long as it is plugged in, that is).

---

### Post by brad3260 on 2011-01-29
Perfect! I was kind of nervous editing that file but it was easy. Thank you for the help today

---

