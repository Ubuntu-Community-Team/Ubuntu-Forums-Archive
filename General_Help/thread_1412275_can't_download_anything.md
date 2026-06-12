---
title: "can't download anything"
date: 2010-02-21
forum: General Help
---

### Post by Elidan on 2010-02-21
i just installed ubuntu 9.10 on my laptop and i went on a website and was required to download the newest flash player, i started the download. in the middle of the download i lost my connection to the internet and the download froze, i reconnected it and it didn't continue (not that i expected it to) so i tried to close it but it wouldn't, i tried everything i could, it just wouldn't close, it was frozen like that, so i decided all i can do is restart my comp. after i restarted my computer no downloads work anymore. i tried redownload flash and this is the error i got:
 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the probelm
E:_cache->open() failed, please report.
 
i tried running Sudo dpkg --configure -a but it only read sudo, so after that i tried it without the sudo, so just dpkg --configure -a and this is the response i got:
 
requested operation requires superuser privilege
 
so i don't know what to do now. i get the exact same error when i try to download ubuntu updates as when i try to download flash.
 
another downloading problem that i have is when i try to download something from Ubuntu software center the download progress bar shows up and under the downlaod name it says "waiting for other software managers to quit" and the progress stays at 0%, no matter how long you wait it stays that way, it's like that with anything i try to download from Ubuntu software Center andrestarting my comp dosen't help at all.
 
if someone could tell me how to fix these problems i would really appreciate it, but it would be just as good if someone could tell me how to run some kind of system restore like program if such a program exists. thnx in advance =)

---

### Post by Ozymandias_117 on 2010-02-21
In linux, case matters, this means when you did Sudo dpkg --configure, you were actually telling it a different command from sudo dpkg --configure. So, basically, don't put a capital s =)

---

### Post by Elidan on 2010-02-21
> **Ozymandias_117 said:**
> In linux, case matters, this means when you did Sudo dpkg --configure, you were actually telling it a different command from sudo dpkg --configure. So, basically, don't put a capital s =)
 
hmm, i am pretty sure i didn't capitilize it b4 but i decided to try it once again and it works, thnx! now everything should work fine =D

---

### Post by Ozymandias_117 on 2010-02-21
Glad to help :)

---

