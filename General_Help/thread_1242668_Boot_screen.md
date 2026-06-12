---
title: "Boot screen"
date: 2009-08-17
forum: General Help
---

### Post by leona on 2009-08-17
Hi there.

I wonder if someone might help me with this.

I cloned my drive (upgraded hard drive), since doing so, the boot screen now displays a lot of loading status stuff, (verbose) where it just used to give me the ubuntu with the loading bar, I want the loading bar back.

I looked in the grub loader and it seems to read ok.

My grub loader looks like
```

/vmlinuz-2.6.24-24-generic root=UUID=89a24bda-e31b-4205-a711-d95170b5eff8 ro quiet splash

```
So why has it gone, and how do I get it back?

Thanks.

---

### Post by trikster_x on 2009-08-22
I recently had a problem like this.  I had moved a couple partitions around to make my /home a seperate one, and lost the graphical loader.  The problem was the new uuid didn't match the one that was originally associated any more on any of the partitions.  Fortunately it is just a matter of changing the uuid to match the new one.  Unfortunately, I was in the process of looking for the post on how to bring up a uuid for a problem I am having now when I came across your thread, so I can't offer much help beyond that.  If I find what I was looking for I will post a fix.

EDIT:

type blkid in a terminal then open /etc/fstab and /etc/initramfs-tools/conf.d/resume and make sure all the uuid's match, specifically your swap id.  If not, then make the changes accordingly using ```
sudo gedit "/location/of/file/to/change"
```  This is my best guess, so hopefully it works.

---

### Post by Rainbow Road on 2009-08-24
Have a look at post 5 of [this thread]("http://ubuntuforums.org/showthread.php?t=857565"). I had a similar problem where I used gparted to tidy my hard drive and both Ubuntu and Mint lost their graphical loading progress bar which was replaced with list of loading files. Both my OS are now showing the progress bar. 
HTH.

---

### Post by leona on 2009-09-19
Thank you, I had a look at the thread and my UUID's for my swaps where different, but changing them has not resolved the problem.

```

sudo blkid -c /dev/null

```
returns
```

/dev/sda10: TYPE="swap" UUID="90a2099b-b4c5-4ad0-8505-123e2e1dfc1a" 

```
```

/etc/initramfs-tools/conf.d/resume 

```
Contains.
```

RESUME=UUID=90a2099b-b4c5-4ad0-8505-123e2e1dfc1a

```
FSTAB contains
```

UUID=90a2099b-b4c5-4ad0-8505-123e2e1dfc1a none            swap    sw   0 0

```

As you see they all match and I did the update.

Still no splash screen.

Any other ideas?

---

### Post by trikster_x on 2009-09-19
Do the UUID's of all your other partitions match as well?  I know I had to change all of mine when I used that fix.

---

### Post by leona on 2009-09-21
Hi
I think they do all match ya.
sudo blkid -c /dev/null
```

/dev/sda7: UUID="0e672aef-12b9-44ed-ac27-bf9b6f9bf0ab" TYPE="ext3" 
/dev/sda8: UUID="89a24bda-e31b-4205-a711-d95170b5eff8" TYPE="ext3" 
/dev/sda9: UUID="0a19f1ca-c309-4a0f-adbc-74b216ea839a" TYPE="ext3" 
/dev/sda10: TYPE="swap" UUID="90a2099b-b4c5-4ad0-8505-123e2e1dfc1a" 

```
FSTAB
```

# /dev/sda8
UUID=89a24bda-e31b-4205-a711-d95170b5eff8 /      ext3
# /dev/sda7
UUID=0e672aef-12b9-44ed-ac27-bf9b6f9bf0ab /boot  ext3
# /dev/sda9
UUID=0a19f1ca-c309-4a0f-adbc-74b216ea839a /home  ext3
# /dev/sda10
UUID=90a2099b-b4c5-4ad0-8505-123e2e1dfc1a none            swap

```

---

### Post by trikster_x on 2009-09-28
The only othere thing I can think of is that your splash page was corrupted or something when you cloned your drive.  Try following the instructions here:  [https://help.ubuntu.com/community/USplash]("https://help.ubuntu.com/community/USplash")
I would suggest trying to use a different artwork at first, that way it clears out the old artwork file, and if it works, go back to your original usplash artwork.  It's a long shot, but it might work.

---

