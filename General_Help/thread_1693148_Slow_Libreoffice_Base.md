---
title: "Slow Libreoffice Base"
date: 2011-02-22
forum: General Help
---

### Post by Eduardoecp on 2011-02-22
I've recently installed Ubuntu 10.10 and Libreoffice 3.3. My Base is very very slow. I've already tried changing the JRE to the Oracle/Sun latest version and the problem is still there. The problem doesn't seem to be in the file, since I can open it on my Windows 7 Libreoffice, without any problems. Please help me, solving this bug is important for me to definetely migrate from Windows to Linux.

---

### Post by grahammechanical on 2011-02-22
What a coincidence! In the absolute beginners forum someone posted the answer to speeding up Open Office. I used it because I found Base very slow to go from the first record to the last. It took many minutes to do this. Now, it does in a few seconds. Do you want to know the secret?

Load up Open Office. It does not matter which of the programs you use but the word processor will do.

go to Tools>Options and select Memory, Increase the memory available. If you only increase the memory by a small amount you may not get the effect that you want. This happened to me. so, I used the settings that suggested were in the other post.

Used For Openoffice.org    50MB

Memory per Object    12MB

This worked for me. Regards.

---

### Post by Eduardoecp on 2011-02-22
Sorry, I tried it and the problem remains. Thank you, anyway.

---

### Post by Eduardoecp on 2011-02-23
Finally I solved the problem. Actually, I found a way around it. I've installed Libreoffice for Windows and Java (JRE) Windows version using Wine. It's crucial to download the right file, which can be found [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6626"). Java is important because without it the LO Base won't work at all. Now it works great. This is a temporary solution, until they release another version of Libreoffice.

---

### Post by JohnM1 on 2011-02-25
I have the same problem, it appeared with the latest version of Sun Java, see this bug report:

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/724217](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/724217)

---

### Post by ugm6hr on 2011-05-30
This appears to resolve the speed issue:
[http://hardc0l2e.wordpress.com/2011/04/05/libreoffice-openoffice-base-slow/](http://hardc0l2e.wordpress.com/2011/04/05/libreoffice-openoffice-base-slow/)

---

### Post by Eduardoecp on 2011-05-30
Thank you very much! It worked perfectly.

---

### Post by JavaMeister on 2011-12-05
I tried 20 and 26 to no avail. 21 worked perfectly. I can't believe how much time I have wasted over many months of tolerating this extreme slowdown. Ron

---

