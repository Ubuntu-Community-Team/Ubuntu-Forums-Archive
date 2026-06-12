---
title: "Error during installtion; now I don't have XP now."
date: 2009-11-20
forum: General Help
---

### Post by Karlos2394 on 2009-11-20
Basically I was installing Ubuntu, and I basically got an error (partitioning, I believe) and I don't have Windows XP SP2 either now...

Any ideas how I can get Windows back?

---

### Post by gradinaruvasile on 2009-11-20
More specifically what happened and what error was it? And what happens now if you try to boot?

---

### Post by r_s on 2009-11-20
you can always use windows recovery for recovering your lost partition (only if you have a recovery partition)

---

### Post by phillw on 2009-11-20
Hi,

How far did you get with the partitioning, what were you trying to do ?

The partitioning shouldn't let you make the XP area too small - so it should still be sat there.

can you post the output of

```
$ df -h
```

Regards,

Phill.

---

### Post by Karlos2394 on 2009-11-20
I can't remember the specific error, but it happened while the partioning was going on.
I was installing Ubuntu 8.10 Desktop Edition (CD)..

I kept receiving **Boot From CD: MBR error**
I have since then reinstalled Ubuntu and I was wondering if I could get XP back?

---

### Post by Karlos2394 on 2009-11-20
philw: I roughly got 90% of the way through and as I see there is no XP parition.
And as for the results, I'm not sure what to do with that snippet.. I'm a total Ubuntu n00b hence I wanted to keep it side by side with Windows.

---

### Post by phillw on 2009-11-20
Hi,

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

You'll be wanting the 'windows isn't showing' bit of it !!!

Regards,

Phill.

---

### Post by Karlos2394 on 2009-11-20
Thanks for the help so fare phillw.
However I followed what it had to say and it still hasn't worked.

It looks like XP has been wiped from the system.

---

### Post by gradinaruvasile on 2009-11-20
U should check the integrity of the install cd.

---

### Post by Karlos2394 on 2009-11-20
I did, the results come back fine.

---

### Post by phillw on 2009-11-20
> **Karlos2394 said:**
> Thanks for the help so fare phillw.
However I followed what it had to say and it still hasn't worked.

It looks like XP has been wiped from the system.


If you can pop on the results of ```
df -hT
```I'll be able to see what partitions etc you have. To copy FROM the terminal, triple click on the line you want to copy then  SHIFT-CTRL V to copy. You can then use CTRL P to paste it into here.

Phill.

---

### Post by Karlos2394 on 2009-11-20
```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3     73G  3.2G   67G   5% /
tmpfs        tmpfs    107M     0  107M   0% /lib/init/rw
varrun       tmpfs    107M  104K  107M   1% /var/run
varlock      tmpfs    107M     0  107M   0% /var/lock
udev         tmpfs    107M  144K  107M   1% /dev
tmpfs        tmpfs    107M  120K  107M   1% /dev/shm
lrm          tmpfs    107M  2.2M  105M   3% /lib/modules/2.6.28-16-generic/volatile

```

Looks like it's not there...

---

### Post by phillw on 2009-11-20
Yup ... It's gone :-(

Can't get the data back, sorry. If you want to put XP back on

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Has the instructions

Regards,
Phill.    WHOA ... hang on a mo !!!

---

### Post by phillw on 2009-11-20
Run a Gparted Live CD - The partition may still be there - just not mounted.

It's worth getting Gparted to have a look and see if the partition is still there

You're looking to see if dev/sda1 shows up as a windows partition - if it is there it can be mounted :-D

Phill.

---

### Post by Karlos2394 on 2009-11-20
I'll try his first and hopefully it will be there...

However I didn't get a boot CD from the supplier when I brought it, so how much am I looking at to buy one?

---

### Post by phillw on 2009-11-20
> **Karlos2394 said:**
> I'll try his first and hopefully it will be there...

However I didn't get a boot CD from the supplier when I brought it, so how much am I looking at to buy one?

I'm not sure how much they cost. They've had to stop shipping them for free - too many requests = too much postage.  If your CD has passed its md5 check then that IS a LiveCD - the one you buy is exactly the same, just doesn't have hand written 'koala 9.10' on it (like mine does !!!)

Phill.

---

### Post by phillw on 2009-11-20
'T'-Shirts, mice, stickers etc. etc. are available from  [https://shop.canonical.com/](https://shop.canonical.com/)

Phill.

---

### Post by Karlos2394 on 2009-11-20
The gparted idea didn't work, do you know where I could get a XP boot CD from?

---

### Post by phillw on 2009-11-20
what partitions did GParted show ?

Phill.

You'll have to beg or borrow an XP disk - I'm assuming your computer still has the XP licence sticker on it. - Were you on Home or Pro ?

---

### Post by Karlos2394 on 2009-11-20
Just some of the ones the terminal showed us.. And yea it sure does have the licence sticker on it.
I was on Home Edition.

---

### Post by phillw on 2009-11-20
I can pop an iso image onto a file area later on for you and also pop the SP3 iso on as well. Can you private message me an email address to send the invite to for you to collect it.

Phill.

---

### Post by Karlos2394 on 2009-11-20
Ahh thank you very much! I'll do it right away.

---

### Post by phillw on 2009-11-20
Hmm, the site i usually use won't upload the iso file ... I'll go have a look at another site - bbs

Phill.

---

### Post by Karlos2394 on 2009-11-20
I have an alternative.. I'll PM you..

---

### Post by phillw on 2009-11-20
> **Karlos2394 said:**
> I have an alternative.. I'll PM you..

I'm going to get a bite to eat (been on duty 7 hours .. hungry) - I'll be back in abt an hour.

---

### Post by Karlos2394 on 2009-11-20
Yea okay, and thanks again.. I appricate what your doing.

---

### Post by phillw on 2009-11-20
> **Karlos2394 said:**
> Yea okay, and thanks again.. I appricate what your doing.

u have mail.

---

### Post by Karlos2394 on 2009-11-20
Ahh, replied.

---

### Post by Karlos2394 on 2009-11-21
Cheers Phillw, I have the .bin files on a CD so I put the CD in and restarted the computer, however I still goes to the screen where I choose to go onto Ubuntu.. 

Many regards,
Karl2394

---

