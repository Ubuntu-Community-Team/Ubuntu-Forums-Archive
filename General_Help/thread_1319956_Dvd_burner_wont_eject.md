---
title: "Dvd burner wont eject"
date: 2009-11-08
forum: General Help
---

### Post by psidrum on 2009-11-08
i upgraded to 9.10, then used Brasero to burn an iso, it worked, but then after that, the dvd does not open or eject anymore, 

it ejects when booting up, but once i have the OS running, i cant do anything with it,

how do i mount the dvd?

---

### Post by munky99999 on 2009-11-08
try

sudo umount /media/cdrom0/ -l
That should give the cd back.

This should make the cd player available again.
sudo mount /media/cdrom0/

---

### Post by psidrum on 2009-11-08
i tried the commands it work then i got this error

```
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by stinger30au on 2009-11-08
since i upgraded to 9.10 i get strange things like this with the cd/dvd

i have noticed when i install a dvd it wont auto mount

but i have noticed if i click on 

places

the dvd is there so i click on it to mount

sometimes too it wont eject and i fireup shell and type

eject cdrom

and the disc comes out

other times i have to log off and log back on again to get the drive to work

theres nuffing wrong with the dvd drive. i have put 9.10 on to 4 pc's and they all do the same thing

just some weird new bug

---

### Post by munky99999 on 2009-11-08
arg. Personally I havent used cds/dvds in so long. I would never even notice this bug.

I ejected my cd drive and it absolutely refused to go back in.

Started to debug the situation with looking why the problem was happening. Got angry because everything appeared to be working just fine. Slammed it back in. Now it's working fine. Cant get any problems from it.

I dont suggest doing that though heh.

---

