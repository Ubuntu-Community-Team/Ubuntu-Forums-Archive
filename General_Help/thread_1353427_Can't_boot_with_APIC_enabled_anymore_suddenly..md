---
title: "Can't boot with APIC enabled anymore suddenly."
date: 2009-12-12
forum: General Help
---

### Post by noobuntoo on 2009-12-12
I'm running version 9.04 of Ubuntu (Gnome)

ok this seems weird. Suddenly today when i boot up normally i get stuck. When it says "Starting up..." the cursor just blinks but it never boots.

So i tried doing it in recovery mode and it gets to the point
"[316001] Booting processor 1 APIC 0x2 ip 0x6000"
and again can go no further.

Seeing the mention of APIC where it hung i attempted to boot up with "noapic" added to the command line and then it booted normally.

Apparently out of nowhere APIC has stopped wotking and it has to be disabled to boot up at all. Anyone know how i can fix this?

I took a look at my update history to see if theres anything recently updated that could have broke it but im not sure. Heres what was updated before this problem happened.

Commit Log for Fri Dec 11 18:15:10 2009


Upgraded the following packages:
flashplugin-installer (10.0.32.18ubuntu0.9.04.1) to 10.0.42.34ubuntu0.9.04.1
flashplugin-nonfree (10.0.32.18ubuntu0.9.04.1) to 10.0.42.34ubuntu0.9.04.1
google-chrome-unstable (4.0.249.30-r33928) to 4.0.266.0-r33992
kde-icons-oxygen (4:4.2.2-0ubuntu1) to 4:4.2.2-0ubuntu1.1
kdebase-runtime (4:4.2.2-0ubuntu1) to 4:4.2.2-0ubuntu1.1
kdebase-runtime-bin-kde4 (4:4.2.2-0ubuntu1) to 4:4.2.2-0ubuntu1.1
kdebase-runtime-data (4:4.2.2-0ubuntu1) to 4:4.2.2-0ubuntu1.1
kdebase-runtime-data-common (4:4.2.2-0ubuntu1) to 4:4.2.2-0ubuntu1.1
kdelibs-bin (4:4.2.2-0ubuntu5.2) to 4:4.2.2-0ubuntu5.4
kdelibs-data (4:3.5.10.dfsg.1-1ubuntu8.2) to 4:3.5.10.dfsg.1-1ubuntu8.4
kdelibs4-dev (4:3.5.10.dfsg.1-1ubuntu8.2) to 4:3.5.10.dfsg.1-1ubuntu8.4
kdelibs4c2a (4:3.5.10.dfsg.1-1ubuntu8.2) to 4:3.5.10.dfsg.1-1ubuntu8.4
kdelibs5 (4:4.2.2-0ubuntu5.2) to 4:4.2.2-0ubuntu5.4
kdelibs5-data (4:4.2.2-0ubuntu5.2) to 4:4.2.2-0ubuntu5.4
khelpcenter4 (4:4.2.2-0ubuntu1) to 4:4.2.2-0ubuntu1.1
libplasma3 (4:4.2.2-0ubuntu5.2) to 4:4.2.2-0ubuntu5.4
wine (1.1.33~winehq0~ubuntu~9.04-0ubuntu1) to 1.1.34~winehq0~ubuntu~9.04-0ubuntu1
wine-dev (1.1.33~winehq0~ubuntu~9.04-0ubuntu1) to 1.1.34~winehq0~ubuntu~9.04-0ubuntu1

---

### Post by noobuntoo on 2009-12-12
-bump

nobodys had this occur to them recently?

---

### Post by justin_guerin on 2009-12-12
You might try booting with apic=debug and posting what you see happen.  Someone might be able to help with more specifics.

Justin

---

### Post by SkyNet2029 on 2009-12-12
did you also do a kernel update? that i could see affecting the apic, not the packages you listed.

---

### Post by noobuntoo on 2009-12-12
alright i solved this although im not entirely sure how.

you mentioned kernel update so i looked at the kernel i was using (2.6.28-16) and noticed that the most recent one that had been installed was 2.6.28-17.

For some reason grub wasn't updating itself to include it when i installed it

so..i ran this in terminal

sudo apt-get purge grub
sudo apt-get install grub
sudo update-grub

that fixed grub so that it displays the latest kernel version. rebooted and ran the latest kernel and the error is gone.

not sure why, because i had run all kinds of older kernels, even recovery mode, before and had the same error. updated grub and now no error. weird.

---

