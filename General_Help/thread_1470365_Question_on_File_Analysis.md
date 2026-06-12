---
title: "Question on File Analysis"
date: 2010-05-02
forum: General Help
---

### Post by Dan09 on 2010-05-02
Hey guys, I have a strange question regarding a suspicious .exe file I downloaded on the Windows 7 side of my dual boot system.  After downloading it from a dodgy site, and getting a TERRIBLE report on it from VirusTotal I'm 90% sure it's a virus.  However, I really need the program that it claims to be and want to be absolutly sure before I give up on it.

Would it be possible for me to run the .exe under Linux using Wine to determine whether or not this file is legit? That way it wouldn't be able to harm my computer, and I can get a better look at it than what I get from VirusTotal (which I've known to be wrong about many, many files in the past).

Thanks much!

---

### Post by Dan09 on 2010-05-03
Anyone? :X

---

### Post by WorMzy on 2010-05-03
I'd say it's possible, but I don't know enough about virus' to say whether it's recommendable or not. You might want to copy the file to an ext* partition and unmount any ntfs partitions just to be on the safe side.

---

### Post by Sam on 2010-05-03
Yep use Wine and in case of trouble just delete the directory ~/.wine

Otherwise if Wine cannot open the exe for any reason, you can use a virtual machine, but that's another story...

---

