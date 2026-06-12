---
title: "hard crash during drive backup"
date: 2009-07-31
forum: General Help
---

### Post by Ubermouser on 2009-07-31
I'm having difficulty with an intermittent hard crash in Ubuntu-9.04 AMD64 when attempting large file operations like backing up to a portable drive (every few minutes), or very intermittently (once or twice weekly) with regular use. Upon hard crash, the machine no longer accepts any incoming ssh connections or responds to existing ssh connections, and (as far as I know) the logs found in /var/log don't contain anything out of the ordinary around the time this occurs. The screen appears "frozen", the computer does not accept input from the keyboard or mouse, and all sound immediately cuts out. I'm hesitant to assume that this is a hardware problem due to the computer's exemplary uptime using Windows Vista (upwards of 12 months without a crash or bluescreen) How would I go about attempting to solve this problem?

**Things done so far:**
[LIST]
[*]chkdsk on the NTFS drive returned no errors or problems. (the NTFS drive is the drive in which I need to backup)
[*]attempted to perform backup with samba on the Ubuntu-9.04 AMD64 liveCD instead. Same crash during backup with the liveCD.
[*]attempted to perform backup with sftp, ftp, and samba. All 3 tests resulted in a crash during backup.
[/LIST]

**Computer's operating system:**
Ubuntu - Jaunty (9.04) AMD64

**Computer's hardware:**
Q6660 Intel Quad-Core processor @2.4ghz
4gb G-Skill ram
Abit IP-35 PRO motherboard
eVGA Nvidia 8800GT GPU (twinview)
-Hanns-G HG281D Monitor
-Samsung Syncmaster 204B Monitor
M-Audio Revolution 5.1 Sound Card
Logitech G-15 Keyboard
Logitech MX-Revolution Mouse

**Computer media:**
Western Digital Raptor (150gb)
EXT3: /boot
EXT4: /
Western Digital Caviar (740gb)
SWAP: ?
NTFS: /storage  (the drive being backed up)

**Any help you can give is MUCH APPRECIATED! More information available on request.**

---

