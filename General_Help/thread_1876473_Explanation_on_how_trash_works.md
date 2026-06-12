---
title: "Explanation on how trash works"
date: 2011-11-06
forum: General Help
---

### Post by tanoloco on 2011-11-06
Hello,

recently I needed to use a temporary file and according to a thread I found online I tried to use /dev/shm instead of /tmp as a a place in which store my temporary files.

Once used them I decided to delete them, but instead of just remove them with rm, I wished to trash them just to edit them in case of debugging issues.

To do that I simply installed trash-cli and used```
trash 'foo'
``` to put my files into the bin.

I was surprised in noticing at this point that my 'foo' temporary file wasn't put in my trash bin at
> ~/.local/share/Trash/files/
but actually stored under a new opened hidden folder at the same level of /dev/shm at
> /dev/shm/.Trash-1001/files
where 1001 is my current userID.

So I tried to use the gui and tried to create and trash a file 
using pcmanfm both on /tmp and /dev/shm and noticed that the gui has the same behavior of the trash command (as expected).
That means that the /tmp/foo was put on the trash bin while the /dev/shm/foo was put on this hidden folder.

I tried to understand why, and noticed the /dev/shm is actually symbolic link of /run/shm and tried to create and delete a file on that path to be sure using pcmanfm and it was always put on the same hidden folder.

So, I solved my "problem" using /tmp folder rather than /dev/shm but just to understand better: why this behavior?
I would expect to trash a file from /dev/shm or wherever and find it under my trash bin!

Am I wrong?

I noticed that when I plug a usb drive it stores the trashed staff under> /media/<mounting-point>/.Trash-1001/files/ and I can understand this, but really can't understand the behavior described above.

Is there anyone there who can explain it to me easily?

I'm using lubuntu 11.10 and my user is not root of course but is a sudoers, but I don't use sudo whem trashing the files as shown by the fact that it creates a .Trash-1001 hidden folder.

Thanks for any explanation
Cheers

---

### Post by clrg on 2011-11-06
The trash bin from one filesystem cannot be in another filesystem, since that another filesystem could not be available when the user tries to restore something.

```

rechenknecht:<~> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             115G   52G   58G  48% /
none                  1.9G  368K  1.9G   1% /dev
none                  1.9G  2.1M  1.9G   1% /dev/shm
none                  2.0G   48K  2.0G   1% /tmp
none                  1.9G  212K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/dev/sda1             228M  161M   55M  75% /boot

```

As you can see above, /dev/shm is a filesystem for itself stored in RAM. You can use it to store your temporary files, and it will be much, much faster than /tmp (which is a filesystem on disk in most installations).

I suggest if you want to save your temporary files, implement it in your program.

---

### Post by tanoloco on 2011-11-06
Duh, perfect explanation!

Many thanks!!! :P
Cheers

---

