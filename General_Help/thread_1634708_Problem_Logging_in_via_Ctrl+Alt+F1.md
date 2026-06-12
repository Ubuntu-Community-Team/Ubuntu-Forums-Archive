---
title: "Problem Logging in via Ctrl+Alt+F1"
date: 2010-11-30
forum: General Help
---

### Post by Splat_NJ on 2010-11-30
Only about 1.5 weeks into Linux guys so bear with me. I'm trying to uninstall the Nouveau driver and install NVIDIA-Linux-x86-71.86.14-pkg1.run for my old Nvidia TNT2 card. Following these directions I run into a problem in the first step. :eek:  When I execute the Ctrl+Alt+F1 command and get:

Ubuntu 10.10 splat-desktop tty1
splat-desktop login: 

if I enter splat which I believe is my username and the correct p/w I get an incorrect login response. What now? Thanks guys.

---

### Post by 0949er on 2010-11-30
you are entering the same username/password you log on with at boot? you are using the password that you use for "sudo" and other authentication prompts?

---

### Post by Helkaluin on 2010-11-30
Do a ```
$ whoami
``` inside your graphical session to determine your username.

---

### Post by Splat_NJ on 2010-11-30
> **0949er said:**
> you are entering the same username/password you log on with at boot? you are using the password that you use for "sudo" and other authentication prompts?

I just now finally got my username and p/w to work. I had logged out, logged into Ubuntu then did the Ctrl+Alt+F1 and used my username and p/w and it finally took. Don't know why, but it worked.

---

