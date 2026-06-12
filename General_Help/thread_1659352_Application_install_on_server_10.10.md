---
title: "Application install on server 10.10"
date: 2011-01-03
forum: General Help
---

### Post by peter_parker on 2011-01-03
hey guys,

I recently installed ubuntu server edition 10.10 on an old desktop i had laying around in the purpose of making it my torrent box.  

I'm still fairly new to linux and especially the command line only aspect of ubuntu server.  

I just had  question on how im supposed to install a program from the terminal?

i'm trying to install Vuze

I type in:


wget [http://sourceforge.net/projects/azureus/files/vuze/Vuze_4510/Vuze_4510_linux.tar.bz2/download](http://sourceforge.net/projects/azureus/files/vuze/Vuze_4510/Vuze_4510_linux.tar.bz2/download)


This will kick off my download to what i think is the file.  i get this:


Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/project/azureus/vuze/Vuze_4510/Vuze_4510_linux.tar.bz2?r=&ts=1294110865&use_mirror=superb-sea2](http://downloads.sourceforge.net/project/azureus/vuze/Vuze_4510/Vuze_4510_linux.tar.bz2?r=&ts=1294110865&use_mirror=superb-sea2) [following]
--2011-01-03 22:14:22--  [http://downloads.sourceforge.net/project/azureus/vuze/Vuze_4510/Vuze_4510_linux.tar.bz2?r=&ts=1294110865&use_mirror=superb-sea2](http://downloads.sourceforge.net/project/azureus/vuze/Vuze_4510/Vuze_4510_linux.tar.bz2?r=&ts=1294110865&use_mirror=superb-sea2)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://superb-sea2.dl.sourceforge.net/project/azureus/vuze/Vuze_4510/Vuze_4510_linux.tar.bz2](http://superb-sea2.dl.sourceforge.net/project/azureus/vuze/Vuze_4510/Vuze_4510_linux.tar.bz2) [following]
--2011-01-03 22:14:23--  [http://superb-sea2.dl.sourceforge.net/project/azureus/vuze/Vuze_4510/Vuze_4510_linux.tar.bz2](http://superb-sea2.dl.sourceforge.net/project/azureus/vuze/Vuze_4510/Vuze_4510_linux.tar.bz2)
Resolving superb-sea2.dl.sourceforge.net... 209.160.57.180
Connecting to superb-sea2.dl.sourceforge.net|209.160.57.180|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15083539 (14M) [application/octet-stream]
Saving to: `download'

100%[=========================================================================>] 15,083,539  70.0K/s   in 3m 45s

2011-01-03 22:18:08 (65.5 KB/s) - `download' saved [15083539/15083539]



So i think it saved it as 'download'.  what do i do from here?  am i supposed to extract 'download'?  when i try to ls in it, it says its not a directory....

Any help would be appreciated.

Thanks!!

---

### Post by dcstar on 2011-01-03
> **peter_parker said:**
> hey guys,

I recently installed ubuntu server edition 10.10 on an old desktop i had laying around in the purpose of making it my torrent box.  

I'm still fairly new to linux and especially the command line only aspect of ubuntu server.  

I just had  question on how im supposed to install a program from the terminal?
.........
```
man aptitude
```

---

