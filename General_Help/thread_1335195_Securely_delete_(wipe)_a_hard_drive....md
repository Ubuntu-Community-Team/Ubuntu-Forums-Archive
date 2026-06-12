---
title: "Securely delete (wipe) a hard drive..."
date: 2009-11-23
forum: General Help
---

### Post by Crumbles on 2009-11-23
So, I have a 20 gig hard drive I am trying to wipe securely before I toss it.  I was doing it this way:

sudo dd if=/dev/urandom of=/dev/sdc bs=1024

I want it to wipe anything under sdc (sdc1, sdc2, etc)

So, the guys in the ubuntu chat told me to use wipe instead.  however, everything I try isn't working.  I tried this:

sudo wipe -fq -l 1024K /dev/sdc

and it INSTANTLY finished and said:
Operation finished.                                                           
1 file wiped and 0 special files ignored in 0 directories, 0 symlinks removed but not followed, 0 errors occured.

So... that obviously failed... then I tried:

sudo wipe /dev/sdc
/dev/sdc: fatal: could not lstat: No such file or directory

So... now I'm back to using dd .... is the dd command I'm doing above worse than if I were to use wipe? Also, how the heck do I use wipe???

Thanks in advance...

---

### Post by Cheesemill on 2009-11-23
The dd command you were using is fine, in fact you don't even need to use /dev/urandom.
Just one pass of 0's is enough to securely wipe everything on the drive.

Check out the manual page for wipe if you want to know how to use it:
```
man wipe
```

---

### Post by coffeecat on 2009-11-23
Or have a look at shred from the terminal. You can change the number of overwrites from the default of three. (It used to be 25! :shock: :wink: ). If you just want to overwrite with zeros, the syntax would be:

```
sudo shred -zn 0 /dev/whatever
```

You can shred just a partition or a whole drive.

---

### Post by Crumbles on 2009-11-24
> **coffeecat said:**
> Or have a look at shred from the terminal. You can change the number of overwrites from the default of three. (It used to be 25! :shock: :wink: ). If you just want to overwrite with zeros, the syntax would be:

```
sudo shred -zn 0 /dev/whatever
```You can shred just a partition or a whole drive.
Shred is pretty awesome.  I enjoy it a lot. Thanks for telling me about it!

---

