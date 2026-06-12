---
title: "FireFox Crashes with DOD CAC Inserted"
date: 2012-05-14
forum: General Help
---

### Post by mrcpuhead on 2012-05-14
I've just completed setup of my DOD CAC reader in Kubuntu 12.04 LTS.  I'm using the "coolkey" crypto module.  When I have the CAC inserted in the reader, and run Firefox, it immediately crashes.  As soon as I remove the CAC, Firefox runs fine.  Note that I had this working fine in 10.04 LTS. ](*,)

Turns out that even the latest version of coolkey doesn't work.  I had to remove everything related to the CAC reader, reinstall the needed components, replacing coolkey with cackey.  Then I could successfully install the device in FireFox!  :)

---

### Post by cclukins on 2012-06-09
I've heard that using the cackey module instead of coolkey works. You can get cackey from [forge.mil]("https://software.forge.mil/sf/frs/do/listReleases/projects.community_cac/frs.cackey") but you need to use a cac to log on to get access (I downloaded it at work and emailed it to myself). I, however, could never get my cac to work with 12.04. Actually had the same issue with Firefox crashing in 11.04 and 11.10, but Firefox would start back up with the cac inserted. I switched to Fedora and have had no problems using my cac to log on to AKO or DTS using coolkey. I don't know what the problem is, but I want to blame the Unity desktop ... and Al Gore. Not sure how either are to blame yet, but I want to blame them.

---

