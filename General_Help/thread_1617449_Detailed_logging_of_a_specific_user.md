---
title: "Detailed logging of a specific user"
date: 2010-11-09
forum: General Help
---

### Post by Calcipher on 2010-11-09
I don't really want to go into details of how we got into this situation, but we are in a place where we have to give an account (with sudo access...) to a user we don't completely trust ([I am reminded of this comic]("http://dilbert.com/2010-11-05/")).  What we need to set up is some way of logging pretty much everything that this user does, especially what he does as root (via sudo or sudo -s).  Now, I know that anything we do can easily be undone by another user with root access, but we feel that if he does disable logging we can use this as a really good excuse to revoke his access.  So, does anyone know what logging stuff I'd have to set up to completely monitor one user (it is ok if we are monitoring everyone, but we'd prefer to watch one user if possible)?

---

### Post by CharlesA on 2010-11-09
Best thing to do would be to contact your IT guys and let them deal with it.

By default, any command executed with sudo is logged.

Thread reopened after speaking with OP.

---

### Post by Calcipher on 2010-11-10
> **CharlesA said:**
> Best thing to do would be to contact your IT guys and let them deal with it.
Per CharlesA's request, I am replying with a few additional details.  First off, I am the IT guy at our organization and I am aware that sudo has logging enabled.  The system in question is a fairly important server running Ubuntu and we have been asked by our bosses to monitor all actions that the user (we'll call him Mr. S-) will be doing on said server.

The logs from sudo are a good start, but we would like to go a little farther in depth and I was wondering if anyone out there had any experience in this.  We need to know what Mr. S- has logged in, what he was doing while he was logged in, and any changes that we need to roll back.  The machine is in production and it is our policy that any changes are supposed to be reviewed by a change request process, but we do not trust Mr. S- to abide by these policies.  CharlesA, in a PM, suggested I read [Linux Administrator's Security Guide - Linux System and User Logging](http://www.linuxtopia.org/online_books/linux_administrators_security_guide/08_Linux_System_and_User_Logging.html), but I am still open to other ideas.

---

### Post by houseworkshy on 2010-11-10
Rather iffy subject as people with dodgy intent could use the info too.  Maybe the best solution would be to set up an accout with high but not admin privalages so keeping the core of things away from the suspect person.  Ap-armour may be useful too.

---

### Post by wojox on 2010-11-10
```
[wojox@wojox-desktop ~]$ dmesg | grep wojox
[    0.000000] Command line: ro root=/dev/mapper/vg_wojoxdesktop-lv_root rd_LVM_LV=vg_wojoxdesktop/lv_root rd_LVM_LV=vg_wojoxdesktop/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us nomodeset rhgb quiet nouveau.modeset=0 rdblacklist=nouveau
[    0.000000] Kernel command line: ro root=/dev/mapper/vg_wojoxdesktop-lv_root rd_LVM_LV=vg_wojoxdesktop/lv_root rd_LVM_LV=vg_wojoxdesktop/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us nomodeset rhgb quiet nouveau.modeset=0 rdblacklist=nouveau
[    2.759883] dracut: Scanning devices sda2  for LVM logical volumes vg_wojoxdesktop/lv_root vg_wojoxdesktop/lv_swap 
[    2.774701] dracut: inactive '/dev/vg_wojoxdesktop/lv_root' [50.00 GiB] inherit
[    2.774782] dracut: inactive '/dev/vg_wojoxdesktop/lv_home' [133.47 GiB] inherit
[    2.774855] dracut: inactive '/dev/vg_wojoxdesktop/lv_swap' [2.34 GiB] inherit
[    3.220038] dracut: Mounted root filesystem /dev/mapper/vg_wojoxdesktop-lv_root
[   18.032405] Adding 2457596k swap on /dev/mapper/vg_wojoxdesktop-lv_swap.  Priority:-1 extents:1 across:2457596k 
[  114.659641] type=1100 audit(1289329823.466:24570): user pid=1729 uid=0 auid=4294967295 ses=4294967295 subj=system_u:system_r:xdm_t:s0-s0:c0.c1023 msg='op=PAM:authentication acct="wojox" exe="/usr/libexec/gdm-session-worker" hostname=? addr=? terminal=:0 res=success'
[  114.665897] type=1101 audit(1289329823.472:24571): user pid=1729 uid=0 auid=4294967295 ses=4294967295 subj=system_u:system_r:xdm_t:s0-s0:c0.c1023 msg='op=PAM:accounting acct="wojox" exe="/usr/libexec/gdm-session-worker" hostname=? addr=? terminal=:0 res=success'
[  114.681771] type=1103 audit(1289329823.489:24572): user pid=1729 uid=0 auid=4294967295 ses=4294967295 subj=system_u:system_r:xdm_t:s0-s0:c0.c1023 msg='op=PAM:setcred acct="wojox" exe="/usr/libexec/gdm-session-worker" hostname=? addr=? terminal=:0 res=success'
[  114.935976] type=1105 audit(1289329823.742:24575): user pid=1729 uid=0 auid=500 ses=1 subj=system_u:system_r:xdm_t:s0-s0:c0.c1023 msg='op=PAM:session_open acct="wojox" exe="/usr/libexec/gdm-session-worker" hostname=? addr=? terminal=:0 res=success'
[13420.598438] type=1100 audit(1289343129.405:24601): user pid=2540 uid=500 auid=500 ses=1 subj=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023 msg='op=PAM:unix_chkpwd acct="wojox" exe="/sbin/unix_chkpwd" hostname=? addr=? terminal=? res=success'
[66265.186533] type=1100 audit(1289395973.993:24698): user pid=4170 uid=500 auid=500 ses=1 subj=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023 msg='op=PAM:unix_chkpwd acct="wojox" exe="/sbin/unix_chkpwd" hostname=? addr=? terminal=? res=success'
[67101.472166] type=1100 audit(1289396810.279:24699): user pid=4255 uid=500 auid=500 ses=1 subj=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023 msg='op=PAM:unix_chkpwd acct="wojox" exe="/sbin/unix_chkpwd" hostname=? addr=? terminal=? res=success'
```

---

### Post by Calcipher on 2010-11-10
[QUOTE=houseworkshy]Rather iffy subject as people with dodgy intent could use the info too.[/quote]Yeah, I'm worried that perhaps these aren't the best forums for this kind of discussion. I suppose I could jump over to usenet or something like StackOverflow if things get too useful.  I think Wojox's reply, on the other hand, is a good example of something that was useful to me, but might require a bit too much research for most (thanks Wojox, that is a good method - in your experience, how fast does dmesg fill up?).

---

### Post by SeijiSensei on 2010-11-10
Personally if I were that worried about Mr S, I wouldn't give him sudo on a production server.  Why not make a clone of the production box, let him have sudo on that, then review the changes and replicate them on the production server if appropriate?

I once had a client that was running a proprietary manufacturing system on Linux. The company that provided the software wanted to upgrade one of the boxes over the weekend and told us that everything would be working properly on Monday.  I objected and enforced the same arrangement I described above.  We cloned the production server and let them upgrade that.  *Two weeks later*, they finished the upgrades that were supposed to take only a weekend to complete.  That single event more than financially justified my monthly retainer for at least another year :)

---

### Post by CharlesA on 2010-11-10
> **SeijiSensei said:**
> Personally if I were that worried about Mr S, I wouldn't give him sudo on a production server.  Why not make a clone of the production box, let him have sudo on that, then review the changes and replicate them on the production server if appropriate?

That would be a good idea. I know I've got a VM replica of my server that I test changes on for that very reason.

---

### Post by Calcipher on 2010-11-10
> **SeijiSensei said:**
> Personally if I were that worried about Mr S, I wouldn't give him sudo on a production server.Would if I could.  This is what happens when non-IT staff make decisions with no regards to what IT has suggested.

> **SeijiSensei said:**
> Why not make a clone of the production box, let him have sudo on that, then review the changes and replicate them on the production server if appropriate?That is an interesting idea actually.  I'm not sure I can fully do this as Mr. S- is to 'have access to this physical server', but that reminded me of chroot...

> **SeijiSensei said:**
> *Two weeks later*, they finished the upgrades that were supposed to take only a weekend to complete.  That single event more than financially justified my monthly retainer for at least another year :)Why on earth are people so bad at estimating how long a process will take them or how invasive it will be.  Out of curiosity, what tools did you use to clone the machine and were you required to merge the cloned and production machine when your client was done?

---

### Post by SeijiSensei on 2010-11-10
I think I just installed a fresh copy of RHEL onto the clone box, then used rsync to transfer the additional software.  Most of the software company's stuff was located in just a few directories like /opt and a home directory so it wasn't that hard to transfer.  All the important data was in an Oracle database.  After they finished we copied the upgraded directories back onto the production box.  It started up fine and got what it needed from the untouched Oracle DB.  (This was a few years' ago now so my memory is a bit cloudy.)

Chroot might be an option.  You'd probably have to replicate the server's entire directory tree below the chrooted directory to guarantee the installation would appear identical to working from the actual root.  I've only used chroot on a couple of occasions, like with named on RedHat/CentOS or with an FTP server where you want to force users into a chrooted jail.  Usually you just need to replicate a few directories like bin and populate the appropriate branches like usr/bin and usr/sbin with the required binaries.

---

### Post by houseworkshy on 2010-11-10
Just a thought, whatever you do with the man software wise ( sandboxing does sound good ) don't forget to password lock the bios and disable all boots bar the hard drive.  Though even that can be got round, someone opening the box and playing mechano would probably be noticed by collegues in an office enviroment.

---

