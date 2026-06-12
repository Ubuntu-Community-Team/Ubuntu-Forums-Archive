---
title: "Computer refuses login and password."
date: 2010-12-25
forum: General Help
---

### Post by Cheetah1933 on 2010-12-25
I am running version 10.10 on an HP envy 14.

I just updated the drivers for the video cards, and after I installed them, I was prompted to login to the system. I entered my username and password, and a few seconds later the prompt said "incorrect login" and gave me the same prompt over and over again. I KNOW I'm using the right ID and password, so why isn't it working? How can I get around this?

Specs:[SIZE=2]ATI Mobility Radeon 5650
[/SIZE]500GB (7200RPM) Hard Drive (SATA)
Intel Core i5-450M processor 2.40GHz with Turbo Boost Technology up to 2.66 GHz
4gb of ram
Ubuntu 10.10

---

### Post by Cheetah1933 on 2010-12-26
<snip>

---

### Post by Cheetah1933 on 2010-12-26
<snip>

---

### Post by Cheetah1933 on 2010-12-26
bump. Im booting from a USB now. Can anyone walk me through what I need to do to fix it?

---

### Post by karthick87 on 2010-12-26
Try resetting your password to a new one,

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Cheetah1933 on 2010-12-26
That worked, thank you very much. I am still left without a GUI because it did not recognize the video card after the new drivers. Is there something I can do to fix this?

---

### Post by karthick87 on 2010-12-26
On booting hold down the shift key and the grub menu will appear.The Ubuntu system should be highlighted on the menu. You should press the "e" key and on the new screen navigate to the end of the line that says "quiet splash" and remove those words and replace them with "nomodeset" - without the quotes - then press ctrl + X to reboot.

---

### Post by Cheetah1933 on 2010-12-26
I did that, and it takes me to the same prompt page I was at before. What else do I need to do?

---

### Post by karthick87 on 2010-12-26
Pls wait for another member to look at this thread for giving a better suggestion..

---

### Post by Cheetah1933 on 2010-12-26
Okay, thank you for your help.

---

### Post by coffeecat on 2010-12-26
When you say you updated the video driver, do you mean:

1 - you already had the proprietary fglrx driver installed, but you updated it from System > Adminstration > Additional Drivers.

or

2 - You had previously installed the proprietary catalyst driver from the ATI website and you updated this with another download.

or

3 - You were running with the open-source ATI driver and you replaced it by installing the proprietary driver either from a download or from Additional Drivers.

?

Whichever, if you are running a proprietary driver and this has broken the GUI, it would be a good idea to revert to the open-source driver, at least to get you back to a GUI. Have a look here:

[https://help.ubuntu.com/community/RadeonHD#Preparation](https://help.ubuntu.com/community/RadeonHD#Preparation)

You just need the bit under 'Preparation'. It gives console commands to purge the proprietary driver from either source.

If that works, you might want to consider whether or not to use the proprietary driver again. With my Radeon 4200 and 4350 cards I'm better off with the open-source driver. I wouldn't touch the fglrx one with a proverbial barge-pole. But I don't know what the situation with the Radeon 5650 card is though.

**EDIT**: forgot one important thing which is missing from that now unmaintained link. You need to disable the xorg,conf file before the OS ati driver will work. From the console:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

---

### Post by Cheetah1933 on 2010-12-27
Thanks for the help guys. Apparently Ubuntu doesn't support switchable graphics by default and so the driver screwed up the system. I ended up reinstalling the system, for an unrelated error, and the fact that windows 7 was partitioned wrong and so I had 200gb of deadspace on my harddrive. I also found a kernal that should let me use switchable graphics, which I'll try out tomorrow. I really appreciate the help, especially with how new I am to the operating system.

> **Lotuscather said:**
> [LEFT][LEFT]1. Try No Password Administrator Login Backdoor- In Windows XP there is built in administrator user account that has administrator credentials, enabled by default and without any password to protect the account from been access. If you didn’t change the administrator’s password, then try to sign in to Windows XP without password. 
2. Reset password from another user account with administrator credentials.

[/LEFT]
[/LEFT]
    [LEFT][LEFT]If you are unable to find your lost password from the above listed methods then you can opt for the [windows password reset]("") tools. When I have met such situation, I adopt recommendation of downloading Windows Password Reset Tools online from [URL]  [/LEFT]
[/LEFT]

I'm running Ubuntu 10.10 Maverick Meercat, not Windows XP. Not to be rude, but please read the original post.

---

