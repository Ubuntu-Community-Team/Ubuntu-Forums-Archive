---
title: "Getting online with my WiFi card..."
date: 2006-02-10
forum: General Help
---

### Post by BlacKoffee on 2006-02-10
KAy, so I installed my Belkin F5D7000 card in my tower, and it's registering it. I'm connected to my wireless network and I can transfer files from computer to computer, but when I open Firefox, it doesn't find any internet. I get the "www.google.com cannot be found." message.

What do I need to do?

|<0ff33

---

### Post by Leiki on 2006-02-11
I had the same exact problem. This should help you out:

Go here: [http://sourceforge.net/project/showfiles.php?group_id=132677&package_id=145736&release_id=362223](http://sourceforge.net/project/showfiles.php?group_id=132677&package_id=145736&release_id=362223)

And download the deb file. After that, cd to the file location in your terminal and type in 
```
sudo dpkg -i gtkwifi-1.09.deb
``` to install it. Then, to run it, type ```
gtkwifi "run-in-window"
```. It will show a small window, click on that to view available wireless networks. Click connect and you're done! Goodluck!

P.S. - Thanks byen! ;)

---

