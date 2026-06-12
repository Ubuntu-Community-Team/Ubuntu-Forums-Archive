---
title: "noob to Ubuntu"
date: 2009-10-30
forum: General Help
---

### Post by darkshadow14875 on 2009-10-30
Hi I'm new to Ubuntu, and I'm trying to install Adobe flash and it wont work, also the  movie player wont play any videos and I can't download any other applications. I have Ubuntu 9.10, any help would be great.

---

### Post by celtic426 on 2009-10-30
For flash:
Go here - [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")
Open the dropdown box and select ".deb"
Open that file with the default app and it should install pretty easily.

For movie/audio:
Go to accessories and open up the terminal, then type this in:
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly mplayer w32codecs libdvdcss2

For installing software:
What do you mean you can't install new software?  Is there an error?
You can try this site for easily downloading and installing new software: [http://www.getdeb.net]("http://www.getdeb.net")

---

