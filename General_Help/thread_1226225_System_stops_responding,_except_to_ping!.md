---
title: "System stops responding, except to ping!?"
date: 2009-07-29
forum: General Help
---

### Post by dolson on 2009-07-29
Hi, I hope someone can help me.

I installed Ubuntu 9.04 (32-bit) using the mini ISO. If you aren't familiar with it, it's about 11MB in size and downloads only needed packages from the net.

Anyhow, the system is up and running, and things were good. But about 16 hours after bootup, the system just stops working. Apache, ssh, MediaTomb - all stop working. I can't even log in to the system itself with a keyboard and monitor attached. However, it WILL respond to pings...

I do not have X installed on this system, because I was primarily using it as a file server for my PS3. I have never run Ubuntu for my server before, only debian. I was trying to switch back to Ubuntu again, so if anyone can help me, it'd be appreciated. Otherwise, I guess I'll try debian again.

---

### Post by MichealH on 2009-07-29
Have you installed it with Ext 3 0r Ext 4 because Ext 4 has some bugs check [this]("http://ubuntuforums.org/showthread.php?t=1133719") out.

I have installed 9.04 on Ext 3 and it works Perfect!

---

### Post by t4thfavor on 2009-07-29
I have the same issue, I do have some ext4 hdd's connected to the machine too. It should be noted that I am running up to date, jaunty 9.04 and I haven't had the same problems in a few days. Though I did notice this when I was running apt-mirror to an ext4 hdd.

---

### Post by dolson on 2009-07-29
Yup, I did use ext4... I used it for all of my drives (3 of them). I have about 300GB of data that I can't really move around, but I will try and borrow an external drive or something and reinstall the main OS on ext3.

I didn't know there was an issue with it. That kinda sucks. Oh well, I will try. In the meantime, if anyone else reads this and has experienced this issue, let me know if you found it was definitely an ext4 issue or something else.

The system has locked up like this twice now. I forgave it the first time, but now something has to change.

---

### Post by MichealH on 2009-07-29
Glad to be of any help to you. If you find this to be of any help mark this thread a SOLVED.:D

---

### Post by dolson on 2009-07-29
OK, instead of reinstalling, I just copied my data using cp -aux from my / to my /alternate (I always partition my main OS drive so I can have two distros installed at once - makes it easier to upgrade and downgrade if required when new releases come out), modified my menu.lst, and booted up on the alternate partition (which I had formatted to ext3).

I still have a mounted ext4 partition, but I'm moving my data from that to an ext3 one, and then will format that as ext3 as well. And then, I should be good to go (assuming this was all just an ext4 problem).

The system has locked up (still replies to pings) two or three more times since I posted this thread, so I should know relatively quickly if the ext3 thing fixes the problem. The odd thing is that there are no messages in any of the logs I looked through.

Anyhow... Hope this works.

---

### Post by t4thfavor on 2009-07-30
I reformatted ext3, and have not had any issues since, I am not sure what fixed it, because there have been numerous system updates since.

---

### Post by dolson on 2009-08-02
I did have lockups up until I got data off my last ext4 drive, formatted as ext3 and put my data back.

Once all of the ext4 partitions were gone, all I did was reboot for good measure, and haven't had a lockup since. I didn't do any updates.

I thought my hardware was gone bad.

So, thanks for the advice! I think I'll just avoid ext4 for a few years, until it proves itself.

---

