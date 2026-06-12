---
title: "R/W Access on Second Drive?"
date: 2011-06-25
forum: General Help
---

### Post by homyakchik on 2011-06-25
[FONT="Courier New"]Hi, all

(I'll say up front that I *did* do some research on this ahead of asking. All the answers that search pulls up seem to deal with SAMBA shares rather than a second physical drive, which is my problem.)

Okay. Running (sadly) the newest Ubuntu (11.something), which is really a pain. However, that's neither here nor there; I'll deal with that my own self.

My PC has six hard drives (a sturdy old Dell). C: is my XP OS drive; totally devoted to XP and general-use programs. NTFS. D, E and F are all NTFS drives as well for different purposes (3D graphics, 2D graphics and audiovisual, in order). G: I specifically formatted as FAT32 so that it'd be automatically accessible from Ubuntu, as I intended to fully-install Ubuntu this time and give it a run for its money. Ubuntu has a drive all to itself (formatted with the linux file system), and just today I actually manually corrected where GRUB had gotten lost and lost me my Ubuntu install. Yay.

(And then I accepted that upgrade to version 11, which has been a headache from the get-go. I'm not suited for Utopia.)

Anyway: as said, the G drive was specifically formated to FAT32 and I somehow managed to get it auto-mounted at boot-up (wish I remembered how). However, while it auto-mounts and I can *see* everything on it (documents and MP3s), I don't have *write* access to it. As 75% of my PC use involves word processing, not being able to save the documents on my document drive is a real hardship.

I'm *assuming* that it's probably just a permissions mess-up somewhere that I can fix with chmod or the like, but the results from my searches are all coming up setting write permissions on network and SAMBA shares, and that's not the case here.

G: is a physical second drive next to the Ubuntu drive. It's currently read-only, and I'd like to set it (permanently) to read-write. Not overly concerned with security or anything, just the access.

Can anyone point me in the direction I need to be looking to solve this?

Thanks

Davey[/FONT]

---

### Post by Ozymandias_117 on 2011-06-25
Start by posting the output of ```
cat /etc/fstab
```

---

### Post by dcstar on 2011-06-25
> **homyakchik said:**
> 
......
Can anyone point me in the direction I need to be looking to solve this?

Thanks

Davey

[LIST=1]
[*]Please do not use strange fonts/formatting when posting.
[*]Install the **pysdm** package as it automates mounting of drives by writing the correct fstab entries for you (you may have to manually delete any existing entries).
[/LIST]

---

### Post by homyakchik on 2011-06-26
David said

> **dcstar said:**
> [LIST=1]
[*]Please do not use strange fonts/formatting when posting.
[*]Install the **pysdm** package as it automates mounting of drives by writing the correct fstab entries for you (you may have to manually delete any existing entries).
[/LIST]
[FONT="Courier New"]
I'll ask about #1 first. I've never seen a less strange typeface than Courier New; is that the one you were talking about? Looked okay on *my *screen. (And I was posting from my semi-crippled Ubuntu install, too.)

#2: I'll go look up pysdm here now and see if it'll help me. Thanks very much for pointing me in that direction.

Davey[/FONT]

---

