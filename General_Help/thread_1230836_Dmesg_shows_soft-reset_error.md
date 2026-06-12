---
title: "Dmesg shows soft-reset error"
date: 2009-08-03
forum: General Help
---

### Post by MadHatter21 on 2009-08-03
Hello,

This is not so much a problem because kernel boots right past it, but i was wondering what it is. I am just starting out with linux learning about dmesg. I went thought it until i got to 

```

ata1 : Softreset failed (device not ready)
ata1 : failed due to HW bug, retry pmp=0
ata1 : Sata link ...
...

```
What is the soft reset failure waiting for? How can i fix it? Do i need to fix it if ubuntu works perfectly still?

Ubuntu 9.04 Desktop,
MadHatter21

---

### Post by aesis05401 on 2009-08-03
One suggestion - add all_generic_ide to the end of your grub boot command. 

From grub menu highlight your kernel, press 'e', highlight the line that says 'kernel,' press 'e', add all_generic_ide to the end of the line of commands.

Does this help?

---

### Post by MadHatter21 on 2009-08-03
No this did not help, the same error occured in the dmesg file and the output of the kernel at boot up.

---

### Post by ericab on 2009-08-03
i have the same thing too.... i remember a while ago seeing and report of it on launchpad... not sure if they came to a solution. check there.

---

