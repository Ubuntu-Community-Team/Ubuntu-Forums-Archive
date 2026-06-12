---
title: "problem problem and problem!!!!!"
date: 2009-08-25
forum: General Help
---

### Post by vikylov on 2009-08-25
my pc configuration is

amd 64 3500+
1gb ddr ram
asus a8vmx motherboard with via drivers
seagate 80 gb harddisk
maxtor basic 500gb

                  on this configuration windows xp  running fine with out any problem from the lat 3 yr  installed on the c drive....  
             but recently i tried to intall ubuntu9.04 and also ubuntu 8.04.but it never showed my seagate 80 gb in the partitioner and remarked no other os installed.then i thought may be there is some problem with the hard disk and took it to a friend pc where ubuntu intalled like in a zippy and even detecting the xp already installed on it.
            
             from the last 1 month i am trying ithout any success.......pl any 1 help me out.....

---

### Post by running_rabbit07 on 2009-08-25
Are you able to boot the LiveCD in the Boot without making changes option?

---

### Post by sedawk on 2009-08-25
Boot a LiveCD and then post the output of
```

dmesg | grep sd

```
and
```

sudo fdisk -l

```

---

### Post by running_rabbit07 on 2009-08-25
> **sedawk said:**
> Boot a LiveCD and then post the output of
```

dmesg | grep sd

```and
```

sudo fdisk -l

```

FYI In the second command that is a lower case L not an I or 1. (Easily mistaken.)

---

### Post by P4man on 2009-08-25
seems like this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267261](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267261)

In this thread:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209454](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209454)

They suggest a workaround, namely adding "pci=nomsi" as kernel parameter. If you feel like trying, boot the liveCD. When you get to the first screen where you select language and stuff, press F6 'other options'. Press esc to close the dialog, and after "quiet splash --" add "pci=nomsi" and press enter.

If that works, you will have to make that switch permanent after installing, its not hard, Ill tell you if thats needed.

TBH though, I would suggest you try another distro that is not bitten by this bug. From the bug report, it seems Mandriva works fine with that board, perhaps you can try that instead?

Also, if you feel like spending 5 minutes, please register for launchpad, and confirm that bug also affects you and note whether or not that workaround helped.

---

### Post by P4man on 2009-08-28
Any progress on this?

---

