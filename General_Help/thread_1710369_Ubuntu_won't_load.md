---
title: "Ubuntu won't load"
date: 2011-03-19
forum: General Help
---

### Post by ravis51 on 2011-03-19
So I wubi downloaded ubuntu a couple weeks ago and have been fine with using it. However, today when I tried to access it from my dual boot menu, at first comes a message that says:
Try (hd0,0): NTSF5: No wubilder
Try (hd0, 1): NTSFS:
This message has come up before when I booted but hasn't caused any problems in the past.
After that comes a screen with GNU GRUB version 1.98-1ubuntu9
Minimal BASH-like editing is supported. For the first word, TAB list possible command completions. Anywhere else TAB lists possible device or file completions.

grub>


I can access windows just fine however, I have no clue how to get back to normal on ubuntu. Also I am a newbie when it comes to Ubuntu, so please bear with my ignorance.

---

### Post by bcbc on 2011-03-19
See the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198")

Most likely Problem #2, Solution #1. Then there's a permanent fix.

Since you have a grub prompt it's possible to boot Wubi and fix it (without a live CD). Give the output of:

```
search -s -f -n /ubuntu/disks/root.disk
echo $root
```

---

### Post by ravis51 on 2011-03-19
For the first command, i got the result

error: no such device: /ubuntu/disks/root.disk.


For the second I got
hd0,2

---

### Post by bcbc on 2011-03-19
That doesn't sound good. 

Can you boot windows and make sure that the root.disk is there. If you don't see it (C:\ubuntu\disks\root.disk - change C: if you didn't install on C: ), then turn on hidden folders and system files and look for a C:\FOUND.000 folder and make sure that Windows hasn't moved it there. If so, move it back to the C:\ubuntu\disks directory.

If it's there then boot back to Ubuntu. When you get to the command prompt enter:
```
linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

After booting, make sure you follow the Permanent Fix in the wubi megathread.

---

### Post by ravis51 on 2011-03-19
I found the C:\ubuntu\disks\ on windows, however when I tried to open it, to get to the root.disk, I received some error. I went back, to check if it was the right folder and it was, when I checked again, it was gone. I don't understand how that happened. Do you have any suggestions, or should I just give up on this?
Also, I did not find anything named found.000

---

### Post by bcbc on 2011-03-19
search your computer and look for a file named root.disk.

Try running chkdsk (My computer, right click on C:, properties, tools, check disk for errors, fix automatically)

If you can't find it then the Ubuntu install is gone. It's possible that the root.disk was corrupted somehow (hard shutdown?) and windows seems to take care of these in different ways. It should move them to a hidden C:\FOUND.??? folder but...  it's unclear whether this is always the case.

---

### Post by ravis51 on 2011-03-19
I don't find anything, searching through all of it there are no results. I've decided whatever data I've lost is lost and I'll just proceed with using a live cd and never using a wubi install again. Thanks for the help though. It saved me a lot of time.

---

### Post by bcbc on 2011-03-20
That's unfortunate. I don't know what it is that could cause this. Windows is supposed to saves corrupted files in C:\FOUND.??? and I have no idea why that works in some cases but not others. 

That is one of the problems with Wubi: everything on a single file. I don't think this is a typical case, but it's certainly catastrophic when it does happen.

Can you think of anything you did, or something that happened that was out of the ordinary that could have caused this?

What version of Windows are you running?
How large was your root.disk?

---

### Post by bcbc on 2011-03-20
I was reading this old article on chkdsk [http://technet.microsoft.com/en-us/library/bb457122.aspx](http://technet.microsoft.com/en-us/library/bb457122.aspx)

It seems that the recovered file may not be named root.disk (could be Filennn.chk). It also seems that if the file is sufficiently corrupted it may not be recovered at all. I would guess a very defragmented file system might play a role in this too.

Anyway... it seems you've moved on, but it's helpful for others who might have the same issue.

---

