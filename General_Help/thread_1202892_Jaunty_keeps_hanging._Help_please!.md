---
title: "Jaunty keeps hanging. Help please!"
date: 2009-07-02
forum: General Help
---

### Post by shahveer on 2009-07-02
Hi all,
I'm running Kubuntu 9.04 on my laptop. Its been fine for the past few months.
Today, the following happened:

1. I was copying data from my laptop to my external USB drive. 
2. Suddenly, the whole system froze so I had to switch it off and on again.
Plugged in the USB, same thing happened again.
3. After rebooting, it was back to the default oxygen theme and screen
resolution, desktop display etc. No idea why, so made all the changes again.
4. Since then, the laptop randomly just freezes. I have no idea why. I'm not a
linux guru at all. I tried checking log files, and not sure if its the right
one, but I checked the kern.log file. 
I don't know if this is the matter but I found this - Marking TSC unstable due
to TSC halts in idle

Prior to this, another error I found in the log file was EXT4-fs warning:
maximal mount count reached, running e2fsck is recommended"

I booted using a live cd and did fsck. Whether that worked or not I really
don't know.

Anyhow, this is happening every few minutes for some reason. I think its
something to do with my external USB drive whilst data was being transferred?

I was using Ktorrent and downloading but stopped that for now in case its
something to do with the torrents being saved to one of my partitions.

ANY help / advice would be greatly appreciated. If you need me to post any
logsAs or outputs, just let me know what to type.
As I said, I know basically nothing about linux so please be as kind and patient
as possible. :)

Thank you!

PS - Glad it didn't freeze whilst typing this!!

---

### Post by renkinjutsu on 2009-07-02
get to a terminal and```
sudo init 1
```
then, drop to a root terminal and```
umount -a
```
and do a ```
fsck.ext4 -v -f /dev/<drive>
```

and also, make sure you have the latest kernel images from the repositories (your image may have become corrupt..)

---

### Post by shahveer on 2009-07-02
> **renkinjutsu said:**
> get to a terminal and```
sudo init 1
```then, drop to a root terminal and```
umount -a
```and do a ```
fsck.ext4 -v -f /dev/<drive>
```and also, make sure you have the latest kernel images from the repositories (your image may have become corrupt..)

Thanks renkinjutsu for the quick reply.
I forgot to mention earlier - I am running kernel 2.6.29-02062903-generic

After all these problems started, I did sudo apt-get upgrade and it said it was downloading kernel 2.28 and some other stuff. Strange, but I didn't stop it! 

Anyhow, I did what you said. Opened a terminal window and typed sudo init 1
As soon as I did this, it restarted and came to the boot options screen which comes if you select recovery mode whilst booting.

Did I do something wrong somewhere?

Thanks!

Okay, my laptop just restarted X ( I think its called X - just the GUI) all on its own suddenly. I'm going to try what you said above again now.

---

### Post by shahveer on 2009-07-02
I'm sorry. I just checked what sudo init 1 is supposed to do.
So I dropped to root, and did umount-a but it said device is busy.

I then did the next command. On some of the partitions it says 1 non-contiguous file found (1.1%). Another says 72 such files found (53.3%)

What does this mean? Is this the reason for the problem?

Thanks.

---

### Post by shahveer on 2009-07-02
Hi, can anyone help please?
I checked my logs again and this error seems to be coming - Marking TSC unstable due to TSC halts in idle

I tried the solution found here - [http://bwyan.dk/?p=374](http://bwyan.dk/?p=374) - but it hung again.

Thank you in advance!

---

