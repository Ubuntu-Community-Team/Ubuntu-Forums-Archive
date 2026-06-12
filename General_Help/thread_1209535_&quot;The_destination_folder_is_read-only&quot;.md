---
title: "&quot;The destination folder is read-only&quot;"
date: 2009-07-10
forum: General Help
---

### Post by Chase Young on 2009-07-10
Mhmmmm... I must say, since my last time booting Ubuntu on my old computer, it's showing a lot more difficulty lol. My sound doesn't work, and I know there's about 50 methods to fixing that.

None of them work.

So I've come to facts that until I get a new sound card, I will not be using my laptop for music. However, I plan to overcome this little ordeal with a flash drive and an Xbox 360. Conveniently, I have both. The problem is, whenever I try to move music onto the flash drive, I get an error saying, "The destination folder is read-only". Is there any way to fix that, or am I doomed to suffer musicless programming, web-surfing and other computer based ordeals?

---

### Post by michy99 on 2009-07-10
What is the output of```
ls -l /media
```

---

### Post by Chase Young on 2009-07-10
Of the flash drive, or the music?

---

### Post by michy99 on 2009-07-10
Just enter that command in the terminal. Doesn't matter where you are.

---

### Post by Chase Young on 2009-07-10
Oh. Sorry, I thought I was to replace the "media" part of the command with my media. My bad. Anyways,

```

total 28
drwxrwxrwx 1 root  root  8192 2009-07-07 19:07 ACER
lrwxrwxrwx 1 root  root     6 2009-07-07 13:10 cdrom -> cdrom0
drwxr-xr-x 2 root  root  4096 2009-07-07 13:10 cdrom0
drwx------ 8 james root 16384 1969-12-31 20:30 disk

```
I'm thinking I have to chmod, but tbh, I've never actually used it. Except when I used to build websites.

---

### Post by michy99 on 2009-07-10
I'm assuming that the flash drive is the one named 'disk' See if this fixes it.```
sudo chmod 777 /media/disk
```Also, sometimes a flash disk will have a switch on it to make it read-only.

---

### Post by Chase Young on 2009-07-10
I'll check the switch, and here's the output of the command (it didn't work =():

```

james@ubuntu:~$ sudo chmod 777 /media/disk
[sudo] password for james: 
chmod: changing permissions of `/media/disk': Read-only file system

```

When I try to move music over, same error. I did the command and flipped the switch. You're right, by the way, it is "disk".

---

### Post by michy99 on 2009-07-10
I found a thread with a similar problem:

[http://ubuntuforums.org/showthread.php?t=1208072](http://ubuntuforums.org/showthread.php?t=1208072)

He had to format the drive in Windows to get it to work. I wonder if formating with gparted would do the trick?

---

### Post by Chase Young on 2009-07-10
Hey I'm willing to give it a shot. 2 problems, though.

1. I don't know how to format it on Windows, the DOS command didn't work.
2. Haven't a clue what gparted is.

I'm new to Ubuntu, sorry.

---

### Post by nice_like_rice on 2009-07-10
Can we just check something?

Whats the output of

```

cat /etc/mtab | grep disk

```


Maybe for some strange reason it is being mounted as read only, and can be remounted as read/write?

---

### Post by Chase Young on 2009-07-10
```
/host/ubuntu/disks/root.disk / ext3 rw,errors=remount-ro 0 0
/host/ubuntu/disks/boot /boot none rw,bind 0 0
```

---

### Post by nice_like_rice on 2009-07-10
Okay it's not :)

As michy99 said, try reformatting it. Gparted is a partition manager for gnome, and you run it with "sudo gparted". Then make sure you select the right disk, and reformat it as ntfs/fat32, or whatever it was before.

---

### Post by Chase Young on 2009-07-10
Whoops. I tried formating it and it basically told me to **** off lol. It says one of two things.

1. The disc is write protected, n which case I flip the switch on it and it displays this message

2. The disc is in use, close any applications using it and try again.

Gf Windows. I looked up that Gnome Partition Editer, it didn't do much for me either. So I'm just gonna buy a new flash drive lulz. Thanks for your help though =)

---

### Post by nice_like_rice on 2009-07-10
You posted that already lol :)

The "rw" means it's mounted as read-write, so that's not the problem.

---

### Post by Chase Young on 2009-07-10
Yea sorry about that, I thought it had disapeared cause it changed pages..My bad. I edited it though, look up =)

---

### Post by nice_like_rice on 2009-07-10
Ok :)

Strange that, but they're not too expensive anymore. good luck

david

---

