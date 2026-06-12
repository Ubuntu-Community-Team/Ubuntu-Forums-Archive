---
title: "Randomly stopped working...?"
date: 2012-07-08
forum: General Help
---

### Post by aracanid on 2012-07-08
I apologise firstly in advance for any spelling mistakes because im using my flatmates laptop which has a QWERTZ keyboard and a missing 'n' key haha.

Now onto my problem. Basically, I#ve had my HP Pavillion g6 for about 9 months now and I've been using ubuntu 11.10 perfectly on it for about 3 months. Last night I was using it fine and it shutdown with no problems. When I went to use it today the screen went to a blank black screen. I waited a while then decided to restart. 

When it restarted it brought up my GRUB menu instead, so I decided I should try safemode since this usually doesn't happen. It does the usual loading but when intrid.lz finishes and states 'ready' the laptop goes black again and displays random information regarding my CPU. I thought it might be that the CPU is screwed but then decided that it wouldnt really be getting this far if it was? 

I have tried booting previous linux versions, run not in safe mode and run from my boot disk and usb. The only thing I havent done is trz to run windows simply because I dont have it. All of these approaches either result in a totally black screen with a flashing cursor or the previously mentioned cpu information.

Any help at all would be greatly appreciated,
Aracanid

---

### Post by hakermania on 2012-07-08
It totally looks like this:
[http://askubuntu.com/questions/92344/ubuntu-11-10-black-screen-with-blinking-cursor-on-boot](http://askubuntu.com/questions/92344/ubuntu-11-10-black-screen-with-blinking-cursor-on-boot)
A friend of mine 3 days ago had exactly the same problem and I helped her (through the phone, while she isn't good at all with PCs). We actually did the following:

I told her to download TinyCore (because it's only 12 MB), it burned it into a USB with UNetbootin (she has dual boot in her PC, so she downloaded and made the bootable USB through windows), then boot from it and do the following:
```

sudo fdisk -l

```
to list your partitions. See which from those corresponds to your linux installation and also see what is the corresponding file to it (/dev/sdaX, where X is a number).
Then:
```

sudo fsck -f /dev/sdaX

```
where /dev/sdaX is the file you noticed before.

It worked perfectly fine for her, and she had exactly the same problem with you.

---

### Post by aracanid on 2012-07-08
running from a USB causes the error screen to appear :?

one sweep of memtest has finished and its reporting 4mb of bad RAM. Im assuming thats me screwed unless I buy more RAM then?

---

### Post by aracanid on 2012-07-08
I decided to try running tinycore anyway but still a blinking cursor. I think its the RAM for sure, I'll change this to solved. Thank zou for your help anyway :)

---

