---
title: "ubuntu 9.10 installation"
date: 2010-01-29
forum: General Help
---

### Post by ubunbuntu on 2010-01-29
i am trying to install ubuntu 9.10 desktop on my pc installed with windows xp. i downloaded iso image, checked the md5sum , burnt the cd. now i am trying to insert the cd to install ubuntu software. after pressing f12 ,i can see ubuntu options like english,after i select english, it showed options like install ubuntu,check cd for damages.
no matter which option i select i can only see a blank screen with underscore at leftmost top. i tried to google it, but i never found an exact solution . can someone provide me a solution.

---

### Post by cjhabs on 2010-01-29
I have seen this with Windows - maybe not the same - but it affected booting off the XP recovery cd disk also.
I had replaced the PC drive with a larger one and configured it as a single partition (230gb) - it worked under XP for a couple of months then stopped booting with the problem you describe (and the recovery cd had the same issue).
The problem was that the BIOS could not handle a boot partition greater than 130gb - I have no idea why it worked for a while and then quit - maybe due to how much the disk was filled (not much)?

Anyway, I booted off Parted Magic Linux distro, repartitioned, and after running chkdisk, everything was great.

Just FYI.

---

### Post by ubunbuntu on 2010-01-29
> **cjhabs said:**
> I have seen this with Windows - maybe not the same - but it affected booting off the XP recovery cd disk also.
I had replaced the PC drive with a larger one and configured it as a single partition (230gb) - it worked under XP for a couple of months then stopped booting with the problem you describe (and the recovery cd had the same issue).
The problem was that the BIOS could not handle a boot partition greater than 130gb - I have no idea why it worked for a while and then quit - maybe due to how much the disk was filled (not much)?
 
Anyway, I booted off Parted Magic Linux distro, repartitioned, and after running chkdisk, everything was great.
 
Just FYI.
 i tried to install from windows xp ,opening it from cd drive and install it,when i rebooted  it created an option for ubuntu os ,when i tried to select ubuntu os option it showed an windows error ,hal.dll s corrupt or missing. however my windows xp is working fine.
FYI the windows xp is newly installed so there is enough disk space.

---

