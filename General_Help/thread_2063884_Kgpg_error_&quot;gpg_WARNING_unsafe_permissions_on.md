---
title: "Kgpg error &quot;gpg: WARNING: unsafe permissions on configuration file&quot;"
date: 2012-09-28
forum: General Help
---

### Post by losfalcor on 2012-09-28
Hi all.  Let me start by saying, since i found Ubuntu Studio i think i like it better than windows..

Anyways, trying to get all my essentials in.  I found  a program called Kgpg in the studio market as well as kleopatra.  I managed to install my old keys and unencrypt an email from a few weeks back ive been waiting to unencrypt.  It seemed the program worked the first start, but after reseting my computer and attempting to reload Kgpg again i get the following error

" GnuPG failed to start.
You must fix the GnuPG error first before running KGpg.


 gpg: WARNING: unsafe permissions on configuration file `/home/falcor/.gnupg/gpg.conf'
 gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/falcor/.gnupg/gpg.conf'"


my computers name is Falcor..


Please how to fix?  Only other option i can think of is to run windows in a virtual box so i can use the winpt i used to use, but rather not do this.  Any advise would be appreciated.  Thanks

---

### Post by Habitual on 2012-09-29
terminal> 
```
chmod 600 .gnupg -R
```

---

### Post by losfalcor on 2012-09-29
Thanks for the reply.  When i type that into the terminal i get

"
chmod: cannot access `.gnupg/pubring.gpg~': Permission denied
chmod: cannot access `.gnupg/Fal.revoke': Permission denied
chmod: cannot access `.gnupg/random_seed': Permission denied
chmod: cannot access `.gnupg/pubring.kbx': Permission denied
chmod: cannot access `.gnupg/private-keys-v1.d': Permission denied
chmod: cannot access `.gnupg/trustdb.gpg': Permission denied
chmod: cannot access `.gnupg/pubring.gpg': Permission denied
chmod: cannot access `.gnupg/gpg.conf': Permission denied
chmod: cannot access `.gnupg/pubring.kbx~': Permission denied
chmod: cannot access `.gnupg/secring.gpg': Permission denied

"


i dont understand.  Everything worked fine the first time. Current;y im using kleopatra
and i have set up winpt in windows 7 in a virtualbox, but is very inconvenient

---

### Post by Habitual on 2012-09-30
terminal > 
```
ls -ld .gnupg
```

output please.

---

### Post by losfalcor on 2012-10-01
i typed in the terminal  " sudo kernel.shmmax = 128000000 " to fix a problem with avast, now the only error i get with kgpg is 

 " gpg: option file `/home/falcor/.gnupg/gpg.conf': Permission denied "



> **Habitual said:**
> terminal > 
```
ls -ld .gnupg
```output please.

I get this


drw------- 3 falcor falcor 4096 Sep 29 07:08 .gnupg

---

### Post by Habitual on 2012-10-01
Well, that says you own the directory, now let's look inside it with:
```
ls -al .gnupg
```output please.

---

### Post by losfalcor on 2012-10-02
i get the following 

"
ls: cannot access .gnupg/pubring.gpg~: Permission denied
ls: cannot access .gnupg/Fal.revoke: Permission denied
ls: cannot access .gnupg/random_seed: Permission denied
ls: cannot access .gnupg/.: Permission denied
ls: cannot access .gnupg/pubring.kbx: Permission denied
ls: cannot access .gnupg/private-keys-v1.d: Permission denied
ls: cannot access .gnupg/trustdb.gpg: Permission denied
ls: cannot access .gnupg/..: Permission denied
ls: cannot access .gnupg/pubring.gpg: Permission denied
ls: cannot access .gnupg/gpg.conf: Permission denied
ls: cannot access .gnupg/pubring.kbx~: Permission denied
ls: cannot access .gnupg/secring.gpg: Permission denied
total 0
d????????? ? ? ? ?            ? .
d????????? ? ? ? ?            ? ..
-????????? ? ? ? ?            ? Fal.revoke
-????????? ? ? ? ?            ? gpg.conf
d????????? ? ? ? ?            ? private-keys-v1.d
-????????? ? ? ? ?            ? pubring.gpg
-????????? ? ? ? ?            ? pubring.gpg~
-????????? ? ? ? ?            ? pubring.kbx
-????????? ? ? ? ?            ? pubring.kbx~
-????????? ? ? ? ?            ? random_seed
-????????? ? ? ? ?            ? secring.gpg
-????????? ? ? ? ?            ? trustdb.gpg
"

---

### Post by Habitual on 2012-10-02
try terminal >
```
sudo chown falcor:falcor /home/falcor/.gnupg/* -R
```You have a backup of that directory?

Also please use code tags for command/script output (as attached). 

Thanks!

---

### Post by losfalcor on 2012-10-03
I dont think i have a backup of that directory.   I typed in the terminal the code you specified and still reading '   p, li { white-space: pre-wrap; }  gpg: option file `/home/falcor/.gnupg/gpg.conf': Permission denied'

---

### Post by Habitual on 2012-10-03
You may have lost it and the keys it contained, but you could try to force a fsck with ```
shutdown -rF now
```at the next opportunity to reboot.

---

