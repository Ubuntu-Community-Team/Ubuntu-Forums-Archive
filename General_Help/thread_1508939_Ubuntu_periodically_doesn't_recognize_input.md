---
title: "Ubuntu periodically doesn't recognize input"
date: 2010-06-13
forum: General Help
---

### Post by alem189 on 2010-06-13
I have an Ubuntu 10.04 installation that I have been using for about a month. However, just recently, at random times for about 5 seconds I can't use my mouse or keyboard. When it does that, the computer isn't frozen, I just can't type. About 5 seconds later, all the text that I was trying to type suddenly appears. I have 4GB or RAM, and even when I barely have any programs running and at 0% of resource usage, the problem still persists. This has just been happening for the past day or so. Does anyone know any reasons why this might be happening?

---

### Post by ddrichardson on 2010-06-13
Mine does it too, it seems in my case to be related to the pointer being near the notification area. Its only been in the last few days and it hasn't happened regularly enough for me to gather information for a bug report.

---

### Post by efflandt on 2010-06-13
That is unusual be Linux is usually very good at dividing up time slices for multitasking.

Are you running any other programs that you know of at the time, anything in the background, or associated with disk access?

I have one old laptop that seemed to drop some keyboard characters (made sudo difficult), mousepad would get jumpy in 9.10 due to delayed input at times (especially just after booting), and it would not wake from suspend or hibernate (black screen).  But that is much improved in 10.04 with rarely any dropped keys, only occasional jumpy mousepad, and suspend works.

However, in your case the keyboard buffer appears to be accepting input, it is just not getting to your application promptly.  Something must be hogging your cpu during that time.  You might either try seeing if System Monitor may give a clue what program might be hogging resources, or the **top** command in a terminal.

---

### Post by alem189 on 2010-06-16
I figured out what was causing the non responsiveness. There is evidently some kind of problem with my BCM43xx wireless driver. This is the error I get in my syslog, every ten seconds:

```
Jun 15 22:45:25 oxurtia kernel: [ 1333.931177] b43-phy0: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
Jun 15 22:45:25 oxurtia kernel: [ 1333.931187] b43-phy0: Controller RESET (DMA error) ...
Jun 15 22:45:25 oxurtia kernel: [ 1333.931213] Controller restarted
Jun 15 22:45:25 oxurtia kernel: [ 1333.931241] b43-phy0: Controller RESET (DMA error) ...
Jun 15 22:45:26 oxurtia kernel: [ 1334.260283] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
```

When it happens corresponds with when I can't type. I haven't had any Internet connection for a while, either, but I thought that was a problem with the router.

How do I fix this? I'm not sure how to reinstall the driver. Also, should I start a new thread about this, or keep this one?

---

### Post by ddrichardson on 2010-06-16
I'd report it as a bug.

---

### Post by alem189 on 2010-06-17
Okay, I figured out how to reinstall the driver, and I'm not getting the input problem anymore, but I still can't connect to the internet. Since that's a different problem, though, I should probably mark this as solved.

---

