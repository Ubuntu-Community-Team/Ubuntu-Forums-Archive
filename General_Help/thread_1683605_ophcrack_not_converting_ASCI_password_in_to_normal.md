---
title: "ophcrack not converting ASCI password in to normal text:"
date: 2011-02-07
forum: General Help
---

### Post by freesparks on 2011-02-07
Hello all,

  I'm desperate, well here's the issue, a friend of mine locked himself out of his system and forgot his password and I manage to boot with ophcrack 2.3.1 and we were able to see the files, luckilly.  Now, we just want to retrieve his passwor to get back into the system.  So far I got up to the part where is actually produces the file and this is what is contained in the file:
> 
Administrator:500::31d6cfe0d16ae931b73c59d7e0c089c0:::
Guest:501::31d6cfe0d16ae931b73c59d7e0c089c0:::
SUPPORT_388945a0:1002::881037e0b6909b04b6900f7c806dca6e:::
HelpAssistant:1004:b209ce7e3ff7aea1131906e9f5df4819:d83f663c50bcd5815ccb94f9e38a9a4b:::
Beverly:1005:00006395b1acd69aaad3b435b51404ee:992ac78ffb08204c592c6e47b916f85d:::

Very self explanatory based on the error I'm getting because this is what it reads:

> Tables found:
     /mnt/hdc/tables/xp_free_small

Found one partition that contains hashes:
     /mnt/hda1/WINDOWS/system32/config

Starting Ophcrack
QIconvCodec::convertFromUnicode:  using ASCII for conversion, iconv_open failed
QIconvCodec::convertToUnicode:      using ASCII for conversion, iconv_open failed
/home/tux/launch.sh: line 100:          1044 Killed
ABLES_INLINE -w $FOUND/ -n $numcpu -o /tmp/ophcrack.txt $opts
Press a key to exit::


Any help on this would be greatly appreciated,  I was so relieved when I learned it was Linux and had all the common utilities found in Ubuntu and other Linux distros.

Best Regards,

freesparks

---

### Post by freesparks on 2011-02-07
Whats funny is we have access to all the files.  I wonder if Windows XP stores passwords somewhere in a regular format.

Best Regards,

freesparks

---

