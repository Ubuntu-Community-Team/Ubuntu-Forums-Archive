---
title: "current state of ext4, as of july 09, with 9.04?"
date: 2009-07-12
forum: General Help
---

### Post by Linux&amp;Gsus on 2009-07-12
Hi folks,
I know ext4 has been discussed here before. But I would like to know where things are at right now.

Reason I'm asking is, I'm running out of disk space on my laptop. But since it's a bit an older one, needs PATA drives, etc I'm not sure if it's worth investing in a new drive for the computer. Since that drive wouldn't fit in any other new computer. I believe they all have SATA drives, right?
My current /home has 50GB of which I used ~40GB. From my understanding (that's what I heard before, don't know though if that's true) it would be good to have 5-10GB free space on a HDD for better performance.

Now, I still have a 40GB 2.5" drive in an external USB case. I could off-load some stuff to that one. Things like pictures or other stuff I don't need constantly.
My question is, would it be better to format that drive with ext3 or ext4? Does it make a speed difference at all on an external drive or is USB (the external case has no firewire) the bottleneck?

Or should I better forget this idea and invest in a new drive and when time comes and this computer is in hardware heaven stick that drive in an external case?
However, if I do that I don't think I want to go through the trouble and install Windows on the new drive. Even though I need it every now and then to test websites with it. If I would put the current drive in an external case can I then boot Windows off it or will I have trouble with that? In worst case I still could swap drives. But seriously, all this trouble for Windows...

Also, in an external case, USB or Firewire, would it make a speed difference between PATA and SATA?

Anyways, the main question is, I'm running Kubuntu 9.04 here with / and /home as ext3. What is the current state regarding ext4. Assuming all updates. I know that there were potential problems when ext4 was just released.

Would you say that by now it's ready for production use? This laptop here is my every day work horse. So, I can't afford any major trouble with it. But since it's not exactly a very fast computer I appreciate anything that speeds up things.

So, what are your thoughts about ext4? No problem at all, OK for non-critical use when good backup is in place or simply a no-go at the moment. With 9.04 that is. I heard that Karmic will have a new kernel that addresses some issues.

The poll represents the options I could think of. If you have another opinion then feel free speak up.

Cheers,
L&G

---

### Post by Frugoo Scape on 2009-07-12
Ext4 works perfect, I run a software raid that is ext4.

Edit:
Sorry for the short post, I feel I disrespected you because of your long post. I hate people that did exactly what I did lol.

---

### Post by DeMus on 2009-07-12
> **Linux&Gsus said:**
> Hi folks,
I know ext4 has been discussed here before. But I would like to know where things are at right now.

Reason I'm asking is, I'm running out of disk space on my laptop. But since it's a bit an older one, needs PATA drives, etc I'm not sure if it's worth investing in a new drive for the computer. Since that drive wouldn't fit in any other new computer. I believe they all have SATA drives, right?
My current /home has 50GB of which I used ~40GB. From my understanding (that's what I heard before, don't know though if that's true) it would be good to have 5-10GB free space on a HDD for better performance.

Now, I still have a 40GB 2.5" drive in an external USB case. I could off-load some stuff to that one. Things like pictures or other stuff I don't need constantly.
My question is, would it be better to format that drive with ext3 or ext4? Does it make a speed difference at all on an external drive or is USB (the external case has no firewire) the bottleneck?

Or should I better forget this idea and invest in a new drive and when time comes and this computer is in hardware heaven stick that drive in an external case?
However, if I do that I don't think I want to go through the trouble and install Windows on the new drive. Even though I need it every now and then to test websites with it. If I would put the current drive in an external case can I then boot Windows off it or will I have trouble with that? In worst case I still could swap drives. But seriously, all this trouble for Windows...

Also, in an external case, USB or Firewire, would it make a speed difference between PATA and SATA?

Anyways, the main question is, I'm running Kubuntu 9.04 here with / and /home as ext3. What is the current state regarding ext4. Assuming all updates. I know that there were potential problems when ext4 was just released.

Would you say that by now it's ready for production use? This laptop here is my every day work horse. So, I can't afford any major trouble with it. But since it's not exactly a very fast computer I appreciate anything that speeds up things.

So, what are your thoughts about ext4? No problem at all, OK for non-critical use when good backup is in place or simply a no-go at the moment. With 9.04 that is. I heard that Karmic will have a new kernel that addresses some issues.

The poll represents the options I could think of. If you have another opinion then feel free speak up.

Cheers,
L&G

Yes, it is good to have some spare space on a disk. Ubuntu (Linux) uses a disk in another way than Windows does. Linux does not fragment files but keeps them in one part. Until the disk is getting full, then small open spaces will be filled and fragmentation will occur.

Ext4 is faster than Ext3. If you will notice the speed difference using an external drive is questionable since the USB connection will probably determine the speed.

Forget about Windows. You say you need it to test websites? You can't use Ubuntu for this with Firefox? Install a plugin to let the world believe you do use IE.

I installed Jaunty 9.04 in April when it arrived on Ext4 disks (/ /var /usr and /home) and never had trouble with it. It is safe to use in my opinon, but maybe others have other experiences. I use it on my daily workhorse and it works great. Go for it.

---

### Post by Linux&amp;Gsus on 2009-07-12
@Frugoo Scape
Don't worry, I usually write half a book to even only describe the simplest of things. Thanks for comment. That really is what I need to know, it either works or (still?) gives trouble.

@DeMus
The trouble with Windows is not so much me making others believe I have Windows with IE. It's more the other way round. If I do something for a website I want to / need to make sure it works the same for Windows users. With or without IE. Hence the "testing" rather then using sites that require IE ;)

Also thanks for your opinion about the USB side of things. That is sort of what I was thinking as well. Just wasn't sure.

Cheers,
L&G

---

### Post by Linux&amp;Gsus on 2009-07-14
hmmmmm...
No other opinions? Or is this common sense by now?

---

### Post by 3rdalbum on 2009-07-14
Ext4 isn't like KDE 4 - it's just an evolution of Ext3.

There's been a fairly long period of testing for ext4 anyway, and most of the filesystem is ext3, so you're safe.

There was a problem with the way some programs interacted with a new Ext4 feature that could cause a small amount of data loss if your system crashed fully - you might see some articles about that. That feature of Ext4 has been turned off to restore enterprise-level reliability.

---

### Post by Linux&amp;Gsus on 2009-07-15
Thanks for that info 3rdalbum. So, I guess that is the current state then.

OT:
@3rdalbum, where in WA are you? Can send me a PM if you want. I'm in WA as well.

---

### Post by rogerh on 2009-07-15
Hey, sorry seems I'm going against the tide here.
I've had lots of issues with ext4 in jaunty - my lost+found dir on my home partition has 265 entries. There is one entry in the dir on my root partition.

I have had to fsck to recover the system a few times on bootup and this is what is creating these entries.

I haven't spent much time yet trying to track down the reason why this occurs - looking into the contents of the lost and found dir shows lots of firefox files, and gnome profile files. Obviously these are files which are used a lot, and opened/closed/modified often.

This computer is a reasonably recent Dell laptop (Precision M4300), however the battery is worn out and therefore it may be shutting down uncleanly more often than is normal. However, even assuming this is the cause of the errors, there are more errors than I have ever seen using ext2 and ext3 over an extended period of time. Normally you get away with the occasional crash, seems this is not the case with ext4.

My recommendation would be steer clear of ext4 unless you are really keen on playing with the new stuff. I'm here looking for a solution at the moment, and if I don't find one I'm going to have go back to ext3.

---

### Post by Linux&amp;Gsus on 2009-07-16
Now I'm scared again. :shock:

Well, then I guess I have to decide how important that stuff is for me. If I can afford to loose what I'm going to put on that HDD on the go. I have a backup at home then anyways (hopefully). Question is, can I always wait until I'm back...

Thanks,
L&G

---

