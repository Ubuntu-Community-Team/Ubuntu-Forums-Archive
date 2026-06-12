---
title: "USB speed falsely very high on Ubuntu 12.04  !!!"
date: 2012-05-18
forum: General Help
---

### Post by masterserver on 2012-05-18
Hi to everyone.

I want to share a feedback issue that I receive form my Ubuntu and to see if it is only me that I receive that or it is a general issue.

I plug my USB flash drive to my USB port and when I attempt to copy data to my flash drive ( a movie for example) the progress window shows an amazing writing speed of 40MB/s. I assure you my USB flash drive has only 5 MB/s writing speed. So when the progress bar fills up it stops just a little bit before the end. For example I was transferring a movie of 716MB and the progress bar stopped at 715MB without giving any feedback. So, in the beginning for a few times i was just cancelling the copy progress because i was thinking that it has crashed but after I while I decided to leave it there and see what happens. 

What I realized??? 

The copy progress is performed with the normal writing speed of 5MB/s approximately (despite the fact that Ubuntu shows 40MB/s) and the copy progress continues after the progress bar has reached the end. As a result, when i was copying the movie to my flash drive the progress bar reached the end in just 10 secs but it remained frozen for the rest 2 minutes until the copy was finished.

Does anyone else has faced this issue on his system or it is just my system's fault?

Thanks for reading

(And excuse my bad English, I am not a native speaker...)

---

### Post by 2F4U on 2012-05-19
Personally, I never saw such a behaviour on my system, except, maybe, on Windows systems. Does that happen just with one particular usb flash drive? What USB specification does your hardware (computer and flash drive) support?

---

### Post by carl4926 on 2012-05-19
It may be related to that the system will  hold writes until the buffer has flushed

---

### Post by masterserver on 2012-05-19
2F4U this happens with both of my USB flash drives (One of them actually is a microSD USB adaptor with an 8GB microSD card in it). 

The other one with which I faced this issue yesterday is an Kingston Datatraveller 108 16GB USB2.0 read=16MB/s write=6MB/s

About my laptop now, I don't know exactly how to check the specs of my USB ports. I run this command ```
lspci -vv | grep USB
``` and I got this as result


```
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
0b:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
```

So, I assume that I have USB2.0 and 3.0 ports, right?
If you know a better way to check the USB ports specs please share it.

> It may be related to that the system will hold writes until the buffer has flushed

carl4926 I understand what you are saying but why my system shows a writing speed of 40MB/s?

---

