---
title: "Write tar errors to a file?"
date: 2010-03-10
forum: General Help
---

### Post by Drenon88 on 2010-03-10
Greetings,

I want to backup my Ubuntu box and I found a couple very helpful articles that describe how to use tar for backup and restore. So far so good. I've dabbled in Lin/Unix in the past, mainly on work systems, but Linux on my personal PC is new to me.

When I ran the tar command as root (su -) I noticed several errors scrolling by in the window. It's scrolling too fast to note the exact errors, but I did notice "permission denied" a few times.

Is there some way that I can capture the output of the tar command to a file so I can review it for errors and/or permission denied statements?

Can I just add some arguments to tar?


tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

---

### Post by Kevbert on 2010-03-10
The normal way to send the output to a file is by using a pipe, so you could try
```
command > output.txt
```
where command is what you want to run and output.txt is all messages saved in a current directory file called output.txt.

---

### Post by geirha on 2010-03-10
Error and warning messages are written to stderr (fd 2) though, so to also redirect those to the same file, you need
```
command > output.txt 2>&1
```

---

