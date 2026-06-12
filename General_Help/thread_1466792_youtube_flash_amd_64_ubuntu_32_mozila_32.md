---
title: "youtube flash amd 64 ubuntu 32 mozila 32"
date: 2010-04-30
forum: General Help
---

### Post by tgomly on 2010-04-30
hi. I have very big problem. can't watch video from youtube. Hello, you either have JavaScript turned off or an old version of  Adobe's Flash Player. [Get  the latest Flash player]("http://www.adobe.com/go/getflashplayer/"). 		

I was upgraded Ubuntu form 9.10 to 10.04 and can't watch video.
I tried 5 or maybe 6 options and no one work. When I tried to install recommended version at that link...system write me that I have AMD x64 processor and I can't install it even I have Ubuntu 32bit and Mozilla 32bit . I'm not sure if I have Ubuntu 32bit and Mozilla 32bit because of update Ubuntu. Where can I find which version I have. and how can solve the problem.

Please help me.

---

### Post by tgomly on 2010-04-30
PS. Problem have even with Galeon

---

### Post by pqwoerituytrueiwoq on 2010-04-30
install flash manually 
64bit
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)
32 bit
[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc2_linux_041910.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc2_linux_041910.tar.gz)
extract to /home/tgomly/.mozilla/plugins/
*assumed your login name is tgomly*

---

### Post by oldos2er on 2010-04-30
Open a terminal and run ```
uname -a
``` to see if you're running 32- or 64-bit. Either way you can use this script to install: [http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595)

---

### Post by tgomly on 2010-04-30
Thanks you save my life :D work with 64 and that comand " sudo cp /home/gomly/Downloads/libflashplayer.so /usr/lib/mozilla/plugins" 

and before that I removed file in mozilla folder.

---

