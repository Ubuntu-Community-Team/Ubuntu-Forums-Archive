---
title: "USB Autometically Unmounting"
date: 2009-07-06
forum: General Help
---

### Post by asamay81 on 2009-07-06
A peculiar problem again after I have updated ubuntu. I am using Ubuntu 9.04 in my desktop. One 320 GB SATA External HDD is connected to my PC through a USB cable. After I have updated Ubuntu two days back, what is happening is, the USB is autometically unmounting after some time and upto next restart it is not being mounted. It is really annoying. 

One more problem. Before I updated, my external drive was copying any file from my PC ~ 15-27 MBps, but now I am getting only ~ 2-3 MBps transfer rate.

Is it any problem with Ubuntu? Is there any way to get rid of this situation?

Waiting for your responses

Thanks

---

### Post by Jebtrix on 2009-07-06
After the problem occurs try:

```
sudo /etc/init.d/udev restart
```

Does that help? If not try:

```
sudo /etc/init.d/hal restart
```

Did that help? At least maybe this way will find which one is causing problems and can narrow the search...

---

### Post by asamay81 on 2009-07-13
thanks a lot jebtrix for your reply...but the situation did not improve...in these days i was observing...when it was unmounted, i was running these commands but the situation remain same

---

