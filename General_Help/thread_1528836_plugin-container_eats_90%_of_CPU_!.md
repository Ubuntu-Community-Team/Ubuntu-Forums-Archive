---
title: "plugin-container eats 90% of CPU !"
date: 2010-07-11
forum: General Help
---

### Post by tavis008 on 2010-07-11
Hi all,

few days ago, probably after my Ubuntu (10.04) updated Firefox to 3.6.6, I find my system unusable. Usually, after some time of running, the CPUs are used of about 90 - 99 %. It seems that the cause is the plugin-container in Firefox 3.6.6. Output of 'top' command (first few lines) ...

> top - 15:38:37 up 29 min,  2 users,  load average: 3.39, 2.72, 1.68
Tasks: 167 total,   3 running, 164 sleeping,   0 stopped,   0 zombie
Cpu(s): 80.4%us,  5.0%sy,  0.0%ni, 12.2%id,  0.0%wa,  1.1%hi,  1.3%si,  0.0%st
Mem:   2049856k total,   869252k used,  1180604k free,    49636k buffers
Swap:  3148732k total,        0k used,  3148732k free,   498868k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1770 tavis     20   0 98.1m  34m  15m S   80  1.7   8:50.16 plugin-containe
 1243 root      20   0 77436  52m  13m R   75  2.6   4:02.48 Xorg
 1906 tavis     20   0  2544 1232  924 R    5  0.1   0:03.27 top
 1887 tavis     20   0 50020  15m   9m S    3  0.8   0:08.56 gnome-terminal
 1724 tavis     20   0 31796  18m 4184 S    1  0.9   0:06.34 ubuntuone-syncd
 1590 tavis     20   0 21048  10m 8660 S    1  0.5   0:01.99 metacity
 1744 tavis     20   0  284m  99m  27m S    1  5.0   2:21.39 firefox-bin
    7 root      20   0     0    0    0 S    0  0.0   0:00.10 ksoftirqd/1
  344 root      20   0     0    0    0 S    0  0.0   0:00.52 scsi_eh_1
  851 root      20   0     0    0    0 S    0  0.0   0:00.65 iwlagn
Another CPU-consuming process is Xorg but I suppose it relates to the problem with plugin-container? 

The computer is not usable in this status - please help! I don't need the newest version of firefox, so maybe if somebody could just give me an advice how to down-grade?

Thanks a lot,
Vlasta

---

### Post by quimkaos on 2010-07-11
Probably is some Firefox plug in, in conflict with the las version of FF (3.6.6)...

1 - try disabling all plug in within Firefox, and re-enabling 1 by 1 until you find the one is cosing problems. then remove it or try finding an updated version of it.

2 - completly remove FF by uninstalling it using synaptic or using console and typing:

```
sudo apt-get purge firefox
```

After removing Firefox check if in your home folder there's a folder named .mozilla if so delete it (folders starting with a dot (.folder) are hidden, so on your file browser you have to press ctrl+h to unhidde them).
Then install Firefox again.

---

### Post by tavis008 on 2010-07-11
Thanks for your reply. Since the system was very slow, the first method you suggested wouldn't be very efficient. Eventually I decided to remove Firefox completely and install Google Chrome instead :) It's working so far without any problem :-)
Thanks ...

---

### Post by quimkaos on 2010-07-11
i had my hand full of head-hicks with FF, a few times with plugins other times with configurations, thou i need it to work, so i had to resolve the issues... the second method usually works like a charm, but you have to backup your bookmarks and any configuration you might need.

anyway Chromium/Google chrome is also a good browser!

---

### Post by mprokolo on 2010-08-21
Just a note it is probably the flash plugin. It goes up to 90% whenever I play a video or open a page with flash.

edit: i installed adobe-flashplugin now usage is around 30%. 
It can be done through adobes site (or in firefox: tools->add-ons->plugins->find updates)

---

### Post by nsznaj on 2010-10-12
Hi I have the same problem with pluguin containe. Want to purge firefox and then install it again.

How do I backup Firefox bookmarks and that stuff before uninstalling it? 

Cheers
Nahuel

---

### Post by johanneslandin on 2010-10-25
I did this on my 10.04 LTS LTSP Server:
```
sudo chmod 700 /usr/lib/firefox-3.6.11/plugin-container
```

Ugly, but it works for now.

---

### Post by adza on 2010-11-11
just found it was stumbleupon update that fixed this issue for me ;) hehe, i guess i could've removed SU...

---

### Post by coldraven on 2010-11-11
> **nsznaj said:**
> Hi I have the same problem with pluguin containe. Want to purge firefox and then install it again.

How do I backup Firefox bookmarks and that stuff before uninstalling it? 

Cheers
Nahuel


Read this [http://support.mozilla.com/en-US/kb/backing+up+your+information](http://support.mozilla.com/en-US/kb/backing+up+your+information)

---

### Post by 4ebees on 2010-11-28
> **tavis008 said:**
> Hi all,

few days ago, probably after my Ubuntu (10.04) updated Firefox to 3.6.6, I find my system unusable. 

<SNIP>

Another CPU-consuming process is Xorg but I suppose it relates to the problem with plugin-container? 

<SNIP>
Vlasta

Hi there,

A solution that appears (I've only just started using it :)) to work can be found here:

[http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins](http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins)

---

### Post by kuric on 2010-12-24
Thanks, 4ebees. Actually, it works.

Go to about:config and search for:
dom.ipc.plugins.enabled.libflashplayer.so (Adobe Flash)
dom.ipc.plugins.enabled.libnptest.so (NPAPI test plugin) 
Alternate them to false. 

You're done, no more plugin-container running separately and eating all the RAM.

---

### Post by Chazz44able on 2011-01-08
> **kuric said:**
> Thanks, 4ebees. Actually, it works.

Go to about:config and search for:
dom.ipc.plugins.enabled.libflashplayer.so (Adobe Flash)
dom.ipc.plugins.enabled.libnptest.so (NPAPI test plugin) 
Alternate them to false. 

You're done, no more plugin-container running separately and eating all the RAM.
Thanks for that, the same thing was happening to my system. That appears to have fixed it.

---

### Post by johanneslandin on 2011-01-23
I got a server with 2 old Intel CPU. I recommend both **Swiftfox** and **FlashBlock**:

Get Swiftfox designed for your CPU:
[http://getswiftfox.com/deb.htm]("http://getswiftfox.com/deb.htm")

Install Swiftfox:
sudo dpkg -i swiftfox-3.*

Replace Firefox binary with a hardlink to Swiftfox:
sudo mv /usr/bin/firefox /usr/bin/firefox3
sudo cp -l /usr/bin/swiftfox /usr/bin/firefox 

Flashblock (Will halt most Flash plugins until you click the playbutton, including a lot of adds) :
[https://addons.mozilla.org/sv-se/firefox/addon/flashblock/?src=oftenusedwith]("https://addons.mozilla.org/sv-se/firefox/addon/flashblock/?src=oftenusedwith")

---

### Post by res55 on 2011-02-25
Hi
I also had this problem: 
I first realised it due to a heat problem on my notebook. CPU was 78°C and above and fans were running.

So I looked for the culprit and it was "plugin-containe" per the command "top -bn1"

When I deactivated Shockwave Flash-plugin in FF this was solved for the moment, but I could not look any videos in FF.

So I applied this tip:

> **johanneslandin said:**
> 
Flashblock (Will halt most Flash plugins until you click the playbutton, including a lot of adds) :
[https://addons.mozilla.org/sv-se/firefox/addon/flashblock/?src=oftenusedwith](https://addons.mozilla.org/sv-se/firefox/addon/flashblock/?src=oftenusedwith)

and activated the  Shockwave Flash-plugin in FF again.

And this solved it: Now there is no "plugin-containe" when no video is running. When I call the youtube-website and search for a video, "plugin-containe" can be seen in the list of processes, but without cpu-usage.

Only when I start the video the cpu-usage starts and goes up to 15%. Then also the temperature goes up. But not so much as when FF was idle before. In the moment I push the pause-button of the video the cpu-usage of "plugin-containe" goes down to 1% and so does the temperature.

So this simple Flashblock-addon for FF does the whole trick. I can recommend it.

I hope it helps someone.
yours
Res

---

### Post by d3v1150m471c on 2011-03-26
You can add this to startup as a background process. It will check every 5 seconds to see if plugin-container is running and if so, it will test to see if it's running on average above 15% cpu from three tests taken over a 9 second period. if so, it kills it. This way you can leave your necessary plugins enabled. though, i've had all of them but flash disabled for a while now and it's the only one i've needed.

```

#!/bin/bash

while true; do
Read=`top -n1 | grep plugin-containe`
if [[ $Read == *plugin-containe* ]]; then
one=`top -n1 | grep plugin-containe | cut -d'.' -f1 | sed 's/  / /g' | sed 's/  / /g' | cut -d' ' -f11`
sleep 3
two=`top -n1 | grep plugin-containe | cut -d'.' -f1 | sed 's/  / /g' | sed 's/  / /g' | cut -d' ' -f11`
sleep 3
three=`top -n1 | grep plugin-containe | cut -d'.' -f1 | sed 's/  / /g' | sed 's/  / /g' | cut -d' ' -f11`
sleep 3
Test=$(($one + $two + $three))
[[ $Test -gt 45 ]] && pkill plugin-containe
else
sleep 5
fi
done

```

---

### Post by Legeril on 2011-04-05
> **kuric said:**
> Thanks, 4ebees. Actually, it works.

Go to about:config and search for:
dom.ipc.plugins.enabled.libflashplayer.so (Adobe Flash)
dom.ipc.plugins.enabled.libnptest.so (NPAPI test plugin) 
Alternate them to false. 

You're done, no more plugin-container running separately and eating all the RAM.

This worked great for me, a nice and easy fix. This plug-in container issue has been bugging me for a while, never thought to fix it till this afternoon though *chronic laziness*

Please mark thread as [solved] btw :P

---

### Post by fly2k on 2011-07-05
> **kuric said:**
> Thanks, 4ebees. Actually, it works.

Go to about:config and search for:
dom.ipc.plugins.enabled.libflashplayer.so (Adobe Flash)
dom.ipc.plugins.enabled.libnptest.so (NPAPI test plugin) 
Alternate them to false. 

You're done, no more plugin-container running separately and eating all the RAM.

What if there are no such parameters?

---

### Post by johanneslandin on 2011-10-13
Primary disorder: Advertisers deficit attention and use Flash with loads of graphics to get you hyperactive.

ADH(F)D, Attention Deficit Hyperactivity (Flash) Disorder

This is a problem related to Flash concerning all browsers and all operating systems, but the basic problem is that advertisers pay for your internet services. Therefore the problem will never be permanently solved, but you can work around it.

I've tried Windows, MAC, Ubuntu, SUSE; Firefox, Chrome, Opera. All of these have this problem, and trust me: Silverlight is no salvation from Flash. 

Flashblock is now for both Firefox and Chrome. I've used it for 18 months with Firefox and consider it the best extension for Mozilla since Netscape opened its first HTML document.

[https://addons.mozilla.org/en-US/firefox/addon/flashblock/](https://addons.mozilla.org/en-US/firefox/addon/flashblock/)
[https://chrome.google.com/webstore/detail/cdngiadmnkhgemkimkhiilgffbjijcie](https://chrome.google.com/webstore/detail/cdngiadmnkhgemkimkhiilgffbjijcie)

---

### Post by Qu4rk on 2013-02-02
> **johanneslandin said:**
> Primary disorder: Advertisers deficit attention and use Flash with loads of graphics to get you hyperactive.

ADH(F)D, Attention Deficit Hyperactivity (Flash) Disorder

This is a problem related to Flash concerning all browsers and all operating systems, but the basic problem is that advertisers pay for your internet services. Therefore the problem will never be permanently solved, but you can work around it.

I've tried Windows, MAC, Ubuntu, SUSE; Firefox, Chrome, Opera. All of these have this problem, and trust me: Silverlight is no salvation from Flash. 

Flashblock is now for both Firefox and Chrome. I've used it for 18 months with Firefox and consider it the best extension for Mozilla since Netscape opened its first HTML document.

[https://addons.mozilla.org/en-US/firefox/addon/flashblock/](https://addons.mozilla.org/en-US/firefox/addon/flashblock/)
[https://chrome.google.com/webstore/detail/cdngiadmnkhgemkimkhiilgffbjijcie](https://chrome.google.com/webstore/detail/cdngiadmnkhgemkimkhiilgffbjijcie)

Thanks.  Flashblock works perfectly!

---

### Post by oldos2er on 2013-02-02
Old thread closed.

---

