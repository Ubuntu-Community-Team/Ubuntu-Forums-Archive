---
title: "Can't boot after fresh install"
date: 2012-03-09
forum: General Help
---

### Post by corbino91 on 2012-03-09
I just did a clean install of ubuntu 11.10 and now it wont boot. I know the issue is the video card, i have a gtx 570. I know its the video card because i have done an install with my older video card and it worked.

So as of now i can only get to the command line, i can't get it to fully boot, but everything in the command line works fine.

Can i install the proper nvidia driver from the command line so that I am able to boot up, or do i neeed to do something else?

I have done many installations in the past so im fairly confident that i didnt make any mistakes.

I have now tried ubuntu, mint, and openSuse. I cant get any of the to install easily with my video card, if i cant get it going, im just going back to windows.

thanks

---

### Post by Perfect Storm on 2012-03-09
Try this, it will install the latest nvidia driver;

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install nvidia-current
```

reboot

---

