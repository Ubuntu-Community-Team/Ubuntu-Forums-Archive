---
title: "Kernel Panic after updates - /sbin/init"
date: 2010-08-17
forum: General Help
---

### Post by nightshade209 on 2010-08-17
Hi, i am unable to boot Ubuntu 10.04. I installed some updates this morning, and then shut down the PC. Ever since, i have been unable to boot it up again. Immediately after the BIOS screen, i get the message
```
Target filesystem doesn't have /sbin/init
run-init: /etc/init: Permission denied
[      1.342063] Kernel Panic - not syncing: Attempted to kill init!
```

I could not find any good solution for it. Tried running fsck from LiveCD, shows the FS to be clean.
I cannot even see the GRUB menu at bootup to go to a root prompt. (Though I usually do not see the GRUB menu, having set its time lapse to zero.)
I found a similar thread [_[COLOR="Red"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1554654"), though no one has replied to that.
Also, I came across a few articles that blamed the kernel panic on a hardware change, but that does not apply in my case as I have not moved anything more than my mousepad around.
I am running:
Ubuntu 10.04 on
160GB SATA HDD
1GB DDR2 RAM
2.2GHz Intel Dual Core Processor
Connected to the internet via PPPoE Broadband connection

Any help would be greatly appreciated!

---

### Post by nightshade209 on 2010-08-17
ok, problem hopefully solved - I am typing this from my Ubuntu installation, not the LiveCD. 
I did the following from the LiveCD though.
First, I mounted my installation at /mnt using```
mount /dev/sda1 /mnt
``` 
Then, I opened Nautilus as root ```
gksu nautilus
```
Then , i browsed to /mnt/sbin/init, opened its Properties>Permissions and selected Allow Read and Write for user root. Also, checked off the Allow Running File as Program box.
Then, browsed to /mnt/etc/init,, opened Properties of the entire folder> Permissions and selected Allow Read and Write for user root and clicked on Apply Permissions to Enclosed Files.
Then simply rebooted and it worked.
Note: One of the two steps might be unnecessary, but I am not going to go back and find out.

---

### Post by Daugminas on 2010-08-18
And nothing:(

---

### Post by praveenkovvuri on 2010-08-18
[SIZE=4]try to boot from the recovery mode...
hope u know how to boot from recovery mode...
press 'esc ' before the system start booting to enter to the recovery mode ...
After entering to recovery mode just copy the backup of /sbin/int and reboot.
[/SIZE]

---

### Post by nightshade209 on 2010-08-18
> **praveenkovvuri said:**
> [SIZE=4]try to boot from the recovery mode...
hope u know how to boot from recovery mode...
press 'esc ' before the system start booting to enter to the recovery mode ...
After entering to recovery mode just copy the backup of /sbin/int and reboot.
[/SIZE]

I don't know about any others, but my system wasn't booting up even to the recovery menu; so using that was out of question.

---

### Post by miserly-martyred on 2010-08-22
> **nightshade209 said:**
> I don't know about any others, but my system wasn't booting up even to the recovery menu; so using that was out of question.


yeah, I'm in the same boat, I have zero recovery options as that mode has the same failure rate...

---

### Post by Wafaa on 2010-11-01
Thank you! I also had the missing /sbin/init thing, only in my case, the whole sbin folder seemed missing. I copied and pasted it from the live cd one, changed the permissions, and now it works :)

---

### Post by ruff60series on 2011-10-30
Hi
We are experiencing similiar issues with booting error: Directory not found /sbin/init
We followed your previous steps and mounted the drive after booting with the live CD, gave /sbin/init full permissions, but this did not make any difference to our error. The plan to copy the /sbin/init from the Live CD sounded good, but I was unable to locate it on the CD? We are currently using version: Ubuntu 10.04.3  Can you help?

---

### Post by whiskers751 on 2012-03-18
It says permission denied on **/etc/init, **not /sbin/init...

---

