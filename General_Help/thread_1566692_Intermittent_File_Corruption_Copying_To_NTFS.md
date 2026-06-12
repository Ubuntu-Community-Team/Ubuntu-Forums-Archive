---
title: "Intermittent File Corruption Copying To NTFS"
date: 2010-09-02
forum: General Help
---

### Post by airjrdn on 2010-09-02
I'm relatively new to Linux, so bear with me.  I'm about 38 days into my install...at least that's what uptime shows me right now. :)

Feel free to tell me if this is a known issue and I've been blissfully unaware of it up to this point.

I've copied a 7.9G file multiple times, and sometimes the destination file gets corrupted.  Here's what I've done:

Same for all copies - copied using:  Linux Mint 9 (isadora) Kernel 2.6.32.21-generic
GNOME 2.30.2


1 (bad)
---------------------------------
Source:  WinXP machine on network
Destination:  32G AData thumb drive (NTFS)
Result:  Corrupt, MD5 Hash doesn't match

2 (bad)
---------------------------------
Source:  WinXP machine on network
Destination:  80G USB drive (NTFS)
Result:  Corrupt, MD5 Hash doesn't match

3 (good)
---------------------------------
Source:  WinXP machine on network
Destination:  /$HOME/temp
Result:  Fine, MD5 Hash matches

4 (bad - 1st copy to Data1)
---------------------------------
Source:  /$HOME/temp
Destination:  Data1 Internal SATA drive (NTFS)
Result:  Corrupt, MD5 Hash doesn't match

5 (good - 1st copy to Data2)
---------------------------------
Source:  /$HOME/temp
Destination:  Data2 Internal SATA drive (NTFS)
Result:  Fine, MD5 Hash matches

6 (good - 2nd copy to Data1)
---------------------------------
Source:  /$HOME/temp
Destination:  Data1 Internal SATA drive (NTFS)
Result:  Fine, MD5 Hash matches

7 (good - 2nd copy to Data2)
---------------------------------
Source:  /$HOME/temp
Destination:  Data2 Internal SATA drive (NTFS)
Result:  Fine, MD5 Hash matches

8 (good - 3rd copy to Data1)
---------------------------------
Source:  /$HOME/temp
Destination:  Data1 Internal SATA drive (NTFS)
Result:  Fine, MD5 Hash matches

So, it appears to copy from an SMB share just fine, and to its own filesystem just fine, but intermittently has trouble writing to local NTFS partitions.  Writing to an SMB NTFS share is also file, which makes sense since it isn't having to talk "directly" to NTFS.

Another point to note is that there aren't just two md5 hashes (one good, one bad).  There's one good, and multiple bad.

---

### Post by Mark Phelps on 2010-09-02
I presume that you're mounting "local" NTFS partitions to write to them... if that's the case, use filesystem type of ntfs-3g, not ntfs.  The ntfs-3g SW does a much better job of handling the NTFS stuff.  Check for it in Synaptic.

---

### Post by airjrdn on 2010-09-02
When I connect one, it mounts automatically, so however that happens by default is how they're being mounted.

---

### Post by airjrdn on 2010-09-03
I was hoping to get a few more responses, given that the OS is silently corrupting data, you'd think this would be fairly important.

---

