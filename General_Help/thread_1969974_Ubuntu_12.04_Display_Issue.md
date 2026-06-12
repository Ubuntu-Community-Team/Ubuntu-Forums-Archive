---
title: "Ubuntu 12.04 Display Issue"
date: 2012-04-30
forum: General Help
---

### Post by RevJack on 2012-04-30
I'm trying to run the 64-bit Ubuntu 12.04 in live mode before considering installing it. It does not seem to like my NIVIDIA card, as this is what the display looks like when trying to load the live dvd.

[http://img.photobucket.com/albums/v462/revjackhowell/ubuntu12_04.jpg](http://img.photobucket.com/albums/v462/revjackhowell/ubuntu12_04.jpg)

My card is the NVIDIA GForce GT 425M. How can I get Ubuntu 12.04 to recognize the card when booting in live mode?

---

### Post by Lamukra on 2012-04-30
there should be a choice in the menu that pops up before actual boot to live session, try to choose nomodeset 
Look at this thread, I hope it will help!
:)

---

### Post by Lamukra on 2012-04-30
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Here is the thread :)

---

### Post by RevJack on 2012-04-30
Thanks! That did the trick! Now, how do I modify GRUB with nomodeset after installing so I can get the desktop, and also, how do I install the NVIDIA drivers for my card after I install Ubuntu 12.04?

---

### Post by pqwoerituytrueiwoq on 2012-04-30
live usb i suggest making it with unetbootin so you can use the edit option on the boot line and nomodest the live session (i had to do this to install 12.04)

---

### Post by codingman on 2012-04-30
If you're question has been answered, please set this thread as solved by going to thread tools and selecting "set this thread as solved" =P~

---

### Post by jim_deadlock on 2012-04-30
This is a common problem, I had it too. After you log in and install your Nvidia drivers you will no longer need to set nomodeset, it will all work fine. Most likely you'll be prompted to install the drivers automatically a few minutes after you log on, if not just run jockey-gtk

---

