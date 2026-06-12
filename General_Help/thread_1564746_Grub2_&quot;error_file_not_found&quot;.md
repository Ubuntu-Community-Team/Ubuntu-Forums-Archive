---
title: "Grub2 &quot;error: file not found&quot;"
date: 2010-08-30
forum: General Help
---

### Post by masque7 on 2010-08-30
Referring to the documentation [here]("https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015%29"), there is nothing that seems to fit my problem.

I only have 1 operating system on my hard drive, I've removed Windows. 

When it starts I get **"error: file not found"** -- but it boots anyway! I'm posting from within my Ubuntu install now. Everything (except Grub2) is working perfectly. So it *can't* be error 15.

Just wondering if anyone has any ideas? It may decrease my boot time, and it's quite frustrating have that message, regardless if my system boots fine. My system is acting like I don't even have grub installed at all -- any command I try it doesn't recognise it
**"The program 'grub' is currently not installed."**

---

### Post by Rubi1200 on 2010-08-31
From the same guide you linked to, why not try reinstalling GRUB and see if that fixes it?

You lose nothing by trying it.

And don't forget to run ```
sudo update-grub
``` after rebooting.

---

### Post by masque7 on 2010-08-31
This issue must have been that the MBR was still okay however grub2 and grub-pc were not installed on my Ubuntu partition. Thanks. :-)

---

