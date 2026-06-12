---
title: "mdadm and ubuntu 11.04 (how??) (non system disk)"
date: 2011-07-06
forum: General Help
---

### Post by anewbie on 2011-07-06
Note: the boot disk is not raid. 

I'm having a bit of a time trying to figure out how to setup mdadm under 11.04. Most of the old documentation refers to manual configuration of raidtab and mdadm.conf
-
I see that gparted and diskutils allow me to create the array but they do not allow me to set a mount point or auto mount on reboot.
-
I also see the syntax has created a bit. In my old system I have
/dev/md0 ...
/dev/md1 ...
in /etc/mdadm/mdadm.conf
and raidtab in /etc
-
In the new system (11.04) the system wants to refer to the device as /dev/md/:array_name
-
So the array is not referred to in /etc/mdadm/mdadm.conf but it is found on boot up and i can manually add it to /etc/fstab to auto mount on reboots.

This seems nifty (though I don not know how the system is finding the array) but when I did an apt-get upgrade to apply updates the kernel seemed to forget about the array when it built the new initram and now it won't auto mount on reboots.
-
So - is there an updated document that describes how this works and what I am suppose to be doing to have this auto mounted on reboots ?
-
I have three arrays: the new array (which I am testing with) which is raid1
two old arrays that I want to transfer to this new system (via moving the old disks) both are raid1 but one is encrypted. The encrypted one does not auto mount in the old system  - I use a script at boot up (which is fine for me; since I only reboot once a year and I have to enter the password anyways).
-
I guess I could maybe follow the old procedure but it seems like something changed since 8.04 (when I built the original arrays) and 11.04.
-
Anyways a bit of help; pointer to doc or information regarding missing pieces woudl help.

---

### Post by resistanceISuseless on 2011-07-29
I am in the same boat.  I have ubuntu up and running.  Now, I want to use mdadm for software RAID.  All the documentation I can find is either 'man' pages or how to install RAID while installing Ubuntu.  I don't need to install Ubuntu, just RAID.  I'm ok with command line, but there isn't a forum or help page that gives the steps.  I could be just flaking out on my google search's, but I'm not finding the info I need.  

Thank you ahead of time!

-resistanceISuseless

---

### Post by Habitual on 2011-07-29
this thread seems to point out the issue clearly.

[http://ubuntuforums.org/showpost.php?p=10953357&postcount=8](http://ubuntuforums.org/showpost.php?p=10953357&postcount=8)

HTH

---

### Post by anewbie on 2011-07-30
Yea I fixed the problem by adding the output of mdadm --scan --detail (old fashion way) to mdadm.conf.

I did not bother to remove the name option. Seems to work fine. I like the new idea very much (referring to arrays by name) but it seems to have some glitches and on at least one update they changed the name scheme which broke the mounting of the array (some minor change with usage of ':' in the name).

Good to know that if I have future problems i need to remove the 'name' option (per above link).
-
I never bother with mdadm for a system disk; easy enough to replace the system drive as long as user data is preserved.

---

