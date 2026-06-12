---
title: "Orinoco compiling - enabling wireless extensions"
date: 2009-12-18
forum: General Help
---

### Post by Jungle-Cat on 2009-12-18
Hi,
I'm wanting to get Kismet going with my orinoco card. I've previously determined the drivers I need but have not been able to install them. 

I'm running Ubuntu LTS 8.04 - 2.6.24-24-generic kernel
Trying to isntall these from source:
[http://www.kismetwireless.net/code/orinoco-0.13-dragorn-2.6.17.tar.gz](http://www.kismetwireless.net/code/orinoco-0.13-dragorn-2.6.17.tar.gz)
As per here:
[http://www.kismetwireless.net/download.shtml](http://www.kismetwireless.net/download.shtml)

The instructions there do not help either. I've acquired Linux-headers from apt, and when trying to install I get:
"
makefile:40 *** Wireless extensions are not enabled. Stop.
"

With the orinoco card in, iwconfig shows it up and it appears to work. But in Kismet it doesn't because of the drivers that are currently there... hence wanting to put these on. Kismet even has a window pop up says that the orinoco_cs that is there is ****.

So they do appear to be enabled... I found an old thread here, same issue but for MadWifi - the page it linked to that the OP said worked is 404 now...

Thanks

---

