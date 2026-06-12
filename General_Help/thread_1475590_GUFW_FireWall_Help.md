---
title: "GUFW FireWall Help"
date: 2010-05-07
forum: General Help
---

### Post by XWindows on 2010-05-07
Need help with gufw... 

New to ubuntu, and I am not very good at command line.

**Is a firewall really needed ?**

I have searched and still am at a loss. I see advice on allowing Ports and IP's but I cannot seem to figure out  the correct settings. 

My question with ubuntu and gufw is, when I activate it I cannot access my home network from the ubuntu system. I am not computer savey enough to understand the settings. I have 4 computers in the house and all works well until I activate the firewall, then I get a blank screen (no network share) when trying to access the other shared files. The other computers are XP pro. All works fine without the firewall activated. Any suggestions?

In a nutshell, I can access the ubuntu machine from all the other computers but cannot access the other computers from the ubuntu machine.

---

### Post by zvacet on 2010-05-07
I hope [this]("https://help.ubuntu.com/community/Gufw") will help you.You can also read [this.]("http://ubuntuforums.org/showthread.php?t=694198&highlight=security")

---

### Post by XWindows on 2010-05-08
> **zvacet said:**
> I hope [this]("https://help.ubuntu.com/community/Gufw") will help you.You can also read [this.]("http://ubuntuforums.org/showthread.php?t=694198&highlight=security")

Thanks! I have it working but not real sure how. Main window I have it set to Deny, I allowed both TCP and UDP under the advanced setting and entered my network range 10.2.1.1/22 - 10.2.1.5/22, Nothing entered for Ports, clicked Add.

In the window it changes my range and has 10.2.0.0/22 and 10.0.0.0/22 the range is the same???

It works but I would like to understand why and if it really is protecting anything.

thanks again

---

