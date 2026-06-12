---
title: "download adobe flash player"
date: 2010-12-06
forum: General Help
---

### Post by zainlodhi on 2010-12-06
I have a Ubuntu(64-bit) installed on my PC. I am new to Linx and as that there are several versions of adobe flash player (such as YUM, .rpm, .deb) available for 64-bit Linux. I want to know that which  version is suitable for 64 bit Ubuntu so my browser wiould be able to run the youtube videos.

---

### Post by thinkinhurtz on 2010-12-06
If you go to the adobe official site the default deb file works fine. Aside from that whatever you get from the Ubuntu Software Center should be compatible with the 64 bit version if that is what you are using, and that version is available.

---

### Post by TBABill on 2010-12-06
The repo (ubuntu-restricted-extras) gives you what you need for videos. However, you end up with 32 bit flash in a 64 bit OS. Not a big deal at all, but to fix it the easiest thing I have found is to add the extension for Firefox called FLASH-AID. What it does is each time you open Firefox it looks to see if you have the correct (32 or 64 bit, depending on the OS) version of Flash and if it is the most current (from Adobe directly). If it is not, it prompts you to update and it takes care of the rest. It's wonderful and so simple. Just click in Firefox edit>>preferences>>manage addons and then when the small add on box opens, just click add ons, browse more addons. That should open the website and all you have to do is search for "flash aid" and install it. Close Firefox, restart it and let it do its thing.
 
Great tool created by Ubuntu user LovingLinux!
 
On a side note, anything you install into Ubuntu normally will come from the repos, from a .deb file (stands for Debian, on which Ubuntu is based) or a tar.gz file (like a zip file in Windows).

---

### Post by oldos2er on 2010-12-06
+1 for Flashaid. Here's a direct link: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Spyderkid on 2010-12-06
go to the software centre and download ubuntu-restricted-extras, or jsut flash 10

---

### Post by TBABill on 2010-12-06
ubuntu-restricted-extras only installs the 32 bit. I think the OP was more wanting to have 64 bit flash in the end.

---

### Post by ottosykora on 2010-12-06
at adobe site I found only some kinf of *.bin file, no deb file. How is this bin file to be used?

---

### Post by oldos2er on 2010-12-06
Again, it's easiest to use [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

But if you're determined to do it manually, [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)

---

### Post by Vaphell on 2010-12-06
[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)

unpack, move libflashplayer.so to /usr/lib/mozilla/plugins
OR
install FLASH-AID plugin for firefox mentioned above that automates the procedure

---

