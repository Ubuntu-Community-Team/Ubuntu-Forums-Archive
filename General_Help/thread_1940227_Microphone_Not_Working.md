---
title: "Microphone Not Working"
date: 2012-03-13
forum: General Help
---

### Post by Thaumaturge90 on 2012-03-13
I'm running Ubuntu 11.10 Oneiric Ocelot on a Toshiba Satellite Laptop computer.
My problem is I don't have any use of my microphone.

I found out elsewhere that the following information would be useful in the troubleshooting process, so here it goes:
> 
&& bash alsa-info.sh 
--2012-03-13 03:47:47--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) 
Resolving [www.alsa-project.org]("http://www.alsa-project.org")... 77.48.224.243 
Connecting to [www.alsa-project.org|77.48.224.243|:80]("http://www.alsa-project.org%7C77.48.224.243%7C:80")... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://git.alsa-project.org/?p=alsa-driver.git;&#8203;a=blob_plain;f=utils/alsa-info.sh]("http://git.alsa-project.org/?p=alsa-driver.git;%E2%80%8Ba=blob_plain;f=utils/alsa-info.sh") [following] 
--2012-03-13 03:47:48--  [http://git.alsa-project.org/?p=alsa-driver.git;a=b&#8203;lob_plain;f=utils/alsa-info.sh]("http://git.alsa-project.org/?p=alsa-driver.git;a=b%E2%80%8Blob_plain;f=utils/alsa-info.sh") 
Resolving git.alsa-project.org... 77.48.224.243 
Reusing existing connection to [www.alsa-project.org:80]("http://www.alsa-project.org:80"). 
HTTP request sent, awaiting response... 200 OK 
Length: unspecified [text/plain] 
Saving to: `alsa-info.sh' 

    [   <=>                                 ] 27,247      56.9K/s   in 0.5s     

2012-03-13 03:47:50 (56.9 KB/s) - `alsa-info.sh' saved [27247] 

This script visits the following commands/files to collect diagnostic 
information about your ALSA installation and sound related hardware. 

  dmesg 
  lspci 
  lsmod 
  aplay 
  amixer 
  alsactl 
  /proc/asound/ 
  /sys/class/sound/ 
  ~/.asoundrc (etc.)

---

