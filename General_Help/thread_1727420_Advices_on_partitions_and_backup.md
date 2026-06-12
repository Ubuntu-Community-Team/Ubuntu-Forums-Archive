---
title: "Advices on partitions and backup"
date: 2011-04-12
forum: General Help
---

### Post by hearea on 2011-04-12
Being a curious newbie, i've been reinstalling the os a dozen of times even since i started using Linux. Luckily i keep a seperate /home and also backup 'achieves' from /var/cache/apt to reinstall from synaptic manager, so it doesn't take as much time to setup the system as it used to. But, it still takes a lot of time.

So can you give me some tips about partitioning n backuping? 

Should i create more partitions for /usr, /var n such? Which partitions need to be formatted when install a new system? ( cuz i tried reinstalling without formatting the hard drive once, but it doesn't help : i.e. sudoers or grub still have problem etc. n to a newbie like me, fixing those takes more time than reinstalling the os  )

Asides from /var/cache/apt/achieves, are there any other folders i should backup? cuz it looks like it's not enough. When i add downloaded packages from synaptic, it still needs to download a lot of other packages, and after that, i still have to download some programs from Software Manager, then run update again. ( but with less things need to be updated though )

---

### Post by seawolf167 on 2011-04-12
The bare minimum for partitioning is / (root) and swap mounted as / and swap respectively. You can always add more as you figured out to make your life easier like /home or /boot, etc. but unless you are in a server environment, you probably don't care to have more than /, /home and swap.

As for backups, I generally image my drive with [Clonezilla ]("http://www.clonezilla.org")every couple months, and keep an up-to-date backup of my precious files/folders with an [rsync]("https://help.ubuntu.com/community/BackupYourSystem") crontab entry.

For formatting, you don't need to format anything before installing, i.e. if you select to "manually partition" you can create your partition table, sizes, formats, type, etc. during the installation. The only thing you may need to do if you don't format everything at install time is add an entry in /etc/fstab so it automounts at boot.

---

