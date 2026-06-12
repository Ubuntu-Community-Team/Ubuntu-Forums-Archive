---
title: "Nautilus USB HDD to HDD"
date: 2010-12-16
forum: General Help
---

### Post by DMKryl on 2010-12-16
Hi, for some events out of my control, i've moved my music from hdd  to my portable hdd (around 30gb), when i moved out nautilus went grey and i wasn't sure if it was copying, i left to solve some issues and when i came back still was grey and consuming 90% of the memory, i killed the process from a terminal and the music seems to be fine in the portable hdd, now i want to put back the music to my hdd, nautilus went grey again but this me it didn't copy the music,  what should i do?

---

### Post by oldfred on 2010-12-16
I like to use rsync with parameters that show progress, so then you know if it is working. USB drive may make it slow.

I copied this from my backup script.

# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."

#rsync -aruvP /mnt/data_DT/Documents /usr/local/fred/data/

I always have trouble getting parth correct so what I often do is use Nautilus to show partition and control-l (el, not I or 1) and copy and paste path. You can also add a parameter for test to check if you have it correct first. See man rsync. (I think it is the -n dry run).

---

### Post by DMKryl on 2010-12-17
thx worked like a charm

---

