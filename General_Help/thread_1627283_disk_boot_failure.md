---
title: "disk boot failure"
date: 2010-11-21
forum: General Help
---

### Post by cmscott2 on 2010-11-21
I went to turn on my desktop today with ubuntu on it and it read..... disk boot failure, insert system **** and press enter....

I dont have a system disk and if I create one... wont it wipe out all my info on my computer?

---

### Post by TeoBigusGeekus on 2010-11-21
Can you boot with a live cd?
If so, try to see whether the hd is recognized.

---

### Post by cmscott2 on 2010-11-21
a live cd? im not so sure what you mean? and how do i know if the HD is recognized or not... ive had ubuntu on this pc for a few years now... and no problems so far...

---

### Post by TeoBigusGeekus on 2010-11-21
> **cmscott2 said:**
> a live cd? im not so sure what you mean? and how do i know if the HD is recognized or not... ive had ubuntu on this pc for a few years now... and no problems so far...

I mean an ubuntu live cd, the one you use to install ubuntu.
Boot up with it and see if your hd is present in the places menu.

---

### Post by cmscott2 on 2010-11-21
I dont think I have a live cd :( what to do?

---

### Post by TeoBigusGeekus on 2010-11-21
Turn off your pc and open it (I hope it's not a laptop).
Unplug/plug both the data and power supply cables of your hd - both from the hd side and from the motherboard side.
It could be the first signs of a failing hard disk.

---

### Post by cmscott2 on 2010-11-21
ok so i unplugged it and then plugged it back in..... and i started it up and still the same thing....  i dont know what to do

---

### Post by TeoBigusGeekus on 2010-11-21
Do you have access to another desktop? You could plug your hd in there and test if it can be read.

---

### Post by cmscott2 on 2010-11-21
no i have a macbook and a dell laptop.... and thats it

---

### Post by TeoBigusGeekus on 2010-11-21
What I'd do is that I'd download an ubuntu iso, burn it on a cd and try to boot from it.
Then I would fsck the hd to fix any errors.

---

### Post by cmscott2 on 2010-11-21
ok I am trying that now.... what do I do to fsck the hd to fix it?

---

### Post by TeoBigusGeekus on 2010-11-21
If you're able to boot up with the live cd, go to places and see if your hd is listed there. If so open it and see if you can navigate.
Then open terminal and give
```
sudo fsck /dev/sda1
```
Replace sda1 with the appropriate drive and partition. To find the last info, give
```
sudo fdisk -l
```
that's L, not i, before the fsck command and you'll see the disks and partitions of your system.
Good luck!

---

### Post by cmscott2 on 2010-11-21
ok so I was able to boot up the live cd and it found my HD.... im having problems with the sudo fsck 

what should I do again? im not sure I am typing or reading the instructions correctly

---

### Post by cmscott2 on 2010-11-21
maybe Im not sure what to look for when I am trying to find my hd in places.... 

i went to places... down to computer and saw file system.... 

does that mean that is my HD?

---

### Post by TeoBigusGeekus on 2010-11-21
What do you have under places?

---

### Post by cmscott2 on 2010-11-21
home folder      desktop     documents   music    pictures    videos    downloads    computer    network   connect to server   search for files

---

### Post by TeoBigusGeekus on 2010-11-21
And when you open computer?

---

### Post by cmscott2 on 2010-11-21
its an icon that says file system

---

### Post by bolwara on 2010-11-21
Hi,
 
I also have a boot failure issue and I am newly registered so please forgive this intrusion onto your thread.  I am just wanting some advice from forum members about how I could post my issue and which forum or thread would be appropriate.
I have a much loved netbook that is running windows xp.  Because I also love Ubuntu I installed Ubuntu netbook inside windows - thus allowing dual boot options.
There are 3 partitions on the hard drive and Ubuntu was installed on the E partition (lots of space) and with a large allowance of space for Ubuntu.
Yesterday I updated the software and tried to download a game.  During the update I think I may have made a mistake of proceeding with a step that increased the role of Grub.  The update was completed but the game download kept failing and I eventually got a message that the disk was full.
Then the computer froze.
When I repeatedly restarted the computer I kept getting grub rescue.
I have a lot of important stuff on this netbook because it goes with me everywhere and I do just about everything on it.
The hard disk is 120gb and is by no means full on any of the partitions.
Anyway, sorry guys.
Could someone advise about where I should go with all this.
 
regards

---

### Post by TeoBigusGeekus on 2010-11-21
Open file system and then media. Do you see anything in there?

To bolwara: Please start a new thread so that others with the same problem can benefit from it.

---

### Post by cmscott2 on 2010-11-21
nope nothing comes up

---

### Post by TeoBigusGeekus on 2010-11-21
Doesn't look good...
Open terminal and post the output of
```
sudo fdisk -l
```
(-L)

---

### Post by cmscott2 on 2010-11-21
nothing happens.... i press enter and it just goes down a line for a new command

---

### Post by TeoBigusGeekus on 2010-11-21
I'm sorry Scott but I must give you my condolences - your hd just died on you.
Go to a friend's house and try to connect it to his/her desktop to see if you could get it going (fat chance if you ask me) in order to save any of your files.

Didn't it give you any warnings, i.e. data corruption, buzzing sounds, lagging, etc.?

---

### Post by cmscott2 on 2010-11-21
yikes.... well... thanks for all your help anyways :(

---

### Post by TeoBigusGeekus on 2010-11-21
If someone has another idea, please post.

---

