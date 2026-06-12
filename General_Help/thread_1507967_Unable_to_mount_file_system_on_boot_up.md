---
title: "Unable to mount file system on boot up"
date: 2010-06-12
forum: General Help
---

### Post by oxf on 2010-06-12
OK here's the scenario:

I switch on the PC and it loads the Grub splash screen. However, it does not automatically boot the top entry after two seconds as it's supposed to and just hangs. I hit entry to boot it and it attempts to but after a few seconds gives me the error
"unable to mount file system....a maintenance shel will be started"
Where do I go from here? to figure out whats going on?

thanks

---

### Post by dino99 on 2010-06-12
boot and edit (e) the boot line: remove [COLOR="Blue"]quiet splash[/COLOR] at the end, then boot (x)

if that fail again, do the same thing and add nomodeset, then boot

---

### Post by oxf on 2010-06-12
> **dino99 said:**
> boot and edit (e) the boot line: remove [COLOR=Blue]quiet splash[/COLOR] at the end, then boot (x)

if that fail again, do the same thing and add nomodeset, then boot


Uhm I don't think thats doing anything, Ctrl X still takes me to the maintenance shell

---

### Post by oxf on 2010-06-12
I dont know if this has anything to do with the problem?

But just before this happened everything suddenly froze up on me. I tried to open a terminal but only the terminal window came up but nothing in it. I tried to restart/shut down, same story! Just an empty box with no options so had to kill the power.

Then when I re-booted ... problem as described above :confused:

---

### Post by dino99 on 2010-06-12
same setup than above with video=vesa (to boot)

---

### Post by oxf on 2010-06-12
> **dino99 said:**
> same setup than above with video=vesa (to boot)
  
OK thanks..

Well I presume you mean to put "video=vesa" at the end of the boot line? or after "quiet splash"? or doesn't it matter. Anyway it didn't seem to make any difference, I always end up back at the maintenance shell.

But.... if I can't mount the file system how does video settings affect it anyway, remember it wont mount the file sys after grub.  Can anyone explain>?

---

### Post by oxf on 2010-06-12
OK I fixed this by running fsck

---

### Post by Cold_Lyen_Fish on 2010-06-18
Thank you very much! 
I was able to fix this by running fsck, hitting yes for every request that the computer made.

Although, I'd like to kno why this happened (as described in the first post) because it wasnt a power shortage, since it was my laptop, the battery kicked in. I just shut it down correctly yesterday, tried to turn it on today and found that issue.

---

### Post by oxf on 2010-06-19
> **Cold_Lyen_Fish said:**
> Thank you very much! 
I was able to fix this by running fsck, hitting yes for every request that the computer made.

Although, I'd like to kno why this happened (as described in the first post) because it wasnt a power shortage, since it was my laptop, the battery kicked in. I just shut it down correctly yesterday, tried to turn it on today and found that issue.

My  theory as to why it happened to me was this. Previously I had  a couple of times when the OS was unable to read/write to the Hard Drive. I presume this happened again when the system froze on me.  After running several HD checks in the BIOS I pulled the HD out a couple of times, then cleaned the connector pins and the socket with a small brush and alcohol and firmly inserted it again and have no problems since.

---

