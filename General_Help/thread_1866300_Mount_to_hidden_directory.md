---
title: "Mount to hidden directory"
date: 2011-10-21
forum: General Help
---

### Post by JasonFWard on 2011-10-21
It seems a rare event when I get any answer to my questions here, but hey ho, I try again.

The command below works great, exactly as expected```
sudo mount --bind /media/MilkyTank/.VirtualBox /home/jason/.VirtualBox

```

As you can see here

```

jason@Milkyway:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
...
/media/MilkyTank/Downloads on /home/jason/Downloads type none (rw,bind)
/media/MilkyTank/.VirtualBox on /home/jason/.VirtualBox type none (rw,bind)
jason@Milkyway:~$
```

However when I add it to /etc/fstab as follows:```


jason@Milkyway:~$ cat /etc/fstab
...
"/media/MiltyTank/.VirtualBox" "/home/jason/.VirtualBox" none rw,bind 0 0
``` and run mount -a
```
jason@Milkyway:~$ sudo mount -a
[mntent]: line 18 in /etc/fstab is bad
mount: mount point "/home/jason/.VirtualBox" does not exist
```I get an error.

If I remove the quotes from around the mount point and what to mount, I get this error instead```
mount: special device /media/MiltyTank/.VirtualBox does not exist

```

What am I doing wrong?

---

### Post by drs305 on 2011-10-21
I did some testing as I'm not a fstab genius and I did find a workaround.

1. I tried what you had and got similar results and error messages.

2. I created a non-hidden link to your hidden folder and used that name in fstab.
> /media/MiltyTank/Link.VirtualBox /home/jason/.VirtualBox none rw,bind 0 0

It mounted correctly with no errors. So I'm not sure how you designate a hidden folder to mount, but a non-hidden link appears to mount just fine.

---

### Post by JasonFWard on 2011-10-21
Thanks for that.

Your reply also showed me a spelling mistake I had made,but correcting it had no substantive effect on the problem, /etc/fstab does not like hidden directories as mount points it would seem.

I've been looking at your solution, and it's quite neat, but I think I will after just do what I should probably have done in the first place and just move /home/ wholesale to new partition.

Cheers
Jason

---

