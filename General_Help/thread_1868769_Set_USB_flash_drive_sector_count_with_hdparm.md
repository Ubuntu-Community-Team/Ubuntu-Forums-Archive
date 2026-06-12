---
title: "Set USB flash drive sector count with hdparm"
date: 2011-10-24
forum: General Help
---

### Post by osx on 2011-10-24
I have a Verbatim USB flash drive that I used it's V-Safe security program on. It appears to have set the sector count to a lower number in order to hide the encrypted data. I did this just to play around with it; however, that software doesn't run in Linux - only Windows.

Since then I've forgotten the password and don't really care as I never did put anything in the protected space. Now I just want to reclaim the space so I can use the entire capacity of my thumb drive. I assume I can just re-download the original software and reset the disk, but I wanted to try out hdparm to do this or some other Linux tool.

When I run the commands:
```
sudo hdparm -N /dev/sdf
or
sudo hdparm -N --prefer-ata12 /dev/sdf
```

I get the following results:

> /dev/sdf:
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 max sectors   = 0/1, HPA is enabled

It appears Verbatim uses HPA if this output is correct. The problem is that the man page for hdparm indicates that I should be getting specific sector details - not 0/1. Other people getting an hdparm sector output of 0/1 are also reporting problems (although not on flash drives).

If I have to, I can probably use a friend's Windows machine to get and use the V-safe software, but does anybody know of a way to reset the thumb drive to it's maximum sector count using a Linux tool? Again, I don't care about losing any data in the protected area as I don't think I ever put anything in it. The Verbatim drive is 8 GB.

Thanks.

---

