---
title: "TrueCrypt - how to &quot;Dismount&quot; even if device is in use ?"
date: 2009-07-10
forum: General Help
---

### Post by credobyte on 2009-07-10
I've an encrypted partition and it would be extremely nice if I could dismount it even if it's in use ( like Rythmbox is playing my mp3's, etc. ).
 Is it even possible ? When I hit "Dismount", I'm asked to enter my password and woala .. error pops out saying that I can't unmount "busy" device :(

Any tips/ideas on how to achieve this ( say "Unmount" without listening to my PC's arguments :D ) ?

---

### Post by michy99 on 2009-07-10
From the command line, try```
truecrypt --force --dismount=VOLUME
```Replace VOLUME with the volume name or leave off to dismount all volumes.

---

### Post by doas777 on 2009-07-10
that really isn't a good idea. you can really screw up your filesystem taht way.

in the windows version of truecrypt, you are prompted to force a dismount if the volume is in use. run 
```
truecrypt --help
``` to find the command line arguments possible (sorry, not at a lin terminal) and look to see if there is a -f for force that you can use with -d (dismount)

---

### Post by credobyte on 2009-07-10
> **michy99 said:**
> From the command line, try```
truecrypt --force --dismount=VOLUME
```Replace VOLUME with the volume name or leave off to dismount all volumes.

Something is wrong ..
> Unexpected characters following option 'dismount'.

> **doas777 said:**
> that really isn't a good idea. you can really screw up your filesystem taht way.

in the windows version of truecrypt, you are prompted to force a dismount if the volume is in use. run 
```
truecrypt --help
``` to find the command line arguments possible (sorry, not at a lin terminal) and look to see if there is a -f for force that you can use with -d (dismount)

Good or bad, but what's the point of using TrueCrypt ? To protect my files, right ? So, in case if I need to close my streams in the matter of seconds, "damage" would be the last thing to mention ;)

---

### Post by regala on 2009-07-10
> **credobyte said:**
> I've an encrypted partition and it would be extremely nice if I could dismount it even if it's in use ( like Rythmbox is playing my mp3's, etc. ).
 Is it even possible ? When I hit "Dismount", I'm asked to enter my password and woala .. error pops out saying that I can't unmount "busy" device :(

Any tips/ideas on how to achieve this ( say "Unmount" without listening to my PC's arguments :D ) ?

my 2 eurocents: it would be far better to try and stop whatever keeps it busy. anyway, it won't be really unmounted if you force-umount it.

try fuser -m /any/directory/on/mounted/dir, it should give you whatever processes could still have it busy. then you can kill it the soft way (-TERM) or the hard way (-KILL).

oh, and I am not sure I understood clearly: rhythmbox is still playing music from it and you want to unmount it anyway ? ;)

---

### Post by credobyte on 2009-07-10
> **regala said:**
> 
oh, and I am not sure I understood clearly: rhythmbox is still playing music from it and you want to unmount it anyway ? ;)

This should give you an overview of what I want to achieve :D

```
Q: Go away!
A: No, I'm working ..
```
to something like .. 
```
Q: Go away!
A: No, I'm wor (kill) .. aah .. (gone)
```

---

### Post by doas777 on 2009-07-10
well, the reason that it doesn't want to dismount is a good one. it is likely not the mount point that you are going to kill, but your file system. truecrypt can't protect your files, if you destroy them.

---

### Post by michy99 on 2009-07-10
Did you try the force dismount without specifying a volume?```
truecrypt --force --dismount
```

---

### Post by credobyte on 2009-07-10
> **doas777 said:**
> well, the reason that it doesn't want to dismount is a good one. it is likely not the mount point that you are going to kill, but your file system. truecrypt can't protect your files, if you destroy them.
Did I forgot to mention that it's an extended partition ( only documents and similar stuff ) ? Destroy 2 files, save 2k - for me, reasonable ;)

> **michy99 said:**
> Did you try the force dismount without specifying a volume?```
truecrypt --force --dismount
```
Excellent ! Thanks a lot :)

---

### Post by regala on 2009-07-16
> **credobyte said:**
> Did I forgot to mention that it's an extended partition ( only documents and similar stuff ) ? Destroy 2 files, save 2k - for me, reasonable ;)


a filesystem code doesn't speak "documents and similar stuff". it speaks filesystem integrity for one thing, and, as every other code in kernel space, keeping a running system stable. if you really want to remove it, remove it physically by hand, but don't expect the kernel to do destructive things or even enabling you to do it thru its code :)

---

### Post by credobyte on 2009-07-16
> **regala said:**
> a filesystem code doesn't speak "documents and similar stuff". it speaks filesystem integrity for one thing, and, as every other code in kernel space, keeping a running system stable. if you really want to remove it, remove it physically by hand, but don't expect the kernel to do destructive things or even enabling you to do it thru its code :)

Oh, yeah .. physically removing my HDD would take at least 10 minutes ( instead of 10-30 seconds from my Terminal window ) :D
Anyway, thanks a lot to everyone - problem solved !

---

### Post by Abdus on 2011-05-19
> **credobyte said:**
> Oh, yeah .. physically removing my HDD would take at least 10 minutes ( instead of 10-30 seconds from my Terminal window ) :D
Anyway, thanks a lot to everyone - problem solved !

„Problem solved!”, yet no solution named. :-({|=

Similar problem: can't unmount a darn volume, even though there is no way something really uses it.

fuser -m /home/abd/abd
outputs:
/home/abd/abd:       23468c
And 23058 is just the xterm I use to input fuser command, which is confirmed by lsof:
abd@ubayd:~$ lsof /home/abd/abd/
COMMAND     PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
konsole   23468  abd  cwd    DIR  251,2     4096    2 /home/abd/abd

This drives me mad. I want this unmounted, and readily unmounted any time I need it unmounted in the future, ANY time. How can I achieve that, if even --force doesn't work?

---

### Post by Abdus on 2011-05-26
> **Abdus said:**
> Similar problem: can't unmount a darn volume, even though there is no way something really uses it.

fuser -m /home/abd/abd
outputs:
/home/abd/abd:       23468c
And 23058 is just the xterm I use to input fuser command, which is confirmed by lsof:
abd@ubayd:~$ lsof /home/abd/abd/
COMMAND     PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
konsole   23468  abd  cwd    DIR  251,2     4096    2 /home/abd/abd

This drives me mad. I want this unmounted, and readily unmounted any time I need it unmounted in the future, ANY time. How can I achieve that, if even --force doesn't work?

In my case the problem was caused by KDE, which locked the directory the truecrypt volume was mounted into (/home/ab/abd/), because the directory was set in KDE settings as "Documents folder". As soon as I changed the Document folder to somewhere else the truecrypt volume could be unmounted.

---

