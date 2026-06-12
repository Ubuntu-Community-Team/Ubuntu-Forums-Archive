---
title: "New service start/stop in lucid"
date: 2010-08-28
forum: General Help
---

### Post by NiksaVel on 2010-08-28
Hi guys,

I have big problems since moving to lucid... I feel like I'm working in a new OS alltogether...  some things have obviously changed and I need some help to catch up pls

1. how to restart alsa?  I used 
```
/etc/init.d/alsa-tools restart 
```  
it no longer works...

2. how to stop/start gdm ?
same as above...

3. How to install latest NVIDIA driver?
I need to stop GDM for that but I don't know how...   also after installing the regular one from driver manager I got dropped to low res...  tried to open nvidia-settings and it said that I am not running an nvidia driver..!???!!!??

---

### Post by t.rei on 2010-08-28
Hi there. 
You will find that 'the way it works now' is:
```

sudo service gdm stop
sudo service gdm start

```

I honestly haven't messed with alsa in ages. So I don't actually know. Have you installed 10.04? In that case I suggest looking into pulseaudio.

The nvidiadrivers I use with great success are the ones from 
[http://www.nvidia.de/Download/index.aspx?lang=en](http://www.nvidia.de/Download/index.aspx?lang=en)
but as you said, you need top stop gdm, or run it with the "ignore checking for running x option" wich is just bad. ;) 

Hope I could help a little

---

### Post by 3rdalbum on 2010-08-28
Ubuntu no longer uses the old Init scripts. It has transitioned entirely to Upstart as the bootup/init system. It allows for a faster, more flexible bootup. Funnily enough there's little mention of it in the release notes.

To stop GDM you now use:

```
sudo service gdm stop
```

And, of course, to restart it:

```
sudo service gdm start
```

The alsa-tools service does not seem to exist, so I don't know how to answer your first question. But it should probably involve the 'service' command rather than the old init scripts.

---

### Post by NiksaVel on 2010-08-29
Hi guys,

thanks for the reply guys, for some reason I can now stop GDM...  I could swear I was using the same command before...

Anyhow... still no go on the NVIDIA driver install...  I have the latest driver downloaded... stopped gdm...   but now it says that I need to blacklist the nouveau driver..

I have found posts depicting how to do that...

i.e. [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

> gksudo gedit /etc/modprobe.d/blacklist.conf

Add these lines and save:

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv


but nothing changes...  as if I have not done that at all...   is the driver called something different now... or in the 64 bit edition?

(of course I did reboot...   it booted normally right back to gdm....)

---

