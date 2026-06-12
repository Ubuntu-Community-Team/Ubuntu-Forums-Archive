---
title: "How to force ATA-66 in Ubuntu?"
date: 2004-10-21
forum: General Help
---

### Post by negativ on 2004-10-21
I have an older IBM ATA-66 HDD that Ubuntu detects as ATA-33 (the BIOS correctly identifies it as ATA-66).  In some other distro (Suse, maybe?) there was a tool that allowed you to specify the DMA mode of an IDE device.  I don't know if I'd really see a big performance increase between ATA-33 and ATA-66, but still I'd feel better if I could make the drive run in ATA-66 mode.

How / where do I do this in Ubuntu?

Thanks.

---

### Post by cacofonix on 2004-10-27
Can you type in sudo hdparm -tT /dev/hda and post your results?

---

### Post by jdong on 2004-10-27
pass **ide=66**?

---

### Post by negativ on 2004-10-30
[QUOTE=cacofonix]Can you type in sudo hdparm -tT /dev/hda and post your results?[/QUOTE]

/dev/hda:
 Timing buffer-cache reads:   812 MB in  2.01 seconds = 404.24 MB/sec
 Timing buffered disk reads:   52 MB in  3.09 seconds =  16.83 MB/sec


seems low... ?

---

### Post by cacofonix on 2004-10-31
It does seem a little slow hope these help :D   
Enable  ATA66:
```
sudo hdparm -X68 /dev/hda
```

this can help speed thing up taken from the Gentoo handbook:
Activate DMA: ```
sudo hdparm -d1 /dev/hda
```

Activate DMA + Safe Performance-enhancing Options: 
```
sudo hdparm -d1 -A1 -m16 -u1 -a64 /dev/hda
```

if that still isnt enough try [*here*](http://usalug.org/phpBB2/viewtopic.php?p=33142) it has a mini howto guide to tweak your hdd

cacofonix

---

### Post by ynef on 2004-10-31
cacofonix's advice is very good and you should follow it.

To configure hdparm and have it run every time your system boots, you should edit your /etc/hdparm.conf file, which is more readable than all those acronyms. Try them out first like they are written in cacofonix's post, though! Having bad commands in your hdparm.conf file is a good way to break your system.

---

### Post by negativ on 2004-10-31
Hmm...  well, after all that, I ended up with:

/dev/hda:
 Timing buffer-cache reads:   884 MB in  2.00 seconds = 441.18 MB/sec
 Timing buffered disk reads:   52 MB in  3.07 seconds =  16.96 MB/sec

not exactly a breathtaking improvement, but thanks anyway. :D 

Guess I'll just live with it.

---

