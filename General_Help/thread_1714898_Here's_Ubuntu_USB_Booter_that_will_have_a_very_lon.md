---
title: "Here's Ubuntu USB Booter that will have a very long life"
date: 2011-03-26
forum: General Help
---

### Post by Tone303 on 2011-03-26
The black and blank fourth box in the top panel is "disk" activity, read and write. after OS and program is loaded there is hardly any reading, writing is even rarer. i hardly ever see activity in that box, everything gets cached to RAM.

Do the settings in about:config seen in bold in order to force everything to RAM Memory and use zero disk caching while browsing. This makes the system hardly ever write to the USB

Click Link for Larger Image:

[http://usera.ImageCave.com/Tone303/FFoxSet4USB.png](http://usera.ImageCave.com/Tone303/FFoxSet4USB.png)


[IMG]http://usera.imagecave.com/Tone303/FFoxSet4USB-.png[/IMG]

Edit 1: That third setting is not found in about:config and needs to be created as a right click -> new integer 

Edit 2: i fixed the image link so it really is bigger than the embedded image, if you read this post in the first 20 minutes of it posted, go back to that link and press browser refresh.

Additional Things for USB Booters

Make these 3 lines an .sh file and add it to your top panel:

tput civis 
df -h -t aufs
sleep 5

This tells your percent of virtual drive in use since the regular disk usage analyzer tells you free space on the USB drive rather than free space in the 3.95 GB virtual drive (AKA persistence file)

2) Have RAM Memory box in top panel, Add BleachBit to top panel with the memory box checked, it cleans RAM cache but RAM cache is GOOD with this system at almost all times.

My USB system does mic, cam, streaming videos, and everything done on hard drive except collect stuff. and i updated it once with a large update after installation. Ubuntu 10.04.2 LTS Updated Once is what i use for USB.

youll like a USB set up this way if your hard drive physically breaks. I use an 8 GB of that famous make and model of USB everyone is so fond of.

---

