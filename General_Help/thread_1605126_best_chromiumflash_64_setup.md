---
title: "best chromium/flash 64 setup?"
date: 2010-10-24
forum: General Help
---

### Post by northwestuntu on 2010-10-24
i have ubuntu 10.10 64 bit.  i installed chromium from ubuntu repo, but would i be better off using chromiums repo?  more options and updated more?  also why is it so hard to find chromiums repo? ive ran across it before, but very hard to find.

now for 64 bit flash.  i installed flash from ubuntu repo and i would assume it's the 32bit? i do i verify i have 64bit.  when i go to the about page it says chromium takes care of it :mad:

---

### Post by Sef on 2010-10-24
> i have ubuntu 10.10 64 bit. i installed chromium from ubuntu repo, but would i be better off using chromiums repo? more options and updated more? also why is it so hard to find chromiums repo? ive ran across it before, but very hard to find.

Was not hard for me. I just did a search for it in Ubuntu Software Center. 

If you want more bleeding edge, you can use the [PPA]("https://launchpad.net/~chromium-daily/+archive/ppa").

---

### Post by northwestuntu on 2010-10-24
> **Sef said:**
> Was not hard for me. I just did a search for it in Ubuntu Software Center. 

If you want more bleeding edge, you can use the [PPA]("https://launchpad.net/~chromium-daily/+archive/ppa").

i meant trying to find chromiums repo.  no problem finding chromium in the software center.  im confused though? there are 2 chromium repos? one that ubuntu runs?

---

### Post by oldos2er on 2010-10-25
You can search PPAs for "chromium" here: [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

64-bit flash is here: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz)
You will need to uninstall 32-bit flash first. To install 64-bit flash, un-tar the tar.gz and copy libflashplayer.so to ~/.mozilla/plugins
When you install chromium, it should find flash automatically.

---

### Post by TBABill on 2010-10-25
Sounds like you want the daily PPA for Chromium. Yes that is different than Ubuntu's repository. The daily gives you the latest and greatest, but often there are small issues that cause problems. For example, on one of the daily updates I lost all ability to use codecs. The next day it was fixed. The version in Ubuntu's repo is stable and fairly up to date. (just a few weeks I think)
 
What capability would a daily or weekly update actually give to you that the repo version does not? I'm just curious what is motivating the desire.

---

### Post by northwestuntu on 2010-10-28
> **TBABill said:**
> Sounds like you want the daily PPA for Chromium. Yes that is different than Ubuntu's repository. The daily gives you the latest and greatest, but often there are small issues that cause problems. For example, on one of the daily updates I lost all ability to use codecs. The next day it was fixed. The version in Ubuntu's repo is stable and fairly up to date. (just a few weeks I think)
 
What capability would a daily or weekly update actually give to you that the repo version does not? I'm just curious what is motivating the desire.

well i was looking to try out version 7.  still on 6 now.

---

### Post by northwestuntu on 2010-10-28
> **oldos2er said:**
> You can search PPAs for "chromium" here: [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

64-bit flash is here: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz)
You will need to uninstall 32-bit flash first. To install 64-bit flash, un-tar the tar.gz and copy libflashplayer.so to ~/.mozilla/plugins
When you install chromium, it should find flash automatically.

hmmmm what about this?

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

never mind they both seem to host the same file.  it still reads out of the mozilla folder? i wonder why they don't have it where it reads out of the chromium folder?

---

