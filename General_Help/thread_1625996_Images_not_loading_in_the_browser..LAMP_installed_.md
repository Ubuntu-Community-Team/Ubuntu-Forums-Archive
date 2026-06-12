---
title: "Images not loading in the browser..LAMP installed in ubuntu 10.04"
date: 2010-11-19
forum: General Help
---

### Post by ishwor123 on 2010-11-19
Hi!
I have installed LAMP server in ubuntu 10.04 using sudo tasksel command @ my home and with all the port forwarding and stuff its working fine and i can access it via internet and images load fine, but when i installed LAMP using same exact same command @ my friends place and proper network configs, the php pages load but the images don't load. 
(Images which are very small in size like less then 5 kb is loading though, like small icons, smileys...)
Tried clearing cache, different browsers, different image formats...
Anybody can point me what might be wrong?

Thanks!

---

### Post by Kulshrax on 2010-11-19
Hmm, that is strange. Are the images in question embedded in a webpage? If so, can you access the images directly, or do they still not load?

Are you accessing these pages on the LAN, or are you connecting to the server using the outward facing address? If it is the latter, the router or some other piece of networking equipment may be filtering out the images.

Otherwise, there may be a config issue, or some other problem. More information would be helpful.

---

### Post by ishwor123 on 2010-11-20
Hi!
Thanks for the reply. The images are embedded in  the webpage, however i also put different types of images on www folder to try if it loads and its the same issue (in chrome it tries to download the image file and in firefox it says "The image "http://xx.xxx.xx.xxx/test.png cannot be displayed, because it contains errors"). I am trying access the webpage/images via public IP address now (port forwarding in the router). Yesterday i was in the place where the machine is located, but i didn't check the webpages or images in the localhost,.. coz i think if the images load fine in the localhost then i could rule out the chance of PHP..LAMP not being properly installed and could start to look at the networking devices.
Am i going in the right direction here? :)
I'll be there on Monday and check, and let you, probably i could get some help if it is config issue.

Thanks a lot.

---

