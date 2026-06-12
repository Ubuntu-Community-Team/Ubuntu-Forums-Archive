---
title: "Grub bootloader"
date: 2010-01-06
forum: General Help
---

### Post by supertails on 2010-01-06
Can some help me secure the bootloader?

---

### Post by drs305 on 2010-01-06
> **supertails said:**
> Can some help me secure the bootloader?

If you want password protection and are using Grub 2 (1.97~beta) here is a guide:
[Grub 2 Password Protection]("http://ubuntuforums.org/showthread.php?t=1369019")

You can check the version of Grub with "grub-install -v".

If you want to *hide* Recovery partitions or the Windows Recovery option, take a look at:
[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")
Warning: Some is simple, some is really for certified geeks.

---

### Post by supertails on 2010-01-07
My teacher told me that if you don't password protect the grub then anyone could change it whether they have physical access or not. Is that really true?

---

### Post by drs305 on 2010-01-07
> **supertails said:**
> My teacher told me that if you don't password protect the grub then anyone could change it whether they have physical access or not. Is that really true?


If they have physical access to the machine anyone can use a LiveCD and if they know what they are doing they can modify files on the system. But if they have physical access to the machine, there are lots of other ways that people can mess with your machine.

If the system is running, the grub files are protected just as are the rest of the files on a linux system, and I would take their security over the security provided by that other OS any day.

But I'm not a security expert. ;-)

---

### Post by supertails on 2010-01-07
That's kinda confusing cause u didn't use don't in any of the sentences.

"If they have physical access to the machine anyone can use a LiveCD and if they know what they are doing they can modify files on the system. But if they have physical access to the machine, there are lots of other ways that people can mess with your machine." Should their but a don't in one of them?

---

### Post by audiomick on 2010-01-07
No, drs305 meant it as written. He could have added "...so someone with a live CD is the least you have to worry about."

---

### Post by drs305 on 2010-01-07
> **supertails said:**
> That's kinda confusing cause u didn't use don't in any of the sentences.

"If they have physical access to the machine anyone can use a LiveCD and if they know what they are doing they can modify files on the system. But if they have physical access to the machine, there are lots of other ways that people can mess with your machine." Should their but a don't in one of them?

Let me try again: If they have physical access to your machine protecting GRUB with a password offers marginal protection. There wasn't meant to be a "don't". 

If I put a "don't" in the second sentence so it read:
"But if they *don't* have physical access to the machine, there are lots of other ways that people can mess with your machine." it would not have conveyed my intent. 

I feel much more secure with my linux machine than any machine I had using Windows.

---

