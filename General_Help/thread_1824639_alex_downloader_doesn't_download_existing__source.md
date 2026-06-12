---
title: "alex downloader doesn't download existing  source"
date: 2011-08-14
forum: General Help
---

### Post by rootnet47 on 2011-08-14
Hi! I installed alex by get-apt install alex, after that I tried to download a file

[http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.0.1.tar.bz2](http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.0.1.tar.bz2)
#axel [http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.0.1.tar.bz2](http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.0.1.tar.bz2)

when I hit the enter key to start the download I gives a message like bellow

root@ricky-Rev-1-0:/home/ricky# axel "http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.0.1.tar.bz2"
[http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.0.1.tar.bz2:](http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.0.1.tar.bz2:) filename must end in '.x'
root@ricky-Rev-1-0:/home/ricky#

could anyone help me to fix this problem?

---

### Post by raja.genupula on 2011-08-14
try wget man its better than all

---

### Post by rootnet47 on 2011-08-14
That was not a solution. Well check this out
[http://www.cyberciti.biz/tips/download-accelerator-for-linux-command-line-tools.html](http://www.cyberciti.biz/tips/download-accelerator-for-linux-command-line-tools.html)

---

### Post by Elfy on 2011-08-14
Never heard of alex - but the link you gave shows 

```
axel http://download.com/file.tar.gz
```

Why are you trying to use alex? 

Also it shows without " - you're command was 

```
alex "http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.0.1.tar.bz2"
```

What happens if you try

```
axel http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.0.1.tar.bz2
```

---

### Post by rootnet47 on 2011-08-14
In both, with upper quot without quot result is same.

---

### Post by Elfy on 2011-08-14
Other than not trying to do it as root it works fine here

```
axel http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.0.1.tar.bz2
Initializing download: http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.0.1.tar.bz2
File size: 76754139 bytes
Opening output file linux-3.0.1.tar.bz2
Starting download

[  0%]  .......... .......... .......... .......... ..........  [ 176.8KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 264.7KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 316.0KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 351.1KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 375.5KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 394.0KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 409.0KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 420.4KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 430.0KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 437.8KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 444.5KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 450.3KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 455.4KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 459.8KB/s]
[  0%]  .......... .......... .......... .......... ..........  [ 463.6KB/s]
[  1%]  .......... .......... .......... .......... ..........  [ 467.0KB/s]
[  1%]  .......... .......... .......... .......... ..........  [ 470.1KB/s]
[  1%]  .......... .......... .......... .......... ..........  [ 472.9KB/s]
[  1%]  .......... .......... .......... .......... ..........  [ 475.5KB/s]
[  1%]  .......... .......... .......... .......... ..........  [ 477.6KB/s]
[  1%]  .......... .......... .......... .......... ..........  [ 479.7KB/s]
[  1%]  .......... .......... .......... .......... ..........  [ 481.7KB/s]
[  1%]  .......... .......... .......... .......... .........^C

Downloaded 1149.8 kilobytes in 2 seconds. (483.30 KB/s)
```

---

