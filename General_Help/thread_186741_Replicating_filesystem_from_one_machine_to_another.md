---
title: "Replicating filesystem from one machine to another"
date: 2006-06-02
forum: General Help
---

### Post by bforbes on 2006-06-02
I need to set up 16 machines identically. I've found out how to automate the Ubuntu install. Now I'd like to set one machine up, ie install packages, change configurations, then replicate that onto every other machine. 

Can I do this with rsync, and are there better ways to do it? Note that every machine is 100% identical in terms of hardware.

---

### Post by aysiu on 2006-06-02
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by bforbes on 2006-06-02
I've considered that, but I think it wouldn't be automated enough. I'd need to boot each machine up with the Live CD, download and install PartImage, hook up the external media, image the drive. I'd prefer to do the automated Ubuntu install, then run a single script on each machine that sets them up by transferring files from the master computer. Is there a way I can do that?

---

### Post by aysiu on 2006-06-02
Well, there's a [System rescue CD](http://www.sysresccd.org/Main_Page) that includes PartImage (eliminating the extra download and install step), and PartImage can also store the image on a local server.

---

### Post by bforbes on 2006-06-03
That looks like a good option. So, I would do one computer, create the image, store it on a server, then use the rescue CD to image each hard drive? Would I have to partition each drive or is that also built into the image?

---

### Post by aysiu on 2006-06-03
Hm. Yes, unfortunately, you would have to partition each one.

Partition images are... partition images. In fact, they are images of just the used space on a given partition. So if your partition is 10 GB, and you're using only 4 GB, then the partition image size will also be 4 GB.

I'm not sure if PartImage has an "entire hard drive" image option.

---

### Post by mbeierl on 2006-06-05
It almost sounds like you want to create a master boot image and have the other machines boot via dhcp from that.

---

### Post by bforbes on 2006-06-14
[QUOTE=mbeierl]It almost sounds like you want to create a master boot image and have the other machines boot via dhcp from that.[/QUOTE]

That's what we've ended up doing. We enabled PXE boot on all the cluster machines, and set up a DHCP/TFTP server that starts SystemImager and loads everything on. We're still ironing out the bugs but it's a good solution.

---

