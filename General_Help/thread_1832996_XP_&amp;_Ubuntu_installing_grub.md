---
title: "XP &amp; Ubuntu: installing grub"
date: 2011-08-25
forum: General Help
---

### Post by Dry Lips on 2011-08-25
After installing XP on a machine with Ubuntu Server, I'm no longer
 able to boot into Ubuntu. This was expected, but I wasn't able to 

reinstall the grub when I attempted this...
  

 I did:
```
sudo mount /dev/sda1 /mnt
 sudo grub-install --root-directory=/mnt/ /dev/sda
 
```
The last bit finished witout any errors.
 

But after rebooting, it wasn't Ubuntu that started, but XP!
  I suggest that this perhaps is the problem:
  

```
Device Boot      Start         End      Blocks   Id  System
 /dev/sda1               1        1987    15953920   83  Linux
 Partition 1 does not end on cylinder boundary.
 /dev/sda2   *        1987        6994    40220672    7  HPFS/NTFS
 Partition 2 does not end on cylinder boundary.
 /dev/sda3            6994        7298     2438145    5  Extended
 Partition 3 does not end on cylinder boundary.
 /dev/sda5            6994        7298     2438144   82  Linux swap / Solaris

```

So... What do I do?

---

### Post by Dry Lips on 2011-08-25
Ooops! My bad! It didn't boot into the XP partion I just had installed,
but into the XP that was on the secondary HDD... When I unplugged
the HDD, it booted into Ubuntu as before, and I was able to do a
```
sudo update-grub
```

However there is something that is strange... When starting Ubuntu server
I get this message for a few seconds, before it boots up as normal:

  	 	 	 	 	 	  ```
error: no argument specified. Press a key to continue...
```
 And when checking fdisk -l, I still get the message about partitions not
ending on cylinder boundary.

Will this be a problem?

---

### Post by seawolf167 on 2011-08-25
> **Dry Lips said:**
> I still get the message about partitions not
ending on cylinder boundary.

Will this be a problem?

Take a look at post #2 on [this link]("http://ubuntuforums.org/showthread.php?t=1070547").

---

### Post by Dry Lips on 2011-08-25
> **seawolf167 said:**
> Take a look at post #2 on [this link]("http://ubuntuforums.org/showthread.php?t=1070547").
Excellent! Thanks mate! :D 

(In other words, partitions not ending on cylinder boundary is nothing to worry about.)

---

I'm temped to mark this thread as solved, and I will in a short time,
but I just wanted to see if any has a clue about the final problem...
When I boot into both Ubuntu and Windows I get this:

```
error: no argument specified. Press a key to continue...
```----
edit:

I use Ubuntu server 10.04.2. LTS... The version of the grub is 1.98. I see that 
some people get this error message when updating the grub from 1.98 to
1.99, but I don't know if *my* problem can be solved by **--set=root, **since 10.04 
run 1.98, and not 1.99...
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by seawolf167 on 2011-08-25
If when you boot into Ubuntu you run

```
sudo update-grub
```

does the problem continue to occur?

---

### Post by Dry Lips on 2011-08-25
> **seawolf167 said:**
> If when you boot into Ubuntu you run

```
sudo update-grub
```does the problem continue to occur?

Yes, I've tried that, but it still persists! :-s

---

### Post by seawolf167 on 2011-08-25
What is the output of 

```
grub-install -v
```

---

### Post by Dry Lips on 2011-08-26
Here ya go:
```
grub-install (GNU GRUB 1.98-1ubuntu12)
```

---

### Post by seawolf167 on 2011-08-26
Well, nevermind then. I saw [this thread ]("http://ubuntuforums.org/showthread.php?t=1662142")regarding the error message in Grub 1.99 same as you mentioned above. But since you are definitely using 1.98 it doesn't appear that this would apply. Hopefully someone else will come along and have an idea!

---

### Post by Dry Lips on 2011-08-26
> **seawolf167 said:**
> Well, nevermind then. I saw [this thread ]("http://ubuntuforums.org/showthread.php?t=1662142")regarding the error message in Grub 1.99 same as you mentioned above. But since you are definitely using 1.98 it doesn't appear that this would apply. Hopefully someone else will come along and have an idea!

Well, thanks for your kind help so far, even if my last problem isn't solved yet! :KS

---

### Post by Dry Lips on 2011-08-27
Bump :eek:

It is still the problem outlined below that I need help with:
```
error: no argument specified. Press a key to continue...
```

---

### Post by YesWeCan on 2011-08-28
Try purge and reistall: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) section 12.1.5

---

### Post by Dry Lips on 2011-08-28
> **YesWeCan said:**
> Try purge and reistall: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) section 12.1.5

Thanks for replying... The only problem with the solution outlined here 
is that I run Ubuntu Server, whereas the solution in the documentation
require use of a liveCD...
[I]
"Boot to the LiveCD Desktop. The CD should be the same release 
and architecture (32/64 bit)."[/I] 

But here is an idea... Is it possible to use the "Rescue a broken system"
-option in the Ubuntu Server install in order to do this?

---

### Post by YesWeCan on 2011-08-28
Oh. You dont have to use a live CD. Just boot your server and do steps 8, 9 & 10 (no need for chroot).

---

### Post by Dry Lips on 2011-08-28
> **YesWeCan said:**
> Oh. You dont have to use a live CD. Just boot your server and do steps 8, 9 & 10 (no need for chroot).

Hey, hey! It worked like a charm :D Thanks a lot for your help!

---

