---
title: "&quot;select file system type&quot;"
date: 2010-10-06
forum: General Help
---

### Post by Roasted on 2010-10-06
I split my partitions - root and home.

In the installation of Ubuntu you can see the partition table if you edit it manually. You can see the partitions, devices, etc. What if I select the wrong file system on a partition I am not formatting? Example - if I format root but keep home, but home is EXT3 and I select EXT4 (or vice versa) what happens?

---

### Post by sikander3786 on 2010-10-06
I think one will have to try it actually to see the results. I haven't done that even by mistake.

Do you think it will somehow convert EXT3 into EXT4 and keep the data? If so, seems a bit odd to me.

---

### Post by Roasted on 2010-10-06
> **sikander3786 said:**
> I think one will have to try it actually to see the results. I haven't done that even by mistake.

Do you think it will somehow convert EXT3 into EXT4 and keep the data? If so, seems a bit odd to me.

I'm really not sure. I'm tempted to fire up a test computer just to see. I figured I'd ask meanwhile to see if anybody had any concrete answers or ideas on it since I was kind of clueless on my assumption.

---

### Post by sikander3786 on 2010-10-06
> **Roasted said:**
> I'm really not sure. I'm tempted to fire up a test computer just to see. I figured I'd ask meanwhile to see if anybody had any concrete answers or ideas on it since I was kind of clueless on my assumption.
I doubt if the installer will proceed further. Might be it says to correct the filesystem on /dev/xxx before proceeding. Anyways, I've also started feeling curious about it :-)

---

### Post by whiskeylover on 2010-10-06
Try it in virtualbox

---

### Post by srs5694 on 2010-10-06
> **sikander3786 said:**
> I think one will have to try it actually to see the results. I haven't done that even by mistake.

Do you think it will somehow convert EXT3 into EXT4 and keep the data? If so, seems a bit odd to me.

I seem to recall seeing bug reports of the system erasing the old filesystem and putting a new filesystem of the requested type on the partition with 10.04, but I'm not 100% positive of that, and I've never tested it myself. In any event, I advise caution on this score -- even a slim chance of destroying your data in /home should be avoided, if at all possible! If in doubt, quit the installer, check the filesystem type, and be sure it's specified correctly. Alternatively, for /home, you could omit the /home partition from the partition list and then add it manually to /etc/fstab after the system is installed.

---

