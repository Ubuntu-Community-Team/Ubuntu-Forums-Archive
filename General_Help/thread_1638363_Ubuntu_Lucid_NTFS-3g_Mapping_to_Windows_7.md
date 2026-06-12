---
title: "Ubuntu Lucid NTFS-3g Mapping to Windows 7"
date: 2010-12-05
forum: General Help
---

### Post by LMCarr on 2010-12-05
Hello and thank you in an advance for your help!

I installed Ubuntu Lynx using Wubi. I wanted to map Window to Ubuntu using NTFS-3g. It did not show "Win7" or "Windows" as an option during the process and instead the program mapped to "SYSTEM RESERVED" & "PQSERVICE." Here are my 2 questions:

- Why didn't Windows show up as an option? Isn't Win7 or Windows what I want?
- If I have to get rid of SYSTEM RESERVED and PQSERVICE, how can I erase it from ubuntu? I've "umounted" each drive but I still can't get rid of them.

Thank you!

---

### Post by gordintoronto on 2010-12-05
I'm not sure what you mean by "map". Lucid has no need for NTFS-3g. If you open the "place," "computer," you should see all the Windows partitions. You can click or double-click on them, and navigate through all the folders.

Re your questions: 1: no. 2: I can't figure out what you are trying to say.

---

### Post by Morbius1 on 2010-12-05
Not an expert on Wubu but : [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives")

> 
How do I access the Windows drives? 

The  Windows partition where you installed Wubi is available as [COLOR=Blue]/host[/COLOR] within  Ubuntu (places > computer > file system > host) All the other partitions will be available under places > removable media 

---

