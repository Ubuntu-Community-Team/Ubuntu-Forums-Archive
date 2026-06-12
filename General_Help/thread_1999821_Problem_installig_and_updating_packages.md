---
title: "Problem installig and updating packages"
date: 2012-06-08
forum: General Help
---

### Post by hg088 on 2012-06-08
Hi.

Since yesterday, when i try to do "sudo apt-get update" or install an app "sudo apt-get conky-all" the process gets stuck trying to connect to "archive.ubuntu.com".

So i tried  to ping this sever and but i didn't get any reply. I can't either ping it from my android 4.0 phone.

The weird thing is that when i ping "archive.ubuntu.com" from windows 7 and from my routers web interface (tomato) everything goes well.

Then i tried ping the ip address from the server in ubuntu and i went fine, it's just that i can't ping "archive.ubuntu.com" from ubuntu.

It sure seems like a dns problem, so i tried do disable dnsmasq like suggested [here]("http://ubuntuforums.org/showthread.php?t=1996379"), but that didn't do it.I installed ubuntu 11.04 and i could ping the server succesfully and also could update without problems. The problem is just with precise and my android 4.0 phone so it seems to be something kernel related maybe?

---

