---
title: "updates broken"
date: 2009-12-16
forum: General Help
---

### Post by ufu1 on 2009-12-16
Hi. Please forgive me if this request isn't done properly

I think I'm a fairly technical user and enjoy playing around in ubuntu (it's great to have the power of the terminal) though ubuntu is the first version of linux i've used to any extent.

I was recently busy with an update after a fresh install when the pc shut down unexpectedly during update.
I can't remember if it shut down properly or was just powered off.
Update software would repeatedly not be able to resolve any update servers though once I switched server updates off and then on again (in Software Sources) this problem was fixed (just fixed this a few minutes ago)
It's been a few days since the update yet I don't get update notifications and when I try to update I'm told the system is up to date (new update lists do download)
I'm pretty sure the previous update did not complete before the system shut down.
I have no problem with rolling back to versions of software on the cd if possible without uninstalling a few other packages I've installed

I prefer using aptitude though i'm okay with apt-get or synaptic

Thanks in advance

Setup:
ubuntu 8.04 LTS
PIII 450
256MB  RAM
40GB HDD ubuntu, winXP dual boot
ubuntu main and swap partitions

---

### Post by ufu1 on 2009-12-16
Hi. Please forgive me if this request isn't done properly
 
I think I'm a fairly technical user and enjoy playing around in ubuntu (it's great to have the power of the terminal) though ubuntu is the first version of linux i've used to any extent.

I was recently busy with an update after a fresh install when the pc shut down unexpectedly during update.
I can't remember if it shut down properly or was just powered off.
Update software would repeatedly not be able to resolve any update servers though once I switched server updates off and then on again (in Software Sources) this problem was fixed (just fixed this a few minutes ago)
It's been a few days since the update yet I don't get update notifications and when I try to update I'm told the system is up to date (new update lists do download)
I'm pretty sure the previous update did not complete before the system shut down.
I have no problem with rolling back to versions of software on the cd if possible without uninstalling a few other packages I've installed

I prefer using aptitude though i'm okay with apt-get or synaptic

Thanks in advance

Setup:
ubuntu 8.04 LTS
PIII 450
256MB  RAM
40GB HDD ubuntu, winXP dual boot
ubuntu main and swap partitions

---

### Post by slakkie on 2009-12-16
What you could do is:

```

aptitude install ubuntu-minimal ubuntu-standard ubuntu-base
aptitude install ubuntu-desktop # assuming you run gnome

```

Those packages will make sure that all the packages of a default Ubuntu installation are present.

I don't know which repositories you have defined, but Hardy is pretty stable. If you installed it/upgraded it pretty recently it is not surprising you don't have many updates. Don't expect them on a daily basis.

---

### Post by ufu1 on 2009-12-16
Hi. Please forgive me if this request isn't done properly
  
I think I'm a fairly technical user and enjoy playing around in ubuntu (it's great to have the power of the terminal) though ubuntu is the first version of linux i've used to any extent.

I was recently busy with an update after a fresh install when the pc shut down unexpectedly during update.
I can't remember if it shut down properly or was just powered off.
Update software would repeatedly not be able to resolve any update servers though once I switched server updates off and then on again (in Software Sources) this problem was fixed (just fixed this a few minutes ago)
It's been a few days since the update yet I don't get update notifications and when I try to update I'm told the system is up to date (new update lists do download)
I'm pretty sure the previous update did not complete before the system shut down.
I have no problem with rolling back to versions of software on the cd if possible without uninstalling a few other packages I've installed

I prefer using aptitude though i'm okay with apt-get or synaptic

Thanks in advance

Setup:
ubuntu 8.04 LTS
PIII 450
256MB  RAM
40GB HDD ubuntu, winXP dual boot
ubuntu main and swap partitions

---

### Post by ufu1 on 2009-12-16
Hi. Please forgive me if this request isn't done properly
   
I think I'm a fairly technical user and enjoy playing around in ubuntu (it's great to have the power of the terminal) though ubuntu is the first version of linux i've used to any extent.

I was recently busy with an update after a fresh install when the pc shut down unexpectedly during update.
I can't remember if it shut down properly or was just powered off.
Update software would repeatedly not be able to resolve any update servers though once I switched server updates off and then on again (in Software Sources) this problem was fixed (just fixed this a few minutes ago)
It's been a few days since the update yet I don't get update notifications and when I try to update I'm told the system is up to date (new update lists do download)
I'm pretty sure the previous update did not complete before the system shut down.
I have no problem with rolling back to versions of software on the cd if possible without uninstalling a few other packages I've installed

I prefer using aptitude though i'm okay with apt-get or synaptic

Thanks in advance

Setup:
ubuntu 8.04 LTS
PIII 450
256MB  RAM
40GB HDD ubuntu, winXP dual boot
ubuntu main and swap partitions

---

### Post by NoaHall on 2009-12-16
Run these commands for me, and post the output of each one -

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by MaxIBoy on 2009-12-16
If, as you say, you are not notified of new updates, and the updates did not complete, try firing up Synaptic and looking for broken packages ("Custom filters" in the lower sidebar, then click "Broken" right underneath "All.")

If there are no broken packages, and "sudo apt-get update && sudo apt-get upgrade" don't show any updates, then there is probably nothing worth worrying about.

Unless, you know, it has refused to show any updates for a very long time.

---

### Post by MaxIBoy on 2009-12-16
Nuked for untruth.

---

### Post by NoaHall on 2009-12-16
> **MaxIBoy said:**
> NO! NO! NO! NO!

Skip this one. It will upgrade to the latest distro, which may or may not be what the original poster wants to do, but it's not foolproof and it's not what he asked for.

No it won't. It install packages - even if they need other packages removing/adding. Normal upgrade does not do this. dist-upgrade is without a doubt the command which will fix it if there are any huge problems. Please correct your post from your errors.

And your first post, the command is in the wrong order. You wish to upgrade the system before updating the list? Nice one.

---

### Post by ufu1 on 2009-12-16
root@user-desktop:~# sudo apt-get update
[INDENT]seems to run okay
[/INDENT]root@user-desktop:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

In synaptic : Custom Filters | Broken
[INDENT]No packages
[/INDENT]I guess I'll have to wait and see if I start getting updates again.
Thanks for the help

---

### Post by ufu1 on 2009-12-16
root@user-desktop:~# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by NoaHall on 2009-12-16
Right, in that case, all seems fine. Let us know if you haven't had any more updates in about 1 to 2 weeks.

---

### Post by ufu1 on 2009-12-16
kk. thanks

---

### Post by bodhi.zazen on 2009-12-16
> **noahall said:**
> no it won't. It install packages - even if they need other packages removing/adding. Normal upgrade does not do this.

+1

---

### Post by cariboo on 2009-12-16
Please don't create multiple threads on the same subject, I have merged your 4 threads.

---

