---
title: "Can't Resume from standby"
date: 2011-03-05
forum: General Help
---

### Post by Ali.A on 2011-03-05
i am running Ubuntu 10.10 i386 on my computer

and i put my computer to standby

but when i tried resuming i couldn't 

i pressed EVERYTHING on my keyboard and i still couldn't resume so i  eventually had to shutdown the computer and start it up again

so... can anyone help me to solve this resuming problem

---

### Post by wiggly81 on 2011-03-05
did you try the computer power button? i think a short press should unlock standby

---

### Post by Ali.A on 2011-03-05
when i pressed the power button even for a short while the computer just shut down

---

### Post by ssulaco on 2011-03-05
Do you have a swap partition? I believe the ram drops your current session into swap before powering down.

---

### Post by Ali.A on 2011-03-05
No i don't think so

i do this with my windows xp and then it used to work fine

but ever since i have replaced windows xp with Ubuntu 10.10 desktop i386 i had this resuming from standby problem

(by the way how do i check if i have a swap partition)

---

### Post by highspider on 2011-03-05
> **Ali.A said:**
> 

(by the way how do i check if i have a swap partition)

The easy to check if you have swap partition is go to 
1) system->administrator->Disk utility 
2) click the hard disk
3) check the partition for one saying  
3) Partition type: SWAP

NOTE: you would have got a warning installing with out a swap partition during install and clicked yes to 
            continue the install


alternative methods:
check returns anything you have a swap
```

cat /etc/fstab | grep swap

```this ones better but you have to sudo and type password
```

sudo parted -l

```If it turns out you don't have a swap and you want one I would suggest using 
gparted
and resizing an existing partition to make room for a swap. Then of courses making a swap
You could apt-get or synaptic gparted but I don't know you partitions / file-system and you 
may need to resize an active partition which is easier from live cd.

---

### Post by highspider on 2011-03-06
> **Ali.A said:**
> 
i do this with my windows xp and then it used to work fine



windows xp doesn't use a partition for swap it just makes a file and writes data to file
Win386.swp  or pagefile

windows swap info
[http://www.aumha.org/win5/a/xpvm.php](http://www.aumha.org/win5/a/xpvm.php)

---

