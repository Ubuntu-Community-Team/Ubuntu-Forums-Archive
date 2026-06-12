---
title: "error: cannot execute binary file"
date: 2009-10-17
forum: General Help
---

### Post by James Dee on 2009-10-17
Hi,

I tried to start licence server for installing AbaqusCae, but one error obtained during starting the server. It is this message:
```
/opt/abaqus681/License/lmgrd -c /opt/abaqus681/License/abaquslm.lic
bash: /opt/abaqus685/License/lmgrd: cannot execute binary file
```
I checked permission of the file.
```
ls -al
-rwxrwxrwx 1 root root 2295224 2005-05-23 21:22 lmgrd
```
```
file lmgrd
lmgrd: ELF 64-bit LSB executable, IA-64, version 1 (SYSV), for GNU/Linux 2.4.0, dynamically linked (uses shared libs), stripped
```
I tried also sh lmgrd and chmod a+x lmgrd, but didn't helped.
Can someone explain me what is a problem?

Thnx
James Dee

---

### Post by geurt on 2009-10-17
maybe the architecture isn't right. For example: 32 bit operating systems can not run 64 bit software.

---

### Post by James Dee on 2009-10-17
Is i686 describing that system is 64-bit? Am I wrong? How can I check is the system 32-bit or 64-bit?

```

uname -a
Linux danda-desktop 2.6.27-14-generic #1 SMP Mon Aug 31 13:01:41 UTC 2009 i686 GNU/Linux

```

---

### Post by geurt on 2009-10-17
i686 means that your operating system runs in 32 bit mode.
The binary you are trying to execute is compiled for a 64 bit architecture and will never run in your current 32 bit setup.

---

### Post by James Dee on 2009-10-17
thnx... you been very helpful.
:popcorn:

---

