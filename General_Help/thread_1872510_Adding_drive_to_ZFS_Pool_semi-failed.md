---
title: "Adding drive to ZFS Pool semi-failed"
date: 2011-10-30
forum: General Help
---

### Post by guy_smiley:) on 2011-10-30
Hi, I recently tried adding another 2TB drive to my zpool "tank" and it sort of worked. I believe I added with the command
sudo zpool attach tank disk/by-id/...
Which gave me this on a zpool status:
pool: tank
 state: ONLINE
 scrub: scrub completed after 9h54m with 0 errors on Mon Oct 31 04:26:10 2011
config:

	NAME                                                           STATE     READ WRITE CKSUM
	tank                                                           ONLINE       0     0     0
	  raidz1-0                                                     ONLINE       0     0     0
	    disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WCAZA3724999-part2  ONLINE       0     0     0
	    disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WCAZA6002254-part2  ONLINE       0     0     0
	    disk/by-id/ata-WDC_WD10EACS-00ZJB0_WD-WCASJ1251000-part2   ONLINE       0     0     0
	  disk/by-id/ata-WDC_WD20EARX-00PASB0_WD-WMAZA5894555          ONLINE       0     0     0

errors: No known data errors

Now I want to move this into the raidz1-0 but unfortunately whenever I try zpool replace... it tells me it belongs to the zpool already. Whenever I try zpool offline (or remove) it tells me that it's not a part of the "tank" zpool.

Any help would be much appreciated.

---

### Post by guy_smiley:) on 2011-10-30
Ok, so I needed to add /dev/... to my commands. But this still won't allow me to offline any drives. Now I'm almost 100% sure but I don't have any more SATA ports to play with extra drives.

---

