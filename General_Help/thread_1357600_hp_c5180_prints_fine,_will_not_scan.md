---
title: "hp c5180 prints fine, will not scan"
date: 2009-12-17
forum: General Help
---

### Post by mrufino1 on 2009-12-17
I have an hp c5180 and it will not scan. I have had it working in previous versions, and it prints fine right now, but xsane will not recognize it. Finding a terminal command in another post here got xsane to start, but it froze when I went to preview the scan. xsane says no scanners are found. In the past, when this was the case, I had to install hplip from sourceforge, but hplip is now installed as part of ubuntu. Does this make a difference? I'm going to try to install from sourceforge anyway, see what happens. In the printing properties, this is now the hp output
nssd://Photosmart%20C5100%20series%20%5B4F64FB%5D._pdl-datastream._tcp.local/
It used to be that it would list the ip address (printer is on a network). The printing is working with the hpijs or hpcups driver, just no scanning. I reinstalled xsane, installed sane, installed extra libraries. I am stumped, any ideas? Thanks.

---

### Post by erilidon on 2009-12-20
I was recently wondering this too. However the C5180 has a web interface that can be used to scan.

---

### Post by mrufino1 on 2009-12-20
I installed hplip with the package on the hp linux website and it now scans, no problem. Not sure what the difference is, but it works now.
[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)
There are some dependencies that you need to satisfy, I can't remember what they are, but run the installer and then when it fails, go to synaptic and install the dependency it is asking for. I should probably write these things down so I don't have to keep researching it each time I have to do it and so I can help someone else too...

---

### Post by inhiway on 2009-12-21
mrufino1, thanks for the tips and the link.  I have an hp c5240.  I had to run the hplip file twice, but I do have a working scanner now.  I think in all the Linux distros I've tried, this is the first time I have been able to use the scanner on any multifunction printer I've ever had.  Thanks again.\\:D/

---

### Post by mrufino1 on 2009-12-21
You're welcome! I'm just happy that I finally helped someone else solve an issue!

---

