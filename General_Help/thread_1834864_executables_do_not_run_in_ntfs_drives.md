---
title: "executables do not run in ntfs drives"
date: 2011-08-28
forum: General Help
---

### Post by vikashiiitdm on 2011-08-28
Dear all,
i've a ubuntu  11.04 system with gnome-3 installed in it. recently i wanted to shift some of my applications to one of my ntfs drives. but i noticed that the executables don't run from there. every-time i get a "permission denied" message. i tried to chmod the permissions with roots even, but it doesn't work. to check for whether this problem is with sage only or any executable i tried several others but every-time the same happens. i can't change permissions, especially setting executable bit . please help me out.

thank you,

vikash kumar

---

### Post by TeoBigusGeekus on 2011-08-28
Ntfs has no way of understanding linux permissions. Copy your executables from command line with the cp and the -p switch.

---

