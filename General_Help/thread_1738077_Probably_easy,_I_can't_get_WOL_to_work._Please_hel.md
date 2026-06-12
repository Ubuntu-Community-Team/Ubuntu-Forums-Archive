---
title: "Probably easy, I can't get WOL to work. Please help."
date: 2011-04-24
forum: General Help
---

### Post by eddie3000 on 2011-04-24
Hello folks! 
Great forum, and there are quite a few threads about wakeuponlan and so. But I can't get it to work.

I have Ubuntu 10.10. I have enabled a "Wake on ring" feature in the bios of my computer. It is connected to the internet through a modem-router. I think I have set the nat feature to redirect the traffic to the desktop I want to turn on remotely. I'm not too sure that I've done this correctly.
I have dynamic DNS. 
I have teamviewer working fine.
I have installed ethtool and wakeuponlan on both computers, remote desktop and laptop pc ( I expect to be able to turn on my remote desktop from my laptop).
I followed this guide: 

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

I have tried:

wakeonlan my:ma:ca:dd:re:ss

and:

wakeonlan -i my.ipa.dre.ss -p port my:ma:ca:dd:re:ss

Nothing. I have no idea why it won't work. Any suggestions? 
Thanks.

---

