---
title: "Need help with Grub / Grub2 problems"
date: 2010-01-07
forum: General Help
---

### Post by sparky2 on 2010-01-07
I had everything running fine, my machine dual-booting into either unbuntu 9.10 or Windows XP. Then I got into strife mucking around with what I though was a dead partition... then all I got at boot was grub-rescue> prompt ... oops!

Anyway I worked through that and now I get ubuntu 9.10 up again, but I need to reinstate Windows into boot menu. The complication is I've somehow ended up booting via the older Grub menu.lst mechanism (it's a long story ...:oops:

I tried to upgrade to Grub 2 using "sudo apt-get update" but get a whole bunch of errors like ... 
could not resolve 'security.ubuntu.com'

I did succeed installing the startup manager, and this seems to be able to see Grub2 startup entries, inluding Windows XP, but I can't figure how to convince system to use Grub2 and not menu.lst.

Help !!

---

### Post by boosterjet on 2010-01-07
I don't know whether this is of any help, had similar problems which were solved on the Installation and Upgrade forum. Here is my thread if you would like to take the time to read it - it is rather a saga but you may find something useful in it.
 
[http://ubuntuforums.org/showthread.php?t=1373378](http://ubuntuforums.org/showthread.php?t=1373378)

---

### Post by sparky2 on 2010-01-08
Man that is some thread. Didn't read it all but I scanned through it to the end and got the gist. Your post with the dump of info is about as long as I've ever seen on any forum :shock:, and ***kansasnoob*** was just brilliant in the way he helped you.

I think I have the same problem, probably caused by me naively using out of date grub guides while trying to recover! :frown: 

But there's a few permutations in your thread that may not apply to me so I think my best hope is to seek kansasnoob's help direct. I'll PM him...

thanks

---

### Post by kansasnoob on 2010-01-08
Just saw your PM. I need to know if you can still boot or not and regardless I need to see the output of that Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

And, if you can still boot please include the output from Terminal of:

```
ls /boot
```

We should be able to handle this.

---

### Post by sparky2 on 2010-01-08
great stuff kansasnoob. apologies for tardy response but I'm on holidays so sleeping in a lot :) also our time zones are about 17 hours apart, if your in kansas USA ?!

Yes I can boot into karmic OK. I've attached results.txt and a screenshot for ls /boot (I don't know how to direct terminal output into a text file ... yet?)

sda8 used to contain ubuntu 8.xx ... that was the partition I tried to reclaim that started me down this rocky slope. Hence there are two swap partitions sda5 and sda7. I think sda7 was for ubuntu 8 and sda5 is active for ubuntu 9.10. (I don't care to touch either at present !)

also the response to grub-install -v is 0.97

---

### Post by kansasnoob on 2010-01-09
Well things don't look too bad, you do have mixed grub and grub2 files/directories but we can deal with that.

Reviewing things I have one major concern:

> I tried to upgrade to Grub 2 using "sudo apt-get update" but get a whole bunch of errors like ...
could not resolve 'security.ubuntu.com'

Before we even begin fixing grub I need you to look at Software Sources and see what server is selected. Look here:

[http://ubuntuforums.org/showpost.php?p=8616517&postcount=20](http://ubuntuforums.org/showpost.php?p=8616517&postcount=20)

For now just change to Main Server and run "sudo apt-get update" again.

At the moment I'm too tired to handle anymore but I'll check back in 4 or 5 hours.

---

### Post by kansasnoob on 2010-01-09
I hope you got package management straightened out? When you run "sudo apt-get update" does it still show errors?

There seems to be intermittent trouble with the Australian server, I don't know why.

Just to be sure the packages grub-pc and grub-common are available for reinstallation go to Terminal and run:

```
apt-cache showpkg grub-common grub-pc
```

You'll see a huge output like this if things are right (I highlighted the important stuff):

> lance@lance-desktop:~$ apt-cache showpkg grub-common grub-pc
[B]Package: grub-common
Versions: 
1.97~beta4-1ubuntu4.1[/B] (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-i386_Packages) (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-security_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-i386_Packages
                  MD5: 6398df3f52b0fcc204d8b8ab24aa7158

1.97~beta4-1ubuntu3 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
                  MD5: 6398df3f52b0fcc204d8b8ab24aa7158


Reverse Depends: 
  grub-ieee1275,grub-common 1.97~beta1-1ubuntu4
  grub-ieee1275,grub-common 1.97~beta4-1ubuntu4.1
  grub-emu,grub-common 1.97~beta3-1
  grub-efi-ia32,grub-common 1.97~beta1-1ubuntu4
  grub-efi-ia32,grub-common 1.97~beta4-1ubuntu4.1
  grub-efi-amd64,grub-common 1.97~beta1-1ubuntu4
  grub-efi-amd64,grub-common 1.97~beta4-1ubuntu4.1
  grub-coreboot,grub-common 1.97~beta1-1ubuntu4
  grub-coreboot,grub-common 1.97~beta4-1ubuntu4.1
  grub-pc,grub-common 1.97~beta1-1ubuntu4
  grub-pc,grub-common 1.97~beta4-1ubuntu4.1
  grub-pc,grub-common 1.97~beta4-1ubuntu4.1
  grub-ieee1275,grub-common 1.97~beta1-1ubuntu4
  grub-ieee1275,grub-common 1.97~beta4-1ubuntu3
  grub-emu,grub-common 1.97~beta3-1
  grub-efi-ia32,grub-common 1.97~beta1-1ubuntu4
  grub-efi-ia32,grub-common 1.97~beta4-1ubuntu3
  grub-efi-amd64,grub-common 1.97~beta1-1ubuntu4
  grub-efi-amd64,grub-common 1.97~beta4-1ubuntu3
  grub-coreboot,grub-common 1.97~beta1-1ubuntu4
  grub-coreboot,grub-common 1.97~beta4-1ubuntu3
  grub-pc,grub-common 1.97~beta1-1ubuntu4
  grub-pc,grub-common 1.97~beta4-1ubuntu3
  grub-pc,grub-common 1.97~beta4-1ubuntu3
  grub,grub-common
Dependencies: 
1.97~beta4-1ubuntu4.1 - libc6 (2 2.8) libfreetype6 (2 2.2.1) zlib1g (2 1:1.1.4) base-files (2 4.0.1~) lsb-base (2 3.0-6) multiboot-doc (0 (null)) grub-emu (0 (null)) os-prober (2 1.33) grub-doc (3 0.97-32) grub-legacy-doc (3 0.97-59) mdadm (3 2.6.7-2) grub-coreboot (3 1.96+20080831-1) grub-efi (3 1.96+20080831-1) grub-ieee1275 (3 1.96+20080831-1) grub-linuxbios (3 1.96+20080831-1) grub-pc (3 1.96+20080831-1) 
1.97~beta4-1ubuntu3 - libc6 (2 2.8) libfreetype6 (2 2.2.1) zlib1g (2 1:1.1.4) base-files (2 4.0.1~) lsb-base (2 3.0-6) multiboot-doc (0 (null)) grub-emu (0 (null)) os-prober (2 1.33) grub-doc (3 0.97-32) grub-legacy-doc (3 0.97-59) mdadm (3 2.6.7-2) grub-coreboot (3 1.96+20080831-1) grub-efi (3 1.96+20080831-1) grub-ieee1275 (3 1.96+20080831-1) grub-linuxbios (3 1.96+20080831-1) grub-pc (3 1.96+20080831-1) 
Provides: 
1.97~beta4-1ubuntu4.1 - 
1.97~beta4-1ubuntu3 - 
Reverse Provides: 
[B]Package: grub-pc
Versions: 
1.97~beta4-1ubuntu4.1[/B] (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-i386_Packages) (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-security_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-i386_Packages
                  MD5: 93c713e08b0e7bb2b28e858ded96503b

1.97~beta4-1ubuntu3 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
                  MD5: 93c713e08b0e7bb2b28e858ded96503b


Reverse Depends: 
  linux-crashdump,grub-pc 1.96+20090611-1ubuntu2
  linux-crashdump,grub-pc 1.96+20090611-1ubuntu2
  grub2,grub-pc
  grub-ieee1275,grub-pc
  grub-ieee1275,grub-pc
  grub-efi-ia32,grub-pc
  grub-efi-ia32,grub-pc
  grub-efi-amd64,grub-pc
  grub-coreboot,grub-pc
  grub-coreboot,grub-pc
  ubiquity,grub-pc
  linux-image-2.6.31-17-virtual,grub-pc
  linux-image-2.6.31-17-generic-pae,grub-pc
  linux-image-2.6.31-17-generic,grub-pc
  linux-image-2.6.31-17-386,grub-pc
  linux-image-2.6.31-16-virtual,grub-pc
  linux-image-2.6.31-16-generic-pae,grub-pc
  linux-image-2.6.31-16-generic,grub-pc
  linux-image-2.6.31-16-386,grub-pc
  linux-image-2.6.31-15-virtual,grub-pc
  linux-image-2.6.31-15-generic-pae,grub-pc
  linux-image-2.6.31-15-generic,grub-pc
  linux-image-2.6.31-15-386,grub-pc
  grub-common,grub-pc 1.96+20080831-1
  startupmanager,grub-pc
  selinux,grub-pc
  linux-image-2.6.31-9-rt,grub-pc
  linux-crashdump,grub-pc 1.96+20090611-1ubuntu2
  grub2-splashimages,grub-pc
  grub2,grub-pc
  grub-ieee1275,grub-pc
  grub-ieee1275,grub-pc
  grub-efi-ia32,grub-pc
  grub-efi-ia32,grub-pc
  grub-efi-amd64,grub-pc
  grub-coreboot,grub-pc
  grub-coreboot,grub-pc
  mythbuntu-live,grub-pc
  ubiquity,grub-pc
  linux-image-2.6.31-14-virtual,grub-pc
  linux-image-2.6.31-14-generic-pae,grub-pc
  linux-image-2.6.31-14-generic,grub-pc
  linux-image-2.6.31-14-386,grub-pc
  grub-common,grub-pc 1.96+20080831-1
  grub,grub-pc
Dependencies: 
1.97~beta4-1ubuntu4.1 - libc6 (2 2.8) debconf (18 0.5) debconf-2.0 (0 (null)) grub-common (5 1.97~beta4-1ubuntu4.1) ucf (0 (null)) desktop-base (2 4.0.6) genisoimage (0 (null)) desktop-base (5 4.0.5) grub (3 0.97-54) grub-coreboot (0 (null)) grub-efi-amd64 (0 (null)) grub-efi-ia32 (0 (null)) grub-ieee1275 (0 (null)) grub-legacy (0 (null)) grub (0 (null)) grub-common (5 1.97~beta4-1ubuntu4.1) grub-common (3 1.97~beta1-1ubuntu4) grub-coreboot (0 (null)) grub-efi-amd64 (0 (null)) grub-efi-ia32 (0 (null)) grub-ieee1275 (0 (null)) grub-legacy (0 (null)) grub2 (3 1.97~beta4-1ubuntu4.1) 
1.97~beta4-1ubuntu3 - libc6 (2 2.8) debconf (18 0.5) debconf-2.0 (0 (null)) grub-common (5 1.97~beta4-1ubuntu3) ucf (0 (null)) desktop-base (2 4.0.6) genisoimage (0 (null)) desktop-base (5 4.0.5) grub (3 0.97-54) grub-coreboot (0 (null)) grub-efi-amd64 (0 (null)) grub-efi-ia32 (0 (null)) grub-ieee1275 (0 (null)) grub-legacy (0 (null)) grub (0 (null)) grub-common (5 1.97~beta4-1ubuntu3) grub-common (3 1.97~beta1-1ubuntu4) grub-coreboot (0 (null)) grub-efi-amd64 (0 (null)) grub-efi-ia32 (0 (null)) grub-ieee1275 (0 (null)) grub-legacy (0 (null)) grub2 (3 1.97~beta4-1ubuntu3) 
Provides: 
1.97~beta4-1ubuntu4.1 - 
1.97~beta4-1ubuntu3 - 
Reverse Provides: 


**If those packages are not available for reinstallation then the rest of the procedure will fail and you won't be able to boot!** So if in doubt I should see the output of:

```
cat /etc/apt/sources.list
```

OTOH if the package info looks right we should be able to backup the old /boot/grub directory, create a new one, and change from legacy grub to grub2 with just a few commands (**please copy-n-paste commands**):

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo grub-install /dev/sda
```

```
sudo update-grub
```

If all goes well that should be it!

---

### Post by sparky2 on 2010-01-09
there's another problem interfering... when I tried to change to Main Server it told me my info was out-of-date and gave me a reload button that I clicked (screenshot-20)

it reported an error - mainly unable to resolve 'archive.ubuntu.com' (screenshot-21)

I tried 'sudo apt-get update' again anyway, but got similar errors (screenshot-22)

I'm thinking it may be simpler to reload karmic from my Live CD? provided we can edit the grub menu's later to add in the Windows XP partition. I haven't invested much in Karmic on this machine, but I have in the XP partition ...!

What do you think?

---

### Post by sparky2 on 2010-01-09
hold the boat ! .... I tried 'sudo apt-get update' again and it worked !! so I worked through all your suggested commands and they all worked too ... XP and Linux are both in the boot menu and boot fine. 

Fantastic ! :D

Not sure what happened previous time, but I am now linked to "Main Server" in s/w sources so perhaps it was the Australian Server again ??

many thanks ***kansasnoob***

---

### Post by kansasnoob on 2010-01-10
> **sparky2 said:**
> hold the boat ! .... I tried 'sudo apt-get update' again and it worked !! so I worked through all your suggested commands and they all worked too ... XP and Linux are both in the boot menu and boot fine. 

Fantastic ! :D

Not sure what happened previous time, but I am now linked to "Main Server" in s/w sources so perhaps it was the Australian Server again ??

many thanks ***kansasnoob***

Glad it worked!

I don't know what the deal is with the Australian server. I just know it's created problems for me a few times the past few days.

---

