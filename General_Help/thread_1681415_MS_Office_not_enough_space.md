---
title: "MS Office not enough space"
date: 2011-02-04
forum: General Help
---

### Post by Ampi on 2011-02-04
I installed MS Office 2007 blue edition via Wine with no problems. It's al there and everything runs. A couple of days ago Ubuntu 'tells' me that my /home folder has only so many MB free of space and then it wants me to run the disk analyzer tool.

I dont really understand. I know my wine folder is in my home, but when I check my home folder:
```
user@desktop:~$ df -h $HOME
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              24G  2.6G   20G  12% /home
```
I have more than enough space. In the disk analyzer tool I see that my .wine folder is full (it's around 1.7 GB) and used for 99%.

My questions
1. Why doesnt Wine 'make' the .wine folder as large as necessary?
2. How do I change this without reinstalling?

---

### Post by mcduck on 2011-02-04
I don't know what caused your actual problem (the erros message), but you are misinterpreting the Disk Usage Analyzer's output.

It's not telling you that the .wine folder would be 99% full. it's telling you that the .wine is 99% of the space used by it's parent folder (your home). In other words, 99% of the data in your home directory is located inside .wine.

---

### Post by Ampi on 2011-02-04
Aha, that is very good to know, thanks! 
I had no idea what the disk analyzer was telling me, as far as I know 1.7GB is not 99% of 24GB :)
So maybe I just had the trash in my home folder very full causing me to go near the 24GB, as I just installed I had to copy back and forth from my old computer and deleting a lot of old s**t that I didnt need anymore.
Thanks again, if the error messages comes up again, Ill reply.

---

