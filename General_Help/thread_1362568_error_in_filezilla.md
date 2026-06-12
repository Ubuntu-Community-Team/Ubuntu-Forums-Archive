---
title: "error in filezilla"
date: 2009-12-23
forum: General Help
---

### Post by mohammed85 on 2009-12-23
Hello,

whenever I opened Filezilla in my ubuntu machine.I got the following error

can not open file 'home/mohammed/.kde/share/config/kdeglobals' permission denied?

I did not get that error before just recently? any thoughts?

---

### Post by 3rdalbum on 2009-12-23
It sounds like you ran Filezilla with "sudo" recently - which is a bad idea for two reasons:

1. Running a graphical program with "sudo" rather than "gksudo" will cause permissions to change in the manner you describe
2. If a remote attacker convinces Filezilla to run his commands, those commands will run as root and the attacker can gain complete control over your computer.
3. Any files downloaded with Filezilla when it is run as root, will be owned by root so your ordinary user account can't access them.

You can fix this problem by changing the permissions of that file so your user account can read and write it.

---

### Post by mohammed85 on 2009-12-23
thank you very much for that input...

how do I know if I am using filezill with sudo or gksudo?

How can I fix it so it will not run as a root  ( filezilla )?

---

### Post by 3rdalbum on 2009-12-23
> **mohammed85 said:**
> thank you very much for that input...

how do I know if I am using filezill with sudo or gksudo?

How can I fix it so it will not run as a root  ( filezilla )?

Normally it doesn't run as root. You would have to explicitly run it as root from the command-line. If you haven't done this, then your problem comes from something else.

---

### Post by mohammed85 on 2009-12-23
thanks...

anything I should do? because I have no idea how to proceed?

---

### Post by mohammed85 on 2009-12-23
does that error means that I am running Filezilla as a root?

---

