---
title: "Hwo to share evolution profile between two different ubuntu versions"
date: 2009-11-25
forum: General Help
---

### Post by RodGer GR on 2009-11-25
Hello. I have Hardy Heron and Karmic Koala on my laptop and for the moment I use both. I'm used to experiment a little with different ubuntu versions and I have a separate ext3 partition, with all my files, which is accessible from every O.S. I also keep there my firefox profile. 

I tried to share my evolution profile. Copied the /home/rodger/.evolution folder and made a symlink to replace the respective folders in every installation.

I thought that this would do the job but it didn't. Can you please tell me if there is something I miss and if there is an other way to solve the problem?

I'll be grateful even if you just give me a hint.

---

### Post by RodGer GR on 2009-11-25
Finally I found [this]("https://help.ubuntu.com/community/MigrateEvolutionToNewComputer") which is not exactly what I wanted but it showed me that I also have to share the directories  ~/.gconf/apps/evolution and ~/.gnome2_private/Evolution except ~/.evolution.
Solved.

---

