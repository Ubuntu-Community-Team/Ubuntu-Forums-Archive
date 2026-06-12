---
title: "Laptop won't wake up from Suspend"
date: 2010-01-05
forum: General Help
---

### Post by SchizmWolf on 2010-01-05
Alright, maybe someone will actually find it in their hearts to help me this time. All I want to do is to be able to shut the lid on my laptop, have it go into suspend like it already does, but upon opening it again, successfully start up again. It'll sleep just fine, but if you close the lid and try to open it again later, the lights will indicate it is starting up, but the screen won't initialize, and I am left with a blank, black screen. I've tried a line of code to enter into my menu.lst file, and it seemed like it should work, but it borked my computer and I had to manually reinstate the line of code it had before. Please, I would love to resolve this stupid, stupid problem.

---

### Post by garryknight on 2010-01-05
When I hibernate my netbook then wake it up, my  screen is blank too. Then I press a key (usually Ctrl, just to be on the safe side) and up comes a login input box where I enter my password to get back into my KDE session.

The first time I ever hibernated a computer, I forgot about needing to press a key to get the login box so I held down the power button to reboot, unnecessarily. Maybe you're not as forgetful as me but did you try pressing a key?

---

### Post by Flareside on 2010-01-05
if your suspending to disk, make sure you have at least as much swap space as you do physical ram.

---

### Post by SchizmWolf on 2010-01-06
I've tried pressing keys. The swap space brings up an interesting point, though. Would it affect the hibernate on my computer since I changed my swappiness to 10 when I'm running on 2gb ram???

---

### Post by garryknight on 2010-01-06
I'm no expert on the subject, but I believe that swappiness just changes how often stuff gets swapped to disk. It doesn't affect the size of the swap space. As long as your swap space is at least as large as your RAM size, hibernate should work.

---

### Post by efflandt on 2010-01-06
There is a difference between suspend or hibernate.  Swap should not matter for suspend (which is just a low power state), but hibernate saves RAM to swap and powers down (which requires enough swap, and takes some tricks if a swapfile instead of partition), and needs to be started up to that same OS to resume.

I had no trouble with suspend or hibernate on a number of computers until I set someone up with a new laptop and got their old one.  The old Compaq goes into suspend, but when it wakes up, the keyboard and mousepad are are dead, so I can do nothing other than hold the power button until it shuts down.  So I need to research its hardware and see if something needs to be refreshed when it wakes up.

When some computers wake up, the screen remains blank until you move the mouse, but that one does not respond to any keypress and if there is a cursor, it does not move.

---

### Post by SchizmWolf on 2010-01-09
Well, I'm still fighting with this stupid thing. Whenever I close the lid and reopen it, the screen doesn't seem to initialize. As far as I can tell, the keyboard and touchpad don't respond, but I've no way to be certain without having a visual. I don't know how to change swap, either...

---

### Post by garryknight on 2010-01-09
How much memory does your machine have? How big is your existing swap space? You could try creating a larger swap partition if you have enough free space on your hard disk(s). If you want to do this, copy and paste then post the results of the following commands and we can possibly walk you through the necessary steps.

```

free
swapon -s
df -h

```

---

### Post by SchizmWolf on 2010-01-09
> **garryknight said:**
> How much memory does your machine have? How big is your existing swap space? You could try creating a larger swap partition if you have enough free space on your hard disk(s). If you want to do this, copy and paste then post the results of the following commands and we can possibly walk you through the necessary steps.

```

free
swapon -s
df -h

```

That would be great! I've got the results right here:
```

free
             total       used       free     shared    buffers     cached
Mem:       1931040    1861556      69484          0      64932    1291996
-/+ buffers/cache:     504628    1426412                                 
Swap:      3229024       2100    3226924                                 


schizm@schizm-laptop:~$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       3229024 2100    -1


schizm@schizm-laptop:~$ df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   13G   54G  20% /
tmpfs                 943M     0  943M   0% /lib/init/rw
varrun                943M  220K  943M   1% /var/run
varlock               943M     0  943M   0% /var/lock
udev                  943M  140K  943M   1% /dev
tmpfs                 943M   12K  943M   1% /dev/shm
lrm                   943M  2.4M  941M   1% /lib/modules/2.6.28-11-generic/volatile

```

---

### Post by garryknight on 2010-01-09
From looking at these figures, I can't see any reason why you should have any problem with suspending or waking up from suspend. Your swap partition is just over 3 GB in size and your RAM is less than 2 GB. The system should be able to write the entire contents of memory onto the swap partition with plenty of room to spare. Both hibernate and suspend should work.

I thought that if your swap partition wasn't large enough, you could create a new one at the end of the hard disk and see if using it made a difference, but I'm not sure there's any point in doing this now.

If you want to go ahead anyway, the steps are:
1) reboot using a live Linux CD/DVD that has gparted on it
2) delete your existing sda5 partition
3) resize your existing sda1 partition so that there's a 4 GB empty space after it
4) create a new partition using all of that empty space, making sure you mark it as swap in gparted before applying the changes

My guess is that even if you did all this, you'd still have the problem.

---

