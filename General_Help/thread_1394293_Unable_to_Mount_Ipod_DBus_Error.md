---
title: "Unable to Mount Ipod DBus Error"
date: 2010-01-30
forum: General Help
---

### Post by diandoo on 2010-01-30
I've had my Ipod working fine using both Rhythmbox and gtkpod until a few weeks ago. Now, I can't get my Ipod to mount. My external hard drive mounts fine, just not the Ipod. When I plug it in I get the following message: 

"DBus error org.gtk.Private.RemoteVolumeMonitor. Not Found: The given volume was not found"

I've tried to manually mount it and that doesn't work. I updated from Jaunty to Karmic hoping that would solve it. It didn't. 

Can anyone help?

---

### Post by diandoo on 2010-02-03
No one has suggestions? 
It's a 4th gen nano that was working flawlessly until about a month ago. This is really frustrating. I have no idea how to fix it.

---

### Post by tagawa on 2011-01-14
I know it's nearly a year later but for other people who may have this problem, this blog post fixed it for me: [http://ubuntu-install.blogspot.com/2010/12/iphone-42-in-ubuntu.html](http://ubuntu-install.blogspot.com/2010/12/iphone-42-in-ubuntu.html)
(I didn't have to restart my system for it to work)

---

### Post by dentman on 2011-06-10
Unable to mount iPhone_ org.freedesktop.DBus.Error.NoReply DBus error: MESSAGE DID NOT RECEIVE A REPLY (TIMEOUT MESSAGE BY BUS)
 

This is how to fix it:
 
Open your terminal and copy/paste the following:

sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade

 

restart REBOOT your system and mount your Iphone without problems. 

Thanks to :KS Jeroen :KS
from
[http://ubuntu-install.blogspot.com/2010/12/iphone-42-in-ubuntu.html](http://ubuntu-install.blogspot.com/2010/12/iphone-42-in-ubuntu.html)

---

