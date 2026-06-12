---
title: "I no longer have a user who can run sudo!"
date: 2011-06-23
forum: General Help
---

### Post by kevcoder on 2011-06-23
I was trying to add my user to a group and used the command ```
sudo usermod -G sambashare_kid dev
``` which left me with:)
```

uid=1000(dev) gid=1000(dev) groups=1000(dev),1002(sambashare_kid)

```Now I have no user in the adm or admin groups or any of the other groups I had when I installed the system!!!

How do I undo this big f*ck*p?

---

### Post by capscrew on 2011-06-23
> **kevcoder said:**
> I was trying to add my user to a group and used the command ```
sudo usermod -G sambashare_kid dev
``` which left me with:)
```

uid=1000(dev) gid=1000(dev) groups=1000(dev),1002(sambashare_kid)

```Now I have no user in the adm or admin groups or any of the other groups I had when I installed the system!!!

How do I undo this big f*ck*p?

Hi Kev,

Here are the pertinent sections of the adduser man pages```
  -a, --append
           [COLOR="Green"]**Add the user to the supplementary group(s).**[/COLOR] Use only with the -G
           option.

 -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
           A list of supplementary groups which the user is also a member of.
           Each group is separated from the next by a comma, with no
           intervening whitespace. The groups are subject to the same
           restrictions as the group given with the -g option.

           [COLOR="Blue"][B]If the user is currently a member of a group which is not listed,
           the user will be removed from the group. This behaviour can be
           changed via the -a option, which appends the user to the current
           supplementary group list.[/B][/COLOR]


```

---

### Post by kevcoder on 2011-06-23
> **capscrew said:**
> Hi Kev,

Here are the pertinent sections of the adduser man pages```
  -a, --append
           [COLOR=Green]**Add the user to the supplementary group(s).**[/COLOR] Use only with the -G
           option.

 -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
           A list of supplementary groups which the user is also a member of.
           Each group is separated from the next by a comma, with no
           intervening whitespace. The groups are subject to the same
           restrictions as the group given with the -g option.

           [COLOR=Blue][B]If the user is currently a member of a group which is not listed,
           the user will be removed from the group. This behaviour can be
           changed via the -a option, which appends the user to the current
           supplementary group list.[/B][/COLOR]


```
Hey capscrew,

Yeah... I was just reading that ;).  And I just got the share humming along.

So I guess this its time for a re-install.

---

### Post by gizmo720 on 2011-06-23
No need to reinstall your system. 

When you are at the grub boot menu, select recovery mode. This will allow you to log in as root without a password. Run visudo, and add ```
<user> ALL=(ALL) ALL

``` to the file. This will allow <user> to run sudo. If for some reason you can't get to this root shell, boot into a livecd, mount your ubuntu partion, and run```
sudo visudo -f /mnt/etc/sudoers
```and add the same line.

---

### Post by capscrew on 2011-06-23
> **gizmo720 said:**
> No need to reinstall your system. 

When you are at the grub boot menu, select recovery mode. This will allow you to log in as root without a password. Run visudo, and add ```
<user> ALL=(ALL) ALL

``` to the file. This will allow <user> to run sudo. If for some reason you can't get to this root shell, boot into a livecd, mount your ubuntu partion, and run```
sudo visudo -f /mnt/etc/sudoers
```and add the same line.

Why modify the system at all?  Once you are root in the recovery mode you can usermod to add the groups back that were removed.

From a practical point of view it is always better to leave the system as it was originally, than to make modifications upon what Kevin already said was his f**k up.  We all screw up once in awhile let's not compound that.  :-)

---

### Post by capscrew on 2011-06-23
> **kevcoder said:**
> Hey capscrew,

Yeah... I was just reading that ;).  And I just got the share humming along.

So I guess this its time for a re-install.

Not at all.  The recovery mode either from boot or from a LiveCD if you have to is all you need to do to get root access and reset the groups as they were using usermod.

---

### Post by kevcoder on 2011-06-23
> **capscrew said:**
> Not at all.  The recovery mode either from boot or from a LiveCD if you have to is all you need to do to get root access and reset the groups as they were using usermod.

I assume you mean as its outlined here ([http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)).

thing is, once i get past the BIOS POST stuff, my screen goes blank and I see a "invalid input method" message on my display until the login screen comes up.  My motherboard ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813186155](http://www.newegg.com/Product/Product.aspx?Item=N82E16813186155)) has NVIDIA GeForce 6100

I assume this is not normal.

---

### Post by capscrew on 2011-06-23
> **kevcoder said:**
> I assume you mean as its outlined here ([http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)).

thing is, once i get past the BIOS POST stuff, my screen goes blank and I see a "invalid input method" message on my display until the login screen comes up.  My motherboard ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813186155](http://www.newegg.com/Product/Product.aspx?Item=N82E16813186155)) has NVIDIA GeForce 6100

I assume this is not normal.

I have no experience with the nVidia chip set.  Your symptoms sure sound strange.  Do you have a liveCD?  When you boot into that it is as root.  No login needed.  At that point you will have to modify the /etc/group file directly.  That's all usermod does anyway.  I have done just that in the distant past.  Make a copy of that file first in case you FU again.  :-(

Edit: Unsaid was the fact that if you use the LiveCD you are not booting into the HDD installed OS.  You will have to mount the partition that has the file(s) you want to modify.  What is the partition setup on this host?  Is the /etc file system on the sda or sdb or...?

---

### Post by kevcoder on 2011-06-24
I'm back in business ya'll!!!!

I found the cd I used to install this thing and when the machine booted up it was in a "demo" install with me as a user called ubuntu and the partition already mounted.

but isn't that a huge security risk.  I just need an install disk and I'm into anybody's system I can get physical access to????

Will my Ubuntu 11.04 install disk do the same thing on another distro and visa-versa?

---

### Post by CharlesA on 2011-06-24
It's booted as a livecd, so yes it probably would have done the same thing.

---

### Post by redmk2 on 2011-06-24
> **kevcoder said:**
> I'm back in business ya'll!!!!

I found the cd I used to install this thing and when the machine booted up it was in a "demo" install with me as a user called ubuntu and the partition already mounted.

but isn't that a huge security risk.  I just need an install disk and I'm into anybody's system I can get physical access to????

Will my Ubuntu 11.04 install disk do the same thing on another distro and visa-versa?

Physical access is always a risk.  Yes you can boot up using the LiveCD and use it on Debian style distros like Ubuntu and Arch.  I wonder if it would be the same for Redhat distro's like RHEL, CentOS or Fedora though.  Lots of things are in different places.  You would just have to try it out to see.

---

### Post by collisionystm on 2011-06-24
Or even better, When you load a live cd onto a windows partition, passwords dont even exist lol. You can have free roam over any of the files on the windows drive.

---

### Post by LordNeo on 2011-06-24
Physical access is risky as redmk2 stated. It's probably the weakest link in the chain.
At least Linux lets you encrypt your whole Home folder so noone will access it without your password.
If you go to any other OS and boot live, you will have full access to the files and configurations of the owner, no password or anything needed.

---

