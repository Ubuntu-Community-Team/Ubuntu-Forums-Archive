---
title: "Updating Wine"
date: 2006-02-20
forum: General Help
---

### Post by Timokl on 2006-02-20
I installed Wine 0.9.7 on my Ubuntu Linux 5.10 laptop. Today, I was about to receive an update to Wine 0.9.8.

However, I read on [http://www.winehq.com/site/howto](http://www.winehq.com/site/howto) that you have to remove Wine before upgrading. Is this being done automaticely during the update process? Or do I have to remove Wine manually. If so, how do I do it. This how-to ([http://www.winehq.com/site/docs/wineusr-guide/installing-wine-source#UNINSTALLING-WINE-SOURCE](http://www.winehq.com/site/docs/wineusr-guide/installing-wine-source#UNINSTALLING-WINE-SOURCE)) just gives details on removing the source version. As I installed the binary package of Wine, I am not sure how to remove Wine.

---

### Post by sbassett on 2006-02-20
sudo dpkg -r wine

then

sudo apt-get install wine

then 

winecfg

Should set you up fine.

---

### Post by Timokl on 2006-02-20
Thnx, that did the trick. :)

---

