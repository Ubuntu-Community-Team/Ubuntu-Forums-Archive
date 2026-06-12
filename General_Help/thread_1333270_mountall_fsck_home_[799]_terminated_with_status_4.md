---
title: "mountall: fsck /home [799] terminated with status 4"
date: 2009-11-21
forum: General Help
---

### Post by MacHaddock on 2009-11-21
I need HELP!!!

So I was watching a video on gametrailers and using deluge and pidgin and some other stuff. Suddenly the video started skipping in the same spot and nothing not even the mouse cursor would answer to input. I had to hard boot.

Then while loading it said that it was checking the file system and came up with that there was a problem and that it started some form of "fixit shell" I didn't know what to do in that shell so I rebooted again and choose recovery mode from grub.

The recovery mode started to check the file system (I think it was) and came up with this.

/dev/sda4 contains a file system with errors, check forced.

And then this:

/dev/sda4: Inodes that are part of a corrupted orphan linked list found.

/dev/sda4: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
             (i.e., without -a or -p options)
mountall: fsck /home [799] terminated with status4
mountall:filesystem has errors: /home


Is my home directory broke forever or is there some way I can fix it??? Maybe from that "fixit" shell i mentioned in the beginning of the post???

I'm writhing this now from my otherwise unused windows 7 partition. Please don't make me stay on it for long...

---

### Post by MacHaddock on 2009-11-21
Anyone PLEASE

---

### Post by whoop on 2009-11-21
Well, it says what you need to do, run fsck manually.
```

fsck

```

---

### Post by MacHaddock on 2009-11-21
I booted recovery mode and ran fsck
It came back

/dev/sda3: recovering journal
fsck.ext3: Bad magic number in super-block while trying to re-open /dev/sda3 e2fsck: io manager magic bad!

then I ran it again giving

fsck from util-linux-ng 2.16
fsck.ext3: Unable to resolve 'UUID-5b272b5b-822e-4a83-4a83-b688-3ea8302080c1'

and that's all it said. When I try to reboot now the gurb doesn't work It gives me ERROR 17 and I can't even get in to my windows 7 partition any more. I'm writing this from my old 9.04 live cd.

wont someone please help me I have a meeting Friday and there is files on the /home partition I need for that meeting!!!

---

### Post by Zoot7 on 2009-11-21
Generally errors with fsck point to either your file system being corrupt beyond repair or the hard drive failing.

Try running this:
```
sudo fsck -y /dev/sda3
```

Failing that I would boot off the liveCD and try to recover the files that you really need that way.
If you can't mount it, it might be worth trying to force mount it:
```
sudo mount -t ext4 /dev/sda3 /mnt -o force
```

---

### Post by MacHaddock on 2009-11-22
It's to long to post here but basically that gave me A LOT of these

Free inodes count wrong (610789, counted=460190).
Fix? yes

and then in the end this

/dev/sda3: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda3: 150610/610800 files (1.8% non-contiguous), 813422/2441880 blocks

I'm going to try a reboot now and will post what happens.

[EDIT]
Well that fixed the grub and I got back to what it said before I tried to fix anything. I entered a "fixit" shell and I ran fsck agian and it did and found som stuff that I fixed and now IT WORKS!!!

I love you people thanks so much for helping, I love linux and I love Ubuntu!!!

ps. I feel like such a hacker right now :D

[EDIT again]
Oh there is one thing I noticed right away though. There is a big *** lock on my documents folder. I can access files in it. I only tried with one though. I can't make new folders in it. As owner it says root. How do I fix that?

[EDIT number 3]
I figured out how to change ownership with the help of this page.
[http://www.linuxhelp.net/newbies/#chown]("http://www.linuxhelp.net/newbies/#chown")

---

### Post by Zoot7 on 2009-11-22
Haha, glad to hear you're sorted! :)

---

### Post by MacHaddock on 2009-11-22
Ok there seems to be some other side effects.

Like me not being able to load facebook and some other pages...

[Edit]
Never mind now it works for some reason.

Byt the way how do you delete a post here?

---

### Post by Zoot7 on 2009-11-22
> **MacHaddock said:**
> Byt the way how do you delete a post here?
Edit -> Advanced and there should be an option to delete the post, at least there is on the VBulletin version on my forum.

---

### Post by pdany4 on 2011-10-19
> **Zoot7 said:**
> Generally errors with fsck point to either your file system being corrupt beyond repair or the hard drive failing.

Try running this:
```
sudo fsck -y /dev/sda3
```

Failing that I would boot off the liveCD and try to recover the files that you really need that way.
If you can't mount it, it might be worth trying to force mount it:
```
sudo mount -t ext4 /dev/sda3 /mnt -o force
```

Hello,
I'm french, I've problem too and I run :
```
sudo fsck -y /dev/sda3
```
and it's fonctionned !

But now, after restart OK, I have a message to problem with .ICEauthority, I go to look internet.

Thank's to procedure of réparation with fsck -y /dev/sd3

Cordially

---

