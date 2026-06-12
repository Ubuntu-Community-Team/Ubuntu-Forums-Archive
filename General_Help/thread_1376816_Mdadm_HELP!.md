---
title: "Mdadm HELP!"
date: 2010-01-09
forum: General Help
---

### Post by DarwinLabs on 2010-01-09
Sorry for the double post.

I am having issues with my raid 5 setup. I have created a raid 5 setup on a old machine before using 3 250GB drives and it worked great using this command

mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1

reboot the machine and all drives were apart of the md0 and everything worked great. so I created a new machine and I wanted to use 3 1TB drives so I proceeded as normal fdisk them to raid full partition. rebooted to make sure they got applied double checked setting stayed and ran the mdadm command above. except I get only roughly 1TB using 2 drives instead of the 3, so I let it create and it treats one of the drives as a spare so I let it continue thinking it would be okay but its not. When I reboot the box md0 doesn't show up and one of the drives is part of md_d0 so I have to stop it using mdadm --stop /dev/md_d0 and then reassemble the md0 with all 3 drives everytime. why is this happening can someone please help me. I also tried the --metadata=1.2 and the problem keeps happening.

---

### Post by Fcon_Vpro on 2010-01-10
This is a good guide: [http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/](http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/)

What does your /etc/mdadm/mdadm.conf file say?

---

### Post by DarwinLabs on 2010-01-10
There is no predefined partitions in the mdadm.conf
I had manually added it after the build by getting the details of the UUID from mdadm --query, and mdadm --detail commands then manually added it. but I was still running into the problem after the reboot of the server it would not bring up md0 it would show md_d0 in /proc/mdstat so I had to stop that and then reassemble all three drives under md0 and then restart everything again. I've done the create command that is in that guide and I'm still having the same effect but this time I will run those 2 extra commands to copy over to mdadm.conf and see if that helps. I've also replicated the same problem on a fresh install of 9.10 on a VM either 32 or 64 bit.

---

### Post by brainsick on 2010-01-10
Please provide the output of the following commands:

List the partitions:
```

sudo fdisk -l

```

Display mdadm device details:
```

sudo mdadm --detail /dev/md0
sudo mdadm --detail /dev/md_d0

```

Display mdadm drive details:
```

sudo mdadm --examine /dev/sda1
sudo mdadm --examine /dev/sdb1
sudo mdadm --examine /dev/sdc1

```

There shouldn't be any surprises here, but just for good measure:
```

cat /proc/mdstat

```

---

### Post by DarwinLabs on 2010-01-10
I will provide the outputs when the array has finished being created and if I run into the same problems again. that will take roughly 482.3 minutes.

---

### Post by DarwinLabs on 2010-01-11
Okay I re did everything the same I did for the 3(250GB) raid-5 arrray for the 3(1TB) and waited for it to finish and I manually added the output of sudo mdadm --detail --scan to the /etc/mdadm/mdadm.conf and then rebooted the box this time it worked all devices are part of md0. I appreciate everyones help. Thanks Fcon_Vpro for the link.

---

