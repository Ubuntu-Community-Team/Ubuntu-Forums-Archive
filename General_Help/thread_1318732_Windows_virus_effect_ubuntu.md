---
title: "Windows virus effect ubuntu?"
date: 2009-11-07
forum: General Help
---

### Post by eMan520 on 2009-11-07
Can someone tell me if a Windows virus can effect Ubuntu Jaunty? I have a flash drive with a virus on it.

---

### Post by edd07 on 2009-11-07
Windows viruses do nothing if you are running Ubuntu.

---

### Post by Carbonfusion on 2009-11-07
I don't think so, generally viruses have to been written for an environment in the same way other software is platform specific. That is the virus has to be written for linux to infect a linux system. 

So, no, it should be fine to open, if you want to be extremely paranoid, boot from a live disk and don't mount any hard disks.

---

### Post by tacantara on 2009-11-07
Here's how I understand the virus issue, per what I've read on previous posts in UF....

Because of the differences in the OSes, a virus written to affect Windows should not affect an Ubuntu OS.  If the file makes it on to your Ubuntu box, it should not function.  However, it's always best to err on the side of caution.  If the virus has worked its way onto your Ubuntu system, try to locate and delete it.

---

### Post by UranUtan on 2009-11-07
> **eMan520 said:**
> Can someone tell me if a Windows virus can effect Ubuntu Jaunty? I have a flash drive with a virus on it.

Short answer: the Windows virus cannot do absolutely nothing.

Long answer: if you use Wine (an environment to execute some Windows programs within Linux), and you explicitly run the virus in the Wine instance then only the Wine instance will get affected, which is very easy to clean up. Even in this case, the virus will be confined there and will have no way to propagate to Linux.

---

### Post by CharlesA on 2009-11-07
Same thing goes when running Windows in a VM.

---

### Post by fela on 2009-11-07
Normally a windows virus can do nothing to your Ubuntu/Linux installation. However if you use something like Wine and run the virus with that, there is a possibility of it affecting any files that are owned by you, ie any files in your home folder. However you'd have to run it by choice and I don't think this is very likely :)

So the short answer is no, don't worry about viruses on Linux.

edit: didn't see the post that was near enough exactly the same as my one. I guess it's always good for something to be backed up by someone.

---

### Post by fhmanas on 2009-11-08
Like what everybody said, only Wine may be affected by the virus so your system should be safe from the Win Virus.  You might also want ClamAV to clean your USB stick of the virus.  However, although, your Ubuntu system will not be affected by virus, your system can still be a carrier of the virus so if you transfer the infected file to a Win system, the Win system may still get infected.

---

