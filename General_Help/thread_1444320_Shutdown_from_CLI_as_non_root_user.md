---
title: "Shutdown from CLI as non root user"
date: 2010-04-01
forum: General Help
---

### Post by vikashtulsiyan on 2010-04-01
Hi
It seems little weird that i can shutdown my system (as non root user) from GUI but now from command line. 

I understand this may have to do with old unix tradition. I am now writing a script to shutdown systems after a certain period of inactivity. How do i shutdown system as non root users and without using sudo?

Also the shutdown option in GUI must be calling a command line internally. Which is that option? Can i use that to shutdown system as non root user?

---

### Post by cjhabs on 2010-04-01
> **vikashtulsiyan said:**
> Hi
It seems little weird that i can shutdown my system (as non root user) from GUI but now from command line. 

I understand this may have to do with old unix tradition. I am now writing a script to shutdown systems after a certain period of inactivity. How do i shutdown system as non root users and without using sudo?

Also the shutdown option in GUI must be calling a command line internally. Which is that option? Can i use that to shutdown system as non root user?

You can edit the sudoers file and allow some/all users to run shutdown without a password. I run my backup scripts that way.

---

