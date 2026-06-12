---
title: "install Ubuntu"
date: 2011-04-13
forum: General Help
---

### Post by Gr72 on 2011-04-13
Hello, 
I am a newbie when it comes to linux. About a year ago I installed Ubuntu into a dual boot with winows 7. I accidentally deleted the Ubuntu partition from within windows and left it. After a registry error in the  windows partition I re-installed windows over everything and has been working fine. But, now I am getting back into linux and have been trying to install Ubuntu ans use a Backtrack liveCD but I can't and recieve this error:

Buffer I/O error on device sr0, ;ogical block 993427
Buffer I/O error on device sr0, ;ogical block 993428
Buffer I/O error on device sr0, ;ogical block 993427
Buffer I/O error on device sr0, ;ogical block 993428

SQUASHFS error: squashFs_read_data failed to read block 0x7583e78f
SQUASHFS error: unable to read id index table

BusyBox v 1.10.2 (Ubuntu 1:1.10.2-1 Ubuntu7) built in shell (Ash)
Enter 'Help' for list of built in commands




If Any one can help me with this, that would be great, I have been picking my brains over this and have googled it but have come up with nothing. Thanks

---

### Post by Gr72 on 2011-04-13
sorrt those ";" in the coding are supposed to be "l"'s

---

### Post by MarkVS on 2011-04-13
I'm no expert, but it looks to me like the cd has gotten corrupted. This could be caused by age or a scratch. How old is the CD? If it is corrupted, you should just be able to burn a new one. And if you tell us exactly when you got the error, it would help.

---

### Post by K_45 on 2011-04-13
Compare the MD5SUM hash to the CD here:  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Hedgehog1 on 2011-04-14
Gr72,

Please download the ISO for Ubuntu again, this time using a Bit Torrent client so you can get an error-checked download.

Then, burn a new CD or DVD from the ISO using the slowest speed your burning software allows.

Once you are able to boot from the LiveCD, you can reinstall Ubuntu.


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-14
Gr72
> (from your PM) Thank You, After I re-install will I be able to boot my BaackTrack cd without any Busy Box Problem?

We need to get a look at what your system looks like now.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by Gr72 on 2011-04-14
Thanks, 
I'm going to re-download the ISO now. I Will try it. After I re-install and it boots correctly, will I be able to still boot BackTrack w/o the busy box coming up?
Thank You

---

### Post by Gr72 on 2011-04-14
Would completely Erasing my Hardrive get rid of the busy box boot? and If so, how can I do that?

---

### Post by Hedgehog1 on 2011-04-14
> **Gr72 said:**
> Would completely Erasing my Hardrive get rid of the busy box boot? and If so, how can I do that?

If the issue is a bad ISO, then erasing the hard drive won't solve that.  

We can help you make a more controlled install of Ubuntu (once we see the script output and figure our where you PC is right now).

***The Hedge***

:KS

---

### Post by Gr72 on 2011-04-14
Thanks, Ubuntu now is bootable on a partition, thank you. I never thought that it was just a bad iso... thank you all

---

### Post by Hedgehog1 on 2011-04-15
> **Gr72 said:**
> Thanks, Ubuntu now is bootable on a partition, thank you. I never thought that it was just a bad iso... thank you all

Hurray!  You are back up!!! ***Hedgie Happy Dance***!!!



***The Hedge***

:KS

---

### Post by Gr72 on 2011-04-18
Nice, Ubuntu Works fine except for WiFi.... but when I try to boot my backtrack Live Cd or Linux Mint I get the same error.... any thoughts?

---

### Post by K_45 on 2011-04-19
Post the output of

```
sudo lshw -C network
```

---

