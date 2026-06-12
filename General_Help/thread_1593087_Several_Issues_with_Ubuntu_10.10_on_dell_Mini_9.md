---
title: "Several Issues with Ubuntu 10.10 on dell Mini 9"
date: 2010-10-11
forum: General Help
---

### Post by psypher on 2010-10-11
Hi All,

Before logging a bunch of bugs I wanted to post all the issues I have since freshly installing Maverick Meerkat today on my Dell Mini 9.

1. This issue has been plaguing me since Karmic Kaola and its still not fixed. I only have a 4GB SSD drive in my Dell Mini. Every time I boot up I get an error saying my hard disk is going to fail and "Is being used outside design parameters"

My disk is NOT going to fail and this is a "fail" on the app's part. Its complaining about the size of the disk. You would think a disc which is larger than the recommended disk size would not bring up such a worrying error. I have to go into the app and tell it to stop warning me if this drive is failing. What is my drive is really failing, now I will not get the notification.

2. Unable to install broadcom drivers from the proprietary app at all, when I try I get error :"SystemError: installArchives() failed"

Same thing, since Karmic, Ubuntu cannot get the Broadcom drivers to install properly on a flagship Dell Ubuntu device. Very disappointing.


Does anyone know what are the 2 applications I should log these bugs under?

I think the one is gnome-disk-utility but not sure what the drivers app is.

Thanks

---

### Post by I2v8an on 2010-10-14
> 2. Unable to install broadcom drivers from the proprietary app at all, when I try I get error :"SystemError: installArchives() failed"

I just had the same problem with installing sta driver.  I think it can be solved by reinstalling the package bcmwl-kernel-source or running:
dpkg-reconfigure bcmwl-kernel-source

---

