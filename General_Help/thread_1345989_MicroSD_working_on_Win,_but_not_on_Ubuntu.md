---
title: "MicroSD working on Win, but not on Ubuntu"
date: 2009-12-04
forum: General Help
---

### Post by Luca_turicci on 2009-12-04
Hi, I found a MicroSD i bought a lot ago when i had my old cellphone and hadn't used it because i had a 4gb one(this one is 2gb) but last week I had my phone repaired and they took the MicroSD. So, now i only have this 2gb one and it's working on my cellphone and on a windows, but not on Ubuntu, it doesn't even detect it. What should I do?

---

### Post by Luca_turicci on 2009-12-04
Desperate Bump!

---

### Post by NFblaze on 2009-12-04
I have a similar issue, although I use a microSdD to SD card converter. I find that sometimes it wouldnt mount in XP and sometimes it wouldnt mount in Ubuntu. It seems like what would fix it for me was to mount the card in whichever OS it would pop up, then safely remove it, and mount it in the other OS. Try it out. That's all I can suggest.

---

### Post by Luca_turicci on 2009-12-04
Nope, still not recognized...

---

### Post by Luca_turicci on 2009-12-06
I think i found the problem... but not the solution. I checked other SDs and they are formated into FAT16, mine is on FAT32, how can I format to FAT16 when it isn't even recognized in linux and WinXP doesn't let me format on FAT16?

---

### Post by llamabr on 2009-12-06
> **Luca_turicci said:**
> I think i found the problem... but not the solution. I checked other SDs and they are formated into FAT16, mine is on FAT32, how can I format to FAT16 when it isn't even recognized in linux and WinXP doesn't let me format on FAT16?

that shouldn't be the problem.  Often, when you remove it from windows, you don't properly unmount it.  So while it's in windows connected, there should be a little icon on the lower right that says 'safely remove connected device' or something.  You need to actually do this in windows, or else the filesystem will not be finalized.

After that, plug it into ubuntu, hang back 15 seconds or so, and post the output of:

```
dmesg | tail
```

---

### Post by Luca_turicci on 2009-12-06
Hi, I know how to safely remove HW, but I can't see the little green arrow in the bottom panel... o_o is it ok if a right click the drive and hit "Eject"?

---

### Post by Luca_turicci on 2009-12-06
I managed to follow those steps and this is what i got:

```
[   62.124602] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   62.124613] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   62.129209] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   62.129231]  sdb:
[   62.137707] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   62.137722] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   80.468338] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[   80.468371] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[   98.860475] sd 2:0:0:0: [sdb] Sense Key : No Sense [current] 
[   98.860501] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information


```

---

### Post by llamabr on 2009-12-06
Right.  Also, the output of:

```
df
```

While the thing is still plugged in.

---

### Post by Luca_turicci on 2009-12-07
```
S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/sda1            150902080  97857596  45379072  69% /
udev                    509088       260    508828   1% /dev
none                    509088       548    508540   1% /dev/shm
none                    509088        84    509004   1% /var/run
none                    509088         0    509088   0% /var/lock
none                    509088         0    509088   0% /lib/init/rw

```

---

